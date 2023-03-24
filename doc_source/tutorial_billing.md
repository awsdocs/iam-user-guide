# IAM tutorial: Delegate access to the billing console<a name="tutorial_billing"></a>

AWS account owners can delegate access to specific IAM users who need to view or manage the AWS Billing and Cost Management data for an AWS account\. The instructions that follow will help you set up a pretested scenario\. This scenario helps you gain hands\-on experience configuring billing permissions without concern for affecting your main AWS production account\. If you attach a managed policy to your IAM users instead of following this tutorial, you must first activate access to the AWS Billing and Cost Management console in [Step 1](#tutorial-billing-step1)\. 

**[Step 1: Activate access to billing data on your AWS test account](#tutorial-billing-step1)**  
If you create a single AWS account, only the AWS account owner \([AWS account root user](id_root-user.md)\) has access to view and manage billing information\. IAM users cannot access billing data until the account owner activates IAM access and also attaches policies that provide billing actions to the user or role\. To view additional tasks that require you to sign in as the root user, see [AWS Tasks that Require Account Root User](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\.  
If you [create a member account](https://docs.aws.amazon.com/cli/latest/reference/organizations/create-account.html) using AWS Organizations, this feature is enabled by default\.

**[Step 2: Attach billing policies to your user groups](#tutorial-billing-step2)**  
When you attach a policy to a user group, all members of that user group receive the complete set of access permissions that are associated with that policy\. In this scenario, you attach the billing policies to user groups containing only those users who require the billing access\.

**[Step 3: Test access to the billing console](#tutorial-billing-step3)**  
After you've completed the core tasks, you're ready to test the policy\. Testing ensures that the policy works the way you want it to\.

## Prerequisites<a name="tutorial-billing-prereqs"></a>

Create a test AWS account to use with this tutorial\. In this account create two test users and two test user groups as summarized in the following table\. Be sure to assign a password to each user so that you can sign in later in Step 4\.


| *Create user accounts* | *Create and configure user group accounts* | User name | User group name | Add user as a member | 
| --- | --- | --- | --- | --- | 
| FinanceManager | BillingFullAccessGroup | FinanceManager | 
| FinanceUser | BillingViewAccessGroup | FinanceUser | 

## Step 1: Activate access to billing data on your AWS test account<a name="tutorial-billing-step1"></a>

First, activate billing access for your test users in the AWS Billing and Cost Management console\.

**Note**  
If you [create a member account](https://docs.aws.amazon.com/cli/latest/reference/organizations/create-account.html) using AWS Organizations, this feature is enabled by default\.

**To activate IAM user and role access to the Billing and Cost Management console**

1. Sign in to the AWS Management Console with your root user credentials \(specifically, the email address and password that you used to create your AWS account\)\.

1. On the navigation bar, choose your account name, and then choose [Account](https://console.aws.amazon.com/billing/home#/account)\.

1. Next to **IAM User and Role Access to Billing Information**, choose **Edit**\.

1. Select the **Activate IAM Access** check box to activate access to the Billing and Cost Management console pages\.

1. Choose **Update**\.

 You can now use IAM policies to control which pages a user can access\.

After you have activated IAM user access, you can attach IAM policies to grant or deny access to specific billing features\. For more information about using policies to grant IAM users access to AWS Billing and Cost Management features, see [Using identity\-based policies \(IAM policies\) for Billing and Cost Management](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html) in the *AWS Billing User Guide*\.

## Step 2: Attach billing policies to your user groups<a name="tutorial-billing-step2"></a>

Now we are going to attach the appropriate AWS managed polices to the billing user groups that you created earlier\.

**To attach billing policies to your user groups**

1. In the navigation pane, choose **Policies** to display the full list of policies available to your AWS account\.

1. In the policy search box, enter **Billing**\. The list displays only the AWS managed policies that apply to billing functions\.

1. To give full access to your billing administrator, select the **Billing** AWS managed – job function policy\.

1. Select the **Actions** drop\-down arrow, and then choose **Attach** from the actions list\.

1. On the **Attach policy** page, in the **Filter** search box, enter **BillingFullAccessGroup**\.

1. In the list, select the user group and then select **Attach policy**\. You are returned to the **Policies** page\.

1. In the policy search box, enter **Billing**\. The list displays only the AWS managed policies that apply to billing functions\.

1. To give read\-only access to users that are monitoring billing activity, select the **AWSBillingReadOnlyAccess** AWS managed policy\.

1. Select the **Actions** drop\-down arrow, and then choose **Attach** from the actions list\.

1. On the **Attach policy** page, in the **Filter** search box, enter **BillingViewAccessGroup**\. 

1. In the list, select the user group and then select **Attach policy**\.

1. Sign out of the console, and then proceed to [Step 3: Test access to the billing console](#tutorial-billing-step3)\.

## Step 3: Test access to the billing console<a name="tutorial-billing-step3"></a>

We recommend that you test access by signing in as each of the test users to learn what your users might experience\. Use the following steps to sign in using both test accounts to see the difference between access rights\.

**To test billing access by signing in with both test users**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

1. Sign in with each user using the steps provided below so you can compare the different user experiences\.

   **Full access**

   1. Sign in to your AWS account as the user FinanceManager\.

   1. On the navigation bar, choose **FinanceManager@*<account alias or ID number>*** , and then choose **Billing Dashboard**\.

   1. Browse through the pages and choose the various buttons to ensure that you have full modify permissions\.

   **Read\-only access**

   1. Sign in to your AWS account as the user FinanceUser\.

   1. On the navigation bar, choose **FinanceUser@*<account alias or ID number>***, and then choose **Billing Dashboard**\.

   1. Browse through the pages\. Notice that you can display costs, reports, and billing data with no problems\. However, if you choose an option to modify a value, you receive an **Access Denied **message\. For example, on the **Preferences** page, choose any of the check boxes on the page, and then choose **Save preferences**\. The console message informs you that you need **ModifyBilling** permissions to make changes to that page\.

## Related resources<a name="tutorial-billing-addl-resources"></a>

For related information found in the *AWS Billing User Guide*, see the following resources:
+ [Activating Access to the Billing and Cost Management Console](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/grantaccess.html#ControllingAccessWebsite-Activate) 
+ [Allow full access to AWS services but deny IAM users access to the Billing and Cost Management console](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-example-policies.html#ExampleAllowAllDenyBilling)\.
+ [Billing Permissions Descriptions](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)

For related information in the *IAM User Guide*, see the following resources:
+ [Managed policies and inline policies](access_policies_managed-vs-inline.md)
+ [Controlling IAM users access to the AWS Management Console](console_controlling-access.md)
+ [Attaching a policy to an IAM user group](id_groups_manage_attach-policy.md)

## Summary<a name="tutorial-billing-summary"></a>

You've now successfully completed all of the steps necessary to delegate user access to the Billing and Cost Management console\. As a result, you've seen firsthand what your users billing console experience will be like\. You can now proceed to implement this logic in your production environment at your convenience\. 