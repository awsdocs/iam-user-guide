# Creating Your First IAM Admin User and Group<a name="getting-started_create-admin-group"></a>

**Important**  
If you arrived at this page trying to enable Amazon Advertising for your application or web site, see [Becoming a Product Advertising API Developer](http://docs.aws.amazon.com/AWSECommerceService/latest/DG/becomingDev.html)\.

As a [best practice](best-practices.md#lock-away-credentials), do not use the AWS account root user for any task where it's not required\. Instead, create a new IAM user for each person that requires administrator access\. Then make those users administrators by placing the users into an "Administrators" group to which you attach the AdministratorAccess managed policy\. 

Thereafter, the users in the administrators group should set up the groups, users, and so on, for the AWS account\. All future interaction should be through the AWS account's users and their own keys instead of the root user\. However, to perform some account and service management tasks, you must log in using the root user credentials\. To view the tasks that require you to sign in as the root user, see [AWS Tasks that Require Account Root User](http://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\.

## Creating an Administrator IAM User and Group \(Console\)<a name="getting-started_create-admin-group-console"></a>

This procedure describes how to use the AWS Management Console to create an IAM user for yourself and add that user to a group that has administrative permissions from an attached managed policy\.

**To create an administrator user for yourself and add the user to an administrators group \(console\)**

1. Use your AWS account email address and password to sign in as the *[AWS account root user](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)* to the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users** and then choose **Add user**\.

1. For **User name**, type a user name, such as **Administrator**\. The name can consist of letters, digits, and the following characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), underscore \(\_\), and hyphen \(\-\)\. The name is not case sensitive and can be a maximum of 64 characters in length\.

1. Select the check box next to **AWS Management Console access**, select **Custom password**, and then type your new password in the text box\. If you're creating the user for someone other than yourself, you can optionally select **Require password reset** to force the user to create a new password when first signing in\.

1. Choose **Next: Permissions**\.

1. On the **Set permissions for user** page, choose **Add user to group**\.

1. Choose **Create group**\.

1. In the **Create group** dialog box, type the name for the new group\. The name can consist of letters, digits, and the following characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), underscore \(\_\), and hyphen \(\-\)\. The name is not case sensitive and can be a maximum of 128 characters in length\.

1. In the policy list, select the check box next to **AdministratorAccess**\. Then choose **Create group**\.

1. Back in the list of groups, select the check box for your new group\. Choose **Refresh** if necessary to see the group in the list\.

1. Choose **Next: Review** to see the list of group memberships to be added to the new user\. When you are ready to proceed, choose **Create user**\.

You can use this same process to create more groups and users and to give your users access to your AWS account resources\. To learn about using policies that restrict user permissions to specific AWS resources, see [Access Management](access.md) and [Example Policies](access_policies_examples.md)\. To add additional users to the group after it's created, see [Adding and Removing Users in an IAM Group](id_groups_manage_add-remove-users.md)\.

## Creating an IAM User and Group \(AWS CLI\)<a name="getting-started_create-admin-group-cli"></a>

If you followed the steps in the previous section, you used the AWS Management Console to set up an administrators group while creating the IAM user in your AWS account\. This procedure shows an alternative way to create a group\.

**Overview: Setting Up an Administrators Group**

1. Create a group and give it a name \(for example, Admins\)\. For more information, see [Creating a Group \(AWS CLI\)](#Using_CreateGroup)\. 

1. Attach a policy that gives the group administrative permissions—access to all AWS actions and resources\. For more information, see [Attaching a Policy to the Group \(AWS CLI\)](#Using_AddingAdminRightsPolicy)\. 

1. Add at least one user to the group\. For more information, see [Creating an IAM User in Your AWS Account](id_users_create.md)\. 

### Creating a Group \(AWS CLI\)<a name="Using_CreateGroup"></a>

This section shows how to create a group in the IAM system\. 

**To create an administrators group \(AWS CLI\)**

1. Type the [http://docs.aws.amazon.com/cli/latest/reference/iam/create-group.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-group.html) command with the name you've chosen for the group\. Optionally, you can include a path as part of the group name\. For more information about paths, see [Friendly Names and Paths](reference_identifiers.md#identifiers-friendly-names)\. The name can consist of letters, digits, and the following characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), underscore \(\_\), and hyphen \(\-\)\. The name is not case sensitive and can be a maximum of 128 characters in length\.

   In this example, you create a group named Admins\. 

   ```
   aws iam create-group --group-name Admins
   {
       "Group": {
           "Path": "/", 
           "CreateDate": "2014-06-05T20:29:53.622Z", 
           "GroupId":"ABCDEFGHABCDEFGHABCDE",
           "Arn": "arn:aws:iam::123456789012:group/Admins", 
           "GroupName": "Admins"
       }
   }
   ```

1. Type the [http://docs.aws.amazon.com/cli/latest/reference/iam/list-groups.html](http://docs.aws.amazon.com/cli/latest/reference/iam/list-groups.html) command to list the groups in your AWS account and confirm the group was created\.

   ```
   aws iam list-groups
   {
       "Groups": [
           {
               "Path": "/", 
               "CreateDate": "2014-06-05T20:29:53.622Z", 
               "GroupId":"ABCDEFGHABCDEFGHABCDE", 
               "Arn": "arn:aws:iam::123456789012:group/Admins", 
               "GroupName": "Admins"
           }
       ]
   }
   ```

   The response includes the Amazon Resource Name \(ARN\) for your new group\. The ARN is a standard format that AWS uses to identify resources\. The 12\-digit number in the ARN is your AWS account ID\. The friendly name you assigned to the group \(Admins\) appears at the end of the group's ARN\.

### Attaching a Policy to the Group \(AWS CLI\)<a name="Using_AddingAdminRightsPolicy"></a>

This section shows how to attach a policy that lets any user in the group perform any action on any resource in the AWS account\. You do this by attaching the [AWS managed policy](access_policies_managed-vs-inline.md) called AdministratorAccess to the Admins group\. For more information about policies, see [Access Management](access.md)\. 

**To add a policy giving full administrator permissions \(AWS CLI\)**

1. Type the [http://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html) command to attach the policy called AdministratorAccess to your Admins group\. The command uses the ARN of the AWS managed policy called AdministratorAccess\. 

   ```
   aws iam attach-group-policy --group-name Admins --policy-arn arn:aws:iam::aws:policy/AdministratorAccess
   ```

   If the command is successful, there is no response\.

1. Type the [http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html](http://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html) command to confirm the policy is attached to the Admins group\.

   ```
   aws iam list-attached-group-policies --group-name Admins
   ```

   The response lists the names of the policies attached to the Admins group\. A response like the following tells you that the policy named AdministratorAccess has been attached to the Admins group:

   ```
   {
       "AttachedPolicies": [
           {
               "PolicyName": "AdministratorAccess",
               "PolicyArn": "arn:aws:iam::aws:policy/AdministratorAccess"
           }
       ],
       "IsTruncated": false
   }
   ```

You can confirm the contents of a particular policy with the [http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html](http://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html) command\. 

**Important**  
After you have the administrators group set up, you must add at least one user to it\. For more information about adding users to a group, see [Creating an IAM User in Your AWS Account](id_users_create.md)\. 

## Related Resources<a name="getting-started_create-admin-group-addl-resources"></a>

For related information found in the *Amazon Web Services General Reference*, see the following resources:
+ [AWS Tasks that Require Account Root User](http://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)

For related information in the *IAM User Guide*, see the following resources:
+ [Reducing Policy Scope by Viewing User Activity](access_policies_access-advisor.md)
+ [Tutorial: Delegate Access to the Billing Console](tutorial_billing.md)