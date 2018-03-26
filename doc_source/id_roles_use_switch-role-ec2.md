# Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances<a name="id_roles_use_switch-role-ec2"></a>

Applications that run on an EC2 instance must include AWS credentials in their AWS API requests\. You could have your developers store AWS credentials directly within the EC2 instance and allow applications in that instance to use those credentials\. But developers would then have to manage the credentials and ensure that they securely pass the credentials to each instance and update each EC2 instance when it's time to rotate the credentials\. That's a lot of additional work\.

Instead, you can and should use an IAM role to manage *temporary* credentials for applications that run on an EC2 instance\. When you use a role, you don't have to distribute long\-term credentials \(such as a user name and password or access keys\) to an EC2 instance\. Instead, the role supplies temporary permissions that applications can use when they make calls to other AWS resources\. When you launch an EC2 instance, you specify an IAM role to associate with the instance\. Applications that run on the instance can then use the role\-supplied temporary credentials to sign API requests\.

Using roles to grant permissions to applications that run on EC2 instances requires a bit of extra configuration\. An application running on an EC2 instance is abstracted from AWS by the virtualized operating system\. Because of this extra separation, an additional step is needed to assign an AWS role and its associated permissions to an EC2 instance and make them available to its applications\. This extra step is the creation of an *[instance profile](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html)* that is attached to the instance\. The instance profile contains the role and can provide the role's temporary credentials to an application that runs on the instance\. Those temporary credentials can then be used in the application's API calls to access resources and to limit access to only those resources that the role specifies\. Note that only one role can be assigned to an EC2 instance at a time, and all applications on the instance share the same role and permissions\.

Using roles in this way has several benefits\. Because role credentials are temporary and rotated automatically, you don't have to manage credentials, and you don't have to worry about long\-term security risks\. In addition, if you use a single role for multiple instances, you can make a change to that one role and the change is propagated automatically to all the instances\. 

**Note**  
Although a role is usually assigned to an EC2 instance when you launch it, a role can also be attached to an EC2 instance that is already running\. To learn how to attach a role to a running instance, see [IAM Roles for Amazon EC2](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html#attach-iam-role)\.

## How Do Roles for EC2 Instances Work?<a name="roles-usingrole-ec2instance-roles"></a>

In the following figure, a developer runs an application on an EC2 instance that requires access to the S3 bucket named `photos`\. An administrator creates the `Get-pics` role\. The role includes policies that grant read permissions for the bucket and that allow the developer to launch the role with an EC2 instance\. When the application runs on the instance, it can use the role's temporary credentials to access the photos bucket\. The administrator doesn't have to grant the developer permission to access the photos bucket, and the developer never has to share or manage credentials\.

![\[Application on an EC2 instance accessing an AWS resource\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/roles-usingrole-ec2roleinstance.png)

1. The administrator uses IAM to create the **Get\-pics** role\. In the role's trust policy, the administrator specifies that only EC2 instances can assume the role\. In the role's permission policy, the administrator specifies read\-only permissions for the `photos` bucket\.

1. A developer launches an EC2 instance and assigns the `Get-pics` role to that instance\.
**Note**  
If you use the IAM console, the instance profile is managed for you and is mostly transparent to you\. However, if you use the AWS CLI or API to create and manage the role and EC2 instance, then you must create the instance profile and assign the role to it as separate steps\. Then, when you launch the instance, you must specify the instance profile name instead of the role name\.

1. When the application runs, it obtains temporary security credentials from Amazon EC2 [instance metadata](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AESDG-chapter-instancedata.html), as described in [Retrieving Security Credentials from Instance Metadata](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html#instance-metadata-security-credentials)\. These are [temporary security credentials](id_credentials_temp.md) that represent the role and are valid for a limited period of time\. 

   With some [AWS SDKs](http://aws.amazon.com/tools/), the developer can use a provider that manages the temporary security credentials transparently\. \(The documentation for individual AWS SDKs describes the features supported by that SDK for managing credentials\.\)

   Alternatively, the application can get the temporary credentials directly from the instance metadata of the EC2 instance\. Credentials and related values are available from the `iam/security-credentials/role-name` category \(in this case, `iam/security-credentials/Get-pics`\) of the metadata\. If the application gets the credentials from the instance metadata, it can cache the credentials\.

1. Using the retrieved temporary credentials, the application accesses the photo bucket\. Because of the policy attached to the **Get\-pics** role, the application has read\-only permissions\. 

   The temporary security credentials that are available on the instance are automatically rotated before they expire so that a valid set is always available\. The application just needs to make sure that it gets a new set of credentials from the instance metadata before the current ones expire\. If the AWS SDK manages credentials, the application doesn't need to include additional logic to refresh the credentials\. However, if the application gets temporary security credentials from the instance metadata and has cached them, it should get a refreshed set of credentials every hour, or at least 15 minutes before the current set expires\. The expiration time is included in the information that is returned in the `iam/security-credentials/role-name` category\. 

## Permissions Required for Using Roles with Amazon EC2<a name="roles-usingrole-ec2instance-permissions"></a>

To launch an instance with a role, the developer must have permission to launch EC2 instances and permission to pass IAM roles\.

The following sample policy allows users to use the AWS Management Console to launch an instance with a role\. The policy includes wildcards \(`*`\) to allow a user to pass any role and to perform all Amazon EC2 actions\. The `ListInstanceProfiles` action allows users to view all of the roles that are available in the AWS account\.

**Example policy that grants a user permission to use the Amazon EC2 console to launch an instance with any role**  

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": [
      "iam:PassRole",
      "iam:ListInstanceProfiles",
      "ec2:*"
    ],
    "Resource": "*"
  }]
}
```

### Restricting Which Roles Can Be Passed to EC2 Instances \(Using PassRole\)<a name="roles-usingrole-ec2instance-passrole"></a>

You can use the `PassRole` permission to restrict which role a user can pass to an EC2 instance when the user launches the instance\. This helps prevent the user from running applications that have more permissions than the user has been granted—that is, from being able to obtain elevated privileges\. For example, imagine that user Alice has permissions only to launch EC2 instances and to work with Amazon S3 buckets, but the role she passes to an EC2 instance has permissions to work with IAM and Amazon DynamoDB\. In that case, Alice might be able to launch the instance, log into it, get temporary security credentials, and then perform IAM or DynamoDB actions that she's not authorized for\.

To restrict which roles a user can pass to an EC2 instance, you create a policy that allows the `PassRole` action\. You then attach the policy to the user \(or to an IAM group that the user belongs to\) who will launch EC2 instances\. In the `Resource` element of the policy, you list the role or roles that the user is allowed to pass to EC2 instances\. When the user launches an instance and associates a role with it, Amazon EC2 checks whether the user is allowed to pass that role\. Of course, you should also ensure that the role that the user can pass does not include more permissions than the user is supposed to have\.

**Note**  
`PassRole` is not an API action in the same way that `RunInstances` or `ListInstanceProfiles` is\. Instead, it's a permission that AWS checks whenever a role ARN is passed as a parameter to an API \(or the console does this on the user's behalf\)\. It helps an administrator to control which roles can be passed by which users\. In this case, it ensures that the user is allowed to attach a specific role to an Amazon EC2 instance\.

**Example policy that grants a user permission to launch an EC2 instance with a specific role**  
The following sample policy allows users to use the Amazon EC2 API to launch an instance with a role\. The `Resource` element specifies the Amazon Resource Name \(ARN\) of a role\. By specifying the ARN, the policy grants the user the permission to pass only the `Get-pics` role\. If the user tries to specify a different role when launching an instance, the action fails\.  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "ec2:RunInstances",
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": "iam:PassRole",
      "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:role/Get-pics"
    }
  ]
}
```

