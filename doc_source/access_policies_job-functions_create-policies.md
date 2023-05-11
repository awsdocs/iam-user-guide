# Creating roles and attaching policies \(console\)<a name="access_policies_job-functions_create-policies"></a>

Several of the previously listed policies grant the ability to configure AWS services with roles that enable those services to perform operations on your behalf\. The job function policies either specify exact role names that you must use or at least include a prefix that specifies the first part of the name that can be used\. To create one of these roles, perform the steps in the following procedure\.

**To create a role for an AWS service \(IAM console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. Choose the **AWS service** role type\.

1. Choose the use case for your service\. Use cases are defined by the service to include the trust policy that the service requires\.

1. Choose **Next**\.

1. If possible, select the policy to use for the permissions policy\. Otherwise, choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-start) in the *IAM User Guide*\.

1. After you create the policy, close that tab and return to your original tab\. Select the check box next to the permissions policies that you want the service to have\.

   Depending on the use case that you selected, the service might let you do any of the following:
   + Nothing, because the service defines the permissions for the role\.
   + Choose from a limited set of permissions\.
   + Choose from any permissions\.
   + Select no policies at this time\. However, you can create the policies later, and then attach them to the role\.

1. \(Optional\) Set a [permissions boundary](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html)\. This is an advanced feature that is available for service roles, but not for service\-linked roles\. 

   Expand the **Permissions boundary** section and choose **Use a permissions boundary to control the maximum role permissions**\. IAM includes a list of the AWS managed and customer managed policies in your account\. Select the policy to use for the permissions boundary or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-start) in the *IAM User Guide*\. After you create the policy, close that tab and return to your original tab to select the policy to use for the permissions boundary\.

1. Choose **Next**\.

1. For **Role name**, the degree of role name customization is defined by the service\. If the service defines the role's name, this option is not editable\. In other cases, the service might define a prefix for the role and let you enter an optional suffix\. Some services let you specify the entire name of your role\.

   If possible, enter a role name or role name suffix to help you identify the purpose of this role\. Role names must be unique within your AWS account\. Because role names are case insensitive, you cannot create roles named both **PRODROLE** and **prodrole**\. Various entities might reference the role\. Therefore, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Description**, enter a description for the new role\.

1. Choose **Edit** in the **Step 1: Select trusted entities** or **Step 2: Select permissions** sections to edit the use cases and permissions for the role\. 

1. \(Optional\) Add metadata to the role by attaching tags as key\-value pairs\. For more information about using tags in IAM, see [Tagging IAM resources](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html) in the *IAM User Guide*\.

1. Review the role, and then choose **Create role**\.

## Example 1: Configuring a user as a database administrator \(console\)<a name="jf_example_1"></a>

