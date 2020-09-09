# Creating your first IAM admin user and group<a name="getting-started_create-admin-group"></a>

**Important**  
If you arrived at this page trying to enable Amazon Advertising for your application or web site, see [Becoming a Product Advertising API Developer](https://docs.aws.amazon.com/AWSECommerceService/latest/DG/becomingDev.html)\.

As a [best practice](best-practices.md#lock-away-credentials), do not use the AWS account root user for any task where it's not required\. Instead, create a new IAM user for each person that requires administrator access\. Then make those users administrators by placing the users into an "Administrators" group to which you attach the AdministratorAccess managed policy\. 

Thereafter, the users in the administrators group should set up the groups, users, and so on, for the AWS account\. All future interaction should be through the AWS account's users and their own keys instead of the root user\. However, to perform some account and service management tasks, you must log in using the root user credentials\. To view the tasks that require you to sign in as the root user, see [AWS Tasks that Require Account Root User](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\.

## Creating an administrator IAM user and group \(console\)<a name="getting-started_create-admin-group-console"></a>

This procedure describes how to use the AWS Management Console to create an IAM user for yourself and add that user to a group that has administrative permissions from an attached managed policy\.

**To create an administrator user for yourself and add the user to an administrators group \(console\)**

1. Sign in to the [IAM console](https://console.aws.amazon.com/iam/) as the account owner by choosing **Root user** and entering your AWS account email address\. On the next page, enter your password\.
**Note**  
We strongly recommend that you adhere to the best practice of using the **Administrator** IAM user below and securely lock away the root user credentials\. Sign in as the root user only to perform a few [account and service management tasks](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\.

1. Enable access to billing data for the IAM admin user that you will create as follows:

   1. On the navigation bar, choose your account name, and then choose **My Account**\. 

   1. Next to **IAM User and Role Access to Billing Information**, choose **Edit**\. 

   1. Select the check box to **Activate IAM Access** and choose **Update**\.

   1. On the navigation bar, choose **Services** and then **IAM** to return to the IAM dashboard\.

1. In the navigation pane, choose **Users** and then choose **Add user**\.

1. On the **Details** page, do the following:

   1. For **User name**, type **Administrator**\.

   1. Select the check box for **AWS Management Console access**, select **Custom password**, and then type your new password in the text box\.

   1. By default, AWS forces the new user to create a new password when first signing in\. You can optionally clear the check box next to **User must create a new password at next sign\-in** to allow the new user to reset their password after they sign in\.

   1. Choose **Next: Permissions**\.

1. On the **Permissions** page, do the following:

   1. Choose **Add user to group**\.

   1. Choose **Create group**\.

   1. In the **Create group** dialog box, for **Group name** type **Administrators**\.

   1. Select the check box for the **AdministratorAccess** policy\.

   1. Choose **Create group**\.

   1. Back on the page with the list of groups, select the check box for your new group\. Choose **Refresh** if you don't see the new group in the list\.

   1. Choose **Next: Tags**\.

1. \(Optional\) On the **Tags** page, add metadata to the user by attaching tags as key\-value pairs\. For more information, see [Tagging IAM users and roles](id_tags.md)\.

1. Choose **Next: Review**\. Verify the group memberships to be added to the new user\. When you are ready to proceed, choose **Create user**\.

1. \(Optional\) On the **Complete** page, you can download a \.csv file with login information for the user, or send email with login instructions to the user\.

You can use this same process to create more groups and users and to give your users access to your AWS account resources\. To learn about using policies that restrict user permissions to specific AWS resources, see [Access management for AWS resources](access.md) and [Example IAM identity\-based policies](access_policies_examples.md)\. To add additional users to the group after it's created, see [Adding and removing users in an IAM group](id_groups_manage_add-remove-users.md)\.

## Creating an IAM user and group \(AWS CLI\)<a name="getting-started_create-admin-group-cli"></a>

If you followed the steps in the previous section, you used the AWS Management Console to set up an administrators group while creating the IAM user in your AWS account\. This procedure shows an alternative way to create a group\.

**Overview: Setting up an administrators group**

1. Create a group and give it a name \(for example, Admins\)\. For more information, see [Creating a group \(AWS CLI\)](#Using_CreateGroup)\. 

1. Attach a policy that gives the group administrative permissions—access to all AWS actions and resources\. For more information, see [Attaching a policy to the group \(AWS CLI\)](#Using_AddingAdminRightsPolicy)\. 

1. Add at least one user to the group\. For more information, see [Creating an IAM user in your AWS account](id_users_create.md)\. 

### Creating a group \(AWS CLI\)<a name="Using_CreateGroup"></a>

This section shows how to create a group in the IAM system\.

**Requirements**  
Install the AWS Command Line Interface \(AWS CLI\)\. For more information, see [Installing the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) in the *AWS Command Line Interface User Guide*\.

**To create an administrators group \(AWS CLI\)**

1. Type the [https://docs.aws.amazon.com/cli/latest/reference/iam/create-group.html](https://docs.aws.amazon.com/cli/latest/reference/iam/create-group.html) command with the name you've chosen for the group\. Optionally, you can include a path as part of the group name\. For more information about paths, see [Friendly names and paths](reference_identifiers.md#identifiers-friendly-names)\. The name can consist of letters, digits, and the following characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), underscore \(\_\), and hyphen \(\-\)\. The name is not case sensitive and can be a maximum of 128 characters in length\.

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

1. Type the [https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-groups.html) command to list the groups in your AWS account and confirm the group was created\.

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

### Attaching a policy to the group \(AWS CLI\)<a name="Using_AddingAdminRightsPolicy"></a>

This section shows how to attach a policy that lets any user in the group perform any action on any resource in the AWS account\. You do this by attaching the [AWS managed policy](access_policies_managed-vs-inline.md) called AdministratorAccess to the Admins group\. For more information about policies, see [Access management for AWS resources](access.md)\. 

**To add a policy giving full administrator permissions \(AWS CLI\)**

1. Type the [https://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html) command to attach the policy called AdministratorAccess to your Admins group\. The command uses the ARN of the AWS managed policy called AdministratorAccess\. 

   ```
   aws iam attach-group-policy --group-name Admins --policy-arn arn:aws:iam::aws:policy/AdministratorAccess
   ```

   If the command is successful, there is no response\.

1. Type the [https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-attached-group-policies.html) command to confirm the policy is attached to the Admins group\.

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

You can confirm the contents of a particular policy with the [https://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-policy.html) command\. 

**Important**  
After you have the administrators group set up, you must add at least one user to it\. For more information about adding users to a group, see [Creating an IAM user in your AWS account](id_users_create.md)\. 

## Related resources<a name="getting-started_create-admin-group-addl-resources"></a>

For related information found in the *Amazon Web Services General Reference*, see the following resources:
+ [AWS Tasks that Require Account Root User](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)

For related information in the *IAM User Guide*, see the following resources:
+ [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)
+ [IAM Tutorial: Delegate access to the billing console](tutorial_billing.md)