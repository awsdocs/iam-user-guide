# Troubleshooting Amazon EC2 and IAM<a name="troubleshoot_iam-ec2"></a>

Use the information here to help you troubleshoot and fix access denied or other issues that you might encounter when working with Amazon EC2 and IAM\.

**Topics**
+ [When Attempting to Launch an Instance, I Don't See the Role I Expected to See in the Amazon EC2 Console **IAM Role** List](#troubleshoot_iam-ec2_missingrole)
+ [The Credentials on My Instance Are for the Wrong Role](#troubleshoot_iam-ec2_wrongrole)
+ [When I Attempt to Call the `AddRoleToInstanceProfile`, I Get an `AccessDenied` Error](#troubleshoot_iam-ec2_access-denied-adding-role)
+ [Amazon EC2: When I Attempt to Launch an Instance with a Role, I Get an `AccessDenied` Error](#troubleshoot_iam-ec2_access-denied-launch)
+ [I Can't Access the Temporary Security Credentials on My EC2 Instance](#troubleshoot_iam-ec2_no-keys)
+ [What Do the Errors from the `info` Document in the IAM Subtree Mean?](#troubleshoot_iam-ec2_errors-info-doc)

## When Attempting to Launch an Instance, I Don't See the Role I Expected to See in the Amazon EC2 Console **IAM Role** List<a name="troubleshoot_iam-ec2_missingrole"></a>

Check the following:
+ If you are signed in as an IAM user, verify that you have permission to call `ListInstanceProfiles`\. For information about the permissions necessary to work with roles, see "Permissions Required for Using Roles with Amazon EC2" in [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)\. For information about adding permissions to a user, see [Managing IAM Policies](access_policies_manage.md)\.

  If you cannot modify your own permissions, you must contact an administrator who can work with IAM in order to update your permissions\.
+ If you created a role by using the IAM CLI or API, verify that you created an instance profile and added the role to that instance profile\. Also, if you name your role and instance profile differently, you won't see the correct role name in the list of IAM roles in the Amazon EC2 console\. The **IAM Role** list in the Amazon EC2 console lists the names of instance profiles, not the names of roles\. You will have to select the name of the instance profile that contains the role you want\. For details about instance profiles, see [Using Instance Profiles](id_roles_use_switch-role-ec2_instance-profiles.md)\.
**Note**  
If you use the IAM console to create roles, you don't need to work with instance profiles\. For each role that you create in the IAM console, an instance profile is created with the same name as the role, and the role is automatically added to that instance profile\. An instance profile can contain only one IAM role, and that limit cannot be increased\.

## The Credentials on My Instance Are for the Wrong Role<a name="troubleshoot_iam-ec2_wrongrole"></a>

The role in the instance profile might have been replaced recently\. If so, your application will need to wait for the next automatically scheduled credential rotation before credentials for your role become available\.

## When I Attempt to Call the `AddRoleToInstanceProfile`, I Get an `AccessDenied` Error<a name="troubleshoot_iam-ec2_access-denied-adding-role"></a>

If you are making requests as an IAM user, verify that you have the following permissions:
+ `iam:AddRoleToInstanceProfile` with the resource matching the instance profile ARN \(for example, `arn:aws:iam::999999999999:instance-profile/ExampleInstanceProfile`\)\. 

For more information about the permissions necessary to work with roles, see "How Do I Get Started?" in [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)\. For information about adding permissions to a user, see [Managing IAM Policies](access_policies_manage.md)\.

## Amazon EC2: When I Attempt to Launch an Instance with a Role, I Get an `AccessDenied` Error<a name="troubleshoot_iam-ec2_access-denied-launch"></a>

Check the following:
+ Launch an instance without an instance profile\. This will help ensure that the problem is limited to IAM roles for Amazon EC2 instances\.
+ If you are making requests as an IAM user, verify that you have the following permissions:
  + `ec2:RunInstances` with a wildcard resource \("\*"\)
  + `iam:PassRole` with the resource matching the role ARN \(for example, `arn:aws:iam::999999999999:role/ExampleRoleName`\)
+ Call the IAM `GetInstanceProfile` action to ensure that you are using a valid instance profile name or a valid instance profile ARN\. For more information, see [ Using IAM roles with Amazon EC2 instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html#UsingIAMrolesWithAmazonEC2Instances)\.
+ Call the IAM `GetInstanceProfile` action to ensure that the instance profile has a role\. Empty instance profiles will fail with an `AccessDenied` error\. For more information about creating a role, see [Creating IAM Roles](id_roles_create.md)\.

For more information about the permissions necessary to work with roles, see "How Do I Get Started?" in [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)\. For information about adding permissions to a user, see [Managing IAM Policies](access_policies_manage.md)\. 

## I Can't Access the Temporary Security Credentials on My EC2 Instance<a name="troubleshoot_iam-ec2_no-keys"></a>

To access temporary security credentials on your EC2 instance, you must first use the IAM console to create a role\. Then you launch an EC2 instance that uses that role and examine the running instance\. For more information, see **How Do I Get Started?** in [Using an IAM Role to Grant Permissions to Applications Running on Amazon EC2 Instances](id_roles_use_switch-role-ec2.md)\.

If you still can't access your temporary security credentials on your EC2 instance, check the following:
+ Can you access another part of the instance metadata service \(IMDS\)? If not, check that you have no firewall rules blocking access to requests to the IMDS\.

  ```
  [ec2-user@domU-12-31-39-0A-8D-DE ~]$ GET http://169.254.169.254/latest/meta-data/hostname; echo
  ```
+ Does the `iam` subtree of the IMDS exist? If not, verify that your instance has an IAM instance profile associated with it by calling the EC2 `DescribeInstances` API operation or using the aws ec2 `describe-instances` CLI command\. 

  ```
  [ec2-user@domU-12-31-39-0A-8D-DE ~]$ GET http://169.254.169.254/latest/meta-data/iam; echo
  ```
+ Check the `info` document in the IAM subtree for an error\. If you have an error, see [What Do the Errors from the `info` Document in the IAM Subtree Mean?](#troubleshoot_iam-ec2_errors-info-doc) for more information\.

  ```
  [ec2-user@domU-12-31-39-0A-8D-DE ~]$ GET http://169.254.169.254/latest/meta-data/iam/info; echo
  ```

## What Do the Errors from the `info` Document in the IAM Subtree Mean?<a name="troubleshoot_iam-ec2_errors-info-doc"></a>

### The `iam/info` Document Iindicates `"Code":"InstanceProfileNotFound"`<a name="troubleshoot_iam-ec2_errors-info-doc-profile-not-found"></a>

Your IAM instance profile has been deleted and Amazon EC2 can no longer provide credentials to your instance\. You must attach a valid instance profile to your Amazon EC2 instance\.

If an instance profile with that name exists, check that the instance profile wasn't deleted and another was created with the same name:

1. Call the IAM `GetInstanceProfile` operation to get the `InstanceProfileId`\.

1. Call the Amazon EC2 `DescribeInstances` operation to get the `IamInstanceProfileId` for the instance\.

1. Verify that the `InstanceProfileId` from the IAM operation matches the `IamInstanceProfileId` from the Amazon EC2 operation\.

If the IDs are different, then the instance profile attached to your instances is no longer valid\. You must attach a valid instance profile to the instance\. 

### The `iam/info` Document Indicates a Success but Indicates `"Message":"Instance Profile does not contain a role..."`<a name="troubleshoot_iam-ec2_errors-info-doc-no-role"></a>

The role has been removed from the instance profile by the IAM `RemoveRoleFromInstanceProfile` action\. You can use the IAM `AddRoleToInstanceProfile` action to attach a role to the instance profile\. Your application will need to wait until the next scheduled refresh to access the credentials for the role\. 

### The `iam/security-credentials/[role-name]` Document Indicates `"Code":"AssumeRoleUnauthorizedAccess"`<a name="troubleshoot_iam-ec2_errors-info-doc-unauthorized-access"></a>

Amazon EC2 does not have permission to assume the role\. Permission to assume the role is controlled by the trust policy attached to the role, like the example that follows\. Use the IAM `UpdateAssumeRolePolicy` API to update the trust policy\. 

```
{"Version": "2012-10-17","Statement": [{"Effect": "Allow","Principal": {"Service": ["ec2.amazonaws.com"]},"Action": ["sts:AssumeRole"]}]}
```

Your application will need to wait until the next automatically scheduled refresh to access the credentials for the role\.