This example shows the steps required to configure Alice, an IAM user, as a [Database Administrator](access_policies_job-functions.md#jf_database-administrator)\. You use the information in first row of the table in that section and allow the user to enable Amazon RDS monitoring\. You attach the [DatabaseAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/DatabaseAdministrator) policy to Alice's IAM user so that they can manage the Amazon database services\. That policy also allows Alice to pass a role called `rds-monitoring-role` to the Amazon RDS service that allows the service to monitor the Amazon RDS databases on their behalf\.

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Policies**, type **database** in the search box, and then press enter\.

1. Select the radio button for the **DatabaseAdministrator** policy, choose **Actions**, and then choose **Attach**\.

1. In the list of entities, select **Alice** and then choose **Attach policy**\. Alice now can administer AWS databases\. However, to allow Alice to monitor those databases, you must configure the service role\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. Choose the **AWS Service** role type, and then choose **Amazon RDS**\.

1. Choose the **Amazon RDS Role for Enhanced Monitoring** use case\.

1. Amazon RDS defines the permissions for your role\. Choose **Next: Review** to continue\.

1. The role name must be one of those specified by the DatabaseAdministrator policy that Alice now has\. One of those is **rds\-monitoring\-role**\. Enter that for the **Role name**\.

1. \(Optional\) For **Role description**, enter a description for the new role\.

1. After you review the details, choose **Create role**\.

1. Alice can now enable **RDS Enhanced Monitoring** in the **Monitoring** section of the Amazon RDS console\. For example, they might do this when they create a DB instance, create a read replica, or modify a DB instance\. They must enter the role name they created \(rds\-monitoring\-role\) in the **Monitoring Role** box when they set **Enable Enhanced Monitoring** to **Yes**\. 

## Example 2: Configuring a user as a network administrator \(console\)<a name="jf_example_2"></a>

This example shows the steps required to configure Jorge, an IAM user, as a [Network Administrator](access_policies_job-functions.md#jf_network-administrator)\. It uses the information in the table in that section to allow Jorge to monitor IP traffic going to and from a VPC\. It also allows Jorge to capture that information in the logs in CloudWatch Logs\. You attach the [NetworkAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/NetworkAdministrator) policy to Jorge's IAM user so that they can configure AWS network resources\. That policy also allows Jorge to pass a role whose name begins with `flow-logs*` to Amazon EC2 when you create a flow log\. In this scenario, unlike Example 1, there isn't a predefined service role type, so you must perform a few steps differently\.

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies** and then enter **network** in the search box, and then press enter\.

1. Select the radio button next to **NetworkAdministrator** policy, choose **Actions**, and then choose **Attach**\.

1. In the list of users, select the check box next to **Jorge** and then choose **Attach policy**\. Jorge can now administer AWS network resources\. However, to enable monitoring of IP traffic in your VPC, you must configure the service role\.

1. Because the service role you need to create doesn't have a predefined managed policy, you must first create it\. In the navigation pane, choose **Policies**, then choose **Create policy**\.

1. In the **Policy editor** section, choose the **JSON** option and copy the text from the following JSON policy document\. Paste this text into the **JSON** text box\. 

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Action": [
           "logs:CreateLogGroup",
           "logs:CreateLogStream",
           "logs:PutLogEvents",
           "logs:DescribeLogGroups",
           "logs:DescribeLogStreams"
         ],
         "Effect": "Allow",
         "Resource": "*"
       }
     ]
   }
   ```

1.  Resolve any security warnings, errors, or general warnings generated during [policy validation](access_policies_policy-validator.md), and then choose **Next**\. 
**Note**  
You can switch between the **Visual** and **JSON** editor options any time\. However, if you make changes or choose **Next** in the **Visual** editor, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review and create** page, type **vpc\-flow\-logs\-policy\-for\-service\-role** for the policy name\. Review the **Permissions defined in this policy** to see the permissions granted by your policy, and then choose **Create policy** to save your work\.

   The new policy appears in the list of managed policies and is ready to attach\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. Choose the **AWS Service** role type, and then choose **Amazon EC2**\.

1. Choose the **Amazon EC2** use case\.

1. On the **Attach permissions policies** page, choose the policy you created earlier, **vpc\-flow\-logs\-policy\-for\-service\-role**, and then choose **Next: Review**\.

1. The role name must be permitted by the NetworkAdministrator policy that Jorge now has\. Any name that begins with `flow-logs-` is allowed\. For this example, enter **flow\-logs\-for\-jorge** for the **Role name**\.

1. \(Optional\) For **Role description**, enter a description for the new role\.

1. After you review the details, choose **Create role**\.

1. Now you can configure the trust policy required for this scenario\. On the **Roles** page, choose the **flow\-logs\-for\-jorge** role \(the name, not the check box\)\. On the details page for your new role, choose the **Trust relationships** tab, and then choose **Edit trust relationship**\.

1. Change the "Service" line to read as follows, replacing the entry for `ec2.amazonaws.com`:

   ```
           "Service": "vpc-flow-logs.amazonaws.com"
   ```

1. Jorge can now create flow logs for a VPC or subnet in the Amazon EC2 console\. When you create the flow log, specify the **flow\-logs\-for\-jorge** role\. That role has the permissions to create the log and write data to it\.