## How Do I Get Started?<a name="roles-usingrole-ec2instance-get-started"></a>

To understand how roles work with EC2 instances, you need to use the IAM console to create a role, launch an EC2 instance that uses that role, and then examine the running instance\. You can examine the [instance metadata](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AESDG-chapter-instancedata.html) to see how the role's temporary credentials are made available to an instance\. You can also see how an application that runs on an instance can use the role\. Use the following resources to learn more\. 
+ SDK walkthroughs\. The AWS SDK documentation includes walkthroughs that show an application running on an EC2 instance that uses temporary credentials for roles to read an Amazon S3 bucket\. Each of the following walkthroughs presents similar steps with a different programming language:
  + [ Using IAM Roles for EC2 Instances with the SDK for Java](http://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/java-dg-roles.html) in the *AWS SDK for Java Developer Guide* 
  + [ Using IAM Roles for EC2 Instances with the SDK for \.NET](http://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/net-dg-roles.html) in the *AWS SDK for \.NET Developer Guide*
  + [ Using IAM Roles for EC2 Instances with the SDK for Ruby](http://docs.aws.amazon.com/sdk-for-ruby/v2/developer-guide/ruby-dg-roles.html) in the *AWS SDK for Ruby Developer Guide*

    The walkthroughs provide complete step\-by\-step instructions for creating and compiling the example program, creating the role, launching the instance, connecting to the instance, deploying the example program, and testing it\.

## Related Information<a name="roles-usingrole-ec2instance-related-info"></a>

For more information about creating roles or roles for EC2 instances, see the following information:
+ For more information about [using IAM roles with Amazon EC2 instances](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html#UsingIAMrolesWithAmazonEC2Instances), go to the *Amazon EC2 User Guide for Linux Instances*\.
+ To create a role, see [Creating IAM Roles](id_roles_create.md)
+ For more information about using temporary security credentials, see [Temporary Security Credentials](id_credentials_temp.md)\.
+ If you work with the IAM API or CLI, you must create and manage IAM instance profiles\. For more information about instance profiles, see [Using Instance Profiles](id_roles_use_switch-role-ec2_instance-profiles.md)\.
+ For more information about temporary security credentials for roles in the instance metadata, see [Retrieving Security Credentials from Instance Metadata](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html#instance-metadata-security-credentials) in the Amazon EC2 User Guide for Linux Instances\.