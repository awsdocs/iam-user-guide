# Creating a Role to Delegate Permissions to an AWS Service<a name="id_roles_create_for-service"></a>

Many AWS services require that you use roles to allow the service to access resources in other services on your behalf\. A role that a service assumes to perform actions on your behalf is called a [service role](id_roles_terms-and-concepts.md#iam-term-service-role)\. When a role serves a specialized purpose for a service, it is categorized as a [service role for EC2 instances](id_roles_terms-and-concepts.md#iam-term-service-role-ec2) \(for example\), or a [service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)\. To see what services support using service\-linked roles, or whether a service supports any form of temporary credentials, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md)\. To learn how an individual service uses roles, choose the service name in the table to view the documentation for that service\.

For information about how roles help you to delegate permissions, see [Roles Terms and Concepts](id_roles_terms-and-concepts.md)\.

## Creating a Role for an AWS Service \(Console\)<a name="roles-creatingrole-service-console"></a>

You can use the AWS Management Console to create a role for a service\. Because some services support more than one service role, see the [AWS documentation](http://docs.aws.amazon.com/) for your service to see which use case to choose\. You can learn how to assign the necessary trust and permissions policies to the role so that the service can assume the role on your behalf\. The steps that you can use to control the permissions for your role can vary, depending on how the service defines the use cases, and whether or not you create a service\-linked role\.

**To create a role for an AWS service \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. For **Select type of trusted entity**, choose **AWS service**\. 

1. Choose the service that you want to allow to assume this role\.

1. Choose the use case for your service\. If the specified service has only one use case, it is selected for you\. Use cases are defined by the service to include the trust policy that the service requires\. Then choose **Next: Permissions**\.

1. Choose one or more permissions policies to attach to the role\. Depending on the use case that you selected, the service might do any of the following:
   + Define the permissions that the role uses
   + Allow you to choose from a limited set of permissions
   + Allow you to choose from any permissions
   + Allow you to select no policies at this time, create the policies later, and then attach them to the role

   If possible, select the policy to use for the permissions policy or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see step 4 in the procedure [Creating IAM Policies \(Console\)](access_policies_create.md#access_policies_create-start)\. After you create the policy, close that tab and return to your original tab\. Select the check box next to the permissions policies that you want the service to have\.

1. If possible, select the check box next to the policy that assigns the permissions that you want the users to have\. 

1. \(Optional\) Set a [permissions boundary](access_policies_boundaries.md)\. This is an advanced feature that is available for service roles, but not service\-linked roles\. 

   If possible, open the **Set permissions boundary** section and choose **Use a permissions boundary to control the maximum role permissions**\. IAM includes a list of the AWS managed and customer managed policies in your account\. Select the policy to use for the permissions boundary or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see step 4 in the procedure [Creating IAM Policies \(Console\)](access_policies_create.md#access_policies_create-start)\. After you create the policy, close that tab and return to your original tab to select the policy to use for the permissions boundary\.

1. Choose **Next: Review**\.

1. For **Role name**, the degree of role name customization is defined by the service\. If the service defines the role's name, this option is not editable\. In other cases, the service might define a prefix for the role and allow you to type an optional suffix\. Some services allow you to specify the entire name of your role\.

   If possible, type a role name or role name suffix\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because other AWS resources might reference the role, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Role description**, type a description for the new role\.

1. Review the role and then choose **Create role**\.

## Creating a Role for a Service \(AWS CLI\)<a name="roles-creatingrole-service-cli"></a>

Creating a role from the AWS CLI involves multiple steps\. When you use the console to create a role, many of the steps are done for you, but with the AWS CLI you must explicitly perform each step yourself\. You must create the role and then assign a permission policy to the role\. If the service you are working with is Amazon EC2, then you must also create an instance profile and add the role to it\. Optionally, you can also set the [permissions boundary](access_policies_boundaries.md) for your role\.

**To create a role for an AWS service from the AWS CLI**

1. Create a role: [aws iam create\-role](http://docs.aws.amazon.com/cli/latest/reference/iam/create-role.html)

1. Attach a managed permissions policy to the role: [aws iam attach\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-role-policy.html)

    or

   Create an inline permissions policy for the role: [aws iam put\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)

1. \(Optional\) Set the [permissions boundary](access_policies_boundaries.md) for the role: [aws iam put\-role\-permissions\-boundary](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-permissions-boundary.html)

   A permissions boundary controls the maximum permissions that a role can have\. Permissions boundaries are an advanced AWS feature\.

If you are going to use the role with Amazon EC2 or another AWS service that uses Amazon EC2, you must store the role in an instance profile\. An instance profile is a container for a role that can be attached to an Amazon EC2 instance when launched\. An instance profile can contain only one role, and that limit cannot be increased\. If you create the role using the AWS Management Console, the instance profile is created for you with the same name as the role\. For more information about instance profiles, see [Using Instance Profiles](id_roles_use_switch-role-ec2_instance-profiles.md)\. For information about how to launch an EC2 instance with a role, see [Controlling Access to Amazon EC2 Resources](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html#UsingIAMrolesWithAmazonEC2Instances) in the *Amazon EC2 User Guide for Linux Instances*\.

**To create an instance profile and store the role in it \(AWS CLI\)**

1. Create an instance profile: [aws iam create\-instance\-profile](http://docs.aws.amazon.com/cli/latest/reference/iam/create-instance-profile.html)

1. Add the role to the instance profile: [aws iam add\-role\-to\-instance\-profile](http://docs.aws.amazon.com/cli/latest/reference/iam/add-role-to-instance-profile.html)

The following example demonstrates the first two steps for creating a role and attaching permissions\. It also shows the two steps for creating an instance profile and adding the role to the profile\. This example allows the Amazon EC2 service to assume the role and view the `example_bucket` Amazon S3 bucket\. The example also assumes that you are running on a client computer running Windows and have already configured your command line interface with your account credentials and region\. For more information, see [Configuring the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)\.

In this example, include the following trust policy in the first command when you create the role\. This trust policy allows the Amazon EC2 service to assume the role\. 

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {"Service": "ec2.amazonaws.com"},
    "Action": "sts:AssumeRole"
  }
}
```

When you use the second command, you must attach a permissions policy to the role\. The following example permissions policy allows the role to perform only the `ListBucket` action on the `example_bucket` Amazon S3 bucket\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "s3:ListBucket",
    "Resource": "arn:aws:s3:::example_bucket"
  }
}
```

To create create this `Test-Role-for-EC2` role, you must first save the previous trust policy with the name `trustpolicyforec2.json` and the previous permissions policy with the name `permissionspolicyforec2.json` to the `policies` directory in your local `C:` drive\. You can then use the following commands to create the role, attach the policy, create the instance profile, and add the role to the instance profile\.

```
# Create the role and attach the trust policy that allows EC2 to assume this role.
$ aws iam create-role --role-name Test-Role-for-EC2 --assume-role-policy-document file://C:\policies\trustpolicyforec2.json

# Embed the permissions policy (in this example an inline policy) to the role to specify what it is allowed to do.
$ aws iam put-role-policy --role-name Test-Role-for-EC2 --policy-name Permissions-Policy-For-Ec2 --policy-document file://permissionspolicyforec2.json

# Create the instance profile required by EC2 to contain the role
$ aws iam create-instance-profile --instance-profile-name EC2-ListBucket-S3

# Finally, add the role to the instance profile
$ aws iam add-role-to-instance-profile --instance-profile-name EC2-ListBucket-S3 --role-name Test-Role-for-EC2
```

When you launch the EC2 instance, specify the instance profile name in the **Configure Instance Details** page if you use the AWS console\. If you use the `aws ec2 run-instances` CLI command, specify the `--iam-instance-profile` parameter\.

## Creating a Role for a Service \(AWS API\)<a name="roles-creatingrole-service-api"></a>

### <a name="roles-creatingrole-servicerole-api"></a>

Creating a role from the AWS API involves multiple steps\. When you use the console to create a role, many of the steps are done for you, but with the API you must explicitly perform each step yourself\. You must create the role and then assign a permission policy to the role\. If the service you are working with is Amazon EC2, then you must also create an instance profile and add the role to it\. Optionally, you can also set the [permissions boundary](access_policies_boundaries.md) for your role\.

**To create a role for an AWS service \(AWS API\)**

1. Create a role: [CreateRole](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateRole.html)

   For the role's trust policy, you can specify a file location\.

1. Attach a managed permission policy to the role: [AttachRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html)

    or

   Create an inline permission policy for the role: [PutRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)

1. \(Optional\) Set the [permissions boundary](access_policies_boundaries.md) for the role: [PutRolePermissionsBoundary](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePermissionsBoundary.html)

   A permissions boundary controls the maximum permissions that a role can have\. Permissions boundaries are an advanced AWS feature\.

If you are going to use the role with Amazon EC2 or another AWS service that uses Amazon EC2, you must store the role in an instance profile\. An instance profile is a container for a role\. Each instance profile can contain only one role, and that limit cannot be increased\. If you create the role in the AWS Management Console, the instance profile is created for you with the same name as the role\. For more information about instance profiles, see [Using Instance Profiles](id_roles_use_switch-role-ec2_instance-profiles.md)\. For information about how to launch an Amazon EC2 instance with a role, see [Controlling Access to Amazon EC2 Resources](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html#UsingIAMrolesWithAmazonEC2Instances) in the *Amazon EC2 User Guide for Linux Instances*\. 

**To create an instance profile and store the role in it \(AWS API\)**

1. Create an instance profile: [CreateInstanceProfile](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateInstanceProfile.html)

1. Add the role to the instance profile: [AddRoleToInstanceProfile](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AddRoleToInstanceProfile.html)