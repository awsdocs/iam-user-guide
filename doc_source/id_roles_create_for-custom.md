# Creating a role using custom trust policies \(console\)<a name="id_roles_create_for-custom"></a>

You can create a custom trust policy to delegate access and allow others to perform actions in your AWS account\. For more information, see [Creating IAM policies](access_policies_create-console.md#access_policies_create-start)\.

For information about how to use roles to delegate permissions, see [Roles terms and concepts](id_roles_terms-and-concepts.md)\.

## Creating an IAM role using a custom trust policy \(console\)<a name="roles-creatingrole-custom-trust-policy-console"></a>

You can use the AWS Management Console to create a role that an IAM user can assume\. For example, assume that your organization has multiple AWS accounts to isolate a development environment from a production environment\. For high\-level information about creating a role that allows users in the development account to access resources in the production account, see [Example scenario using separate development and production accounts](id_roles_common-scenarios_aws-accounts.md#id_roles_common-scenarios_aws-accounts-example)\.

**To create a role using a custom trust policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the console, choose **Roles** and then choose **Create role**\.

1. Choose the **Custom trust policy** role type\.

1. In the **Custom trust policy** section, enter or paste the custom trust policy for the role\. For more information, see [Creating IAM policies](access_policies_create-console.md#access_policies_create-start)\.

1. Choose **Next**\.

1. Select the check box next to the custom trust policy you created\.

1. \(Optional\) Set a [permissions boundary](access_policies_boundaries.md)\. This is an advanced feature that is available for service roles, but not service\-linked roles\.

   Open the **Permissions boundary** section and choose **Use a permissions boundary to control the maximum role permissions**\. IAM includes a list of the AWS managed and customer managed policies in your account\. Select the policy to use for the permissions boundary\.

1. Choose **Next**\.

1. For **Role name**, the degree of role name customization is defined by the service\. If the service defines the role's name, this option is not editable\. In other cases, the service might define a prefix for the role and allow you to enter an optional suffix\. Some services allow you to specify the entire name of your role\.

   If possible, enter a role name or role name suffix\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because other AWS resources might reference the role, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Description**, enter a description for the new role\.

1. Choose **Edit** in the **Step 1: Select trusted entities** or **Step 2: Add permissions** sections to edit the custom policy and permissions for the role\. 

1. \(Optional\) Add metadata to the role by attaching tags as key–value pairs\. For more information about using tags in IAM, see [Tagging IAM resources](id_tags.md)\.

1. Review the role and then choose **Create role**\.