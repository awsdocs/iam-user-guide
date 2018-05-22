# Tutorial: Delegate Access to the Billing Console<a name="tutorial_billing"></a>

AWS account owners can delegate access to specific IAM users who need to view or manage the AWS Billing and Cost Management data for an AWS account\. The instructions that follow will help you set up a pretested scenario so you can gain hands\-on experience configuring billing permissions, without concern for affecting your main AWS production account\. 

This workflow has four basic steps\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

**[Step 1: Enable Access to Billing Data on Your AWS Test Account](#tutorial-billing-step1)**  
By default, only the AWS account owner \([AWS account root user](id_root-user.md)\) has access to view and manage billing information\. IAM users cannot access billing data until the account owner provides the user with permission\. To view additional tasks that require you to sign in as the root user, see [AWS Tasks that Require Account Root User](http://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)\.

**[Step 2: Create IAM Policies That Grant Permissions to Billing Data](#tutorial-billing-step2)**  
After enabling billing access on your account, you must still explicitly grant access to billing data to specific IAM users or groups\. You grant this access with a customer managed policy\.

**[Step 3: Attach Billing Policies to Your Groups](#tutorial-billing-step3)**  
When you attach a policy to a group, all members of that group receive the complete set of access permissions that are associated with that policy\. In this scenario, you attach the new billing policies to groups containing only those users who require the billing access\.

**[Step 4: Test Access to the Billing Console](#tutorial-billing-step4)**  
Once you’ve completed the core tasks, you’re ready to test the policy\. Testing ensures that the policy works the way you want it to\.

## Prerequisites<a name="tutorial-billing-prereqs"></a>

Create a test AWS account to use with this tutorial\. In this account create two test users and two test groups as summarized in the following table\. Be sure to assign a password to each user so that you can sign in later in Step 4\.


| *Create user accounts* | *Create and configure group accounts* | User Name | Group Name | Add user as a member | 
| --- | --- | --- | --- | --- | 
| FinanceManager | FullAccess | FinanceManager | 
| FinanceUser | ViewAccess | FinanceUser | 

## Step 1: Enable Access to Billing Data on Your AWS Test Account<a name="tutorial-billing-step1"></a>

Sign into your test account and turn on billing access\. For information about how to follow this process in a production environment, see [Activate Access to the AWS Website](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/grantaccess.html#ControllingAccessWebsite-Activate) in the *AWS Billing and Cost Management User Guide*\.

**To enable access to billing data on your AWS test account**

1. Use your AWS account email address and password to sign in to the [AWS Management Console](https://console.aws.amazon.com/) as the *[AWS account root user](id_root-user.md)*\.

1. On the navigation bar, choose your account name, and then choose **My Account**\.

1. Next to **IAM User and Role Access to Billing Information**, choose **Edit**, and then select the check box to activate IAM user and federated user access to the Billing and Cost Management pages\.

1. Sign out of the console, and then proceed to [Step 2: Create IAM Policies That Grant Permissions to Billing Data](#tutorial-billing-step2)\.

## Step 2: Create IAM Policies That Grant Permissions to Billing Data<a name="tutorial-billing-step2"></a>

Next, create custom policies that grant both view and full access permissions to the pages within the Billing and Cost Management console\. For general information about IAM permission policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\.

**To create IAM policies that grant permissions to billing data**

1. Sign in to the AWS Management Console as a user with administrator credentials\. To adhere to IAM best practices, don’t sign in with your root user credentials\. For more information, see [Create individual IAM users](best-practices.md#create-iam-users)\.

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. <a name="tutorial-billing-repeat"></a>In the navigation pane, choose **Policies**, and then choose **Create policy**\.

1. On the **Visual editor** tab, choose **Choose a service** to get started\. Then choose **Billing**\.

1. Follow these steps to create two policies:

   **Full access**

   1. Choose **Select actions** and then select the check box next to **All Actions \(\*\)**\. You do not need to select a resource or condition for this policy\.

   1. Choose **Review policy**\.

   1. On the **Review** page, next to **Name**, type **BillingFullAccess**, and then choose **Create policy** to save it\.

   **Read\-only access**

   1. Repeat steps [3 and 4](#tutorial-billing-repeat)\.

   1. Choose **Select actions** and then select the check box next to **Read**\. You do not need to select a resource or condition for this policy\.

   1. Choose **Review policy**\.

   1. On the **Review** page, for **Name**, type **BillingViewAccess**\. Then choose **Create policy** to save it\.

   To review descriptions for each of the permissions available in IAM policies that grant users access to the Billing and Cost Management console, see [Billing Permissions Descriptions](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)\.

## Step 3: Attach Billing Policies to Your Groups<a name="tutorial-billing-step3"></a>

Now that you have custom billing policies available, you can attach them to their corresponding groups that you created earlier\. Although you can attach a policy directly to a user or role, we recommend \(in accordance with IAM best practices\) that you use groups instead\. For more information, see [Use groups to assign permissions to IAM users](best-practices.md#use-groups-for-permissions)\. 

**To attach billing policies to your groups**

1. In the navigation pane, choose **Policies** to display the full list of policies available to your AWS account\. To attach each policy to its appropriate group, follow these steps:

   **Full access**

   1. In the search box, type **BillingFullAccess**, and then select the check box next to the policy name\. 

   1. Choose **Policy actions**, and then choose **Attach**\.

   1. In the search box, type **FinanceManager**, select the check box next to the name of the group, and then choose **Attach policy**\.

   **Read\-only access**

   1. In the search box, type **BillingViewAccess**, and then select the check box next to the policy name\.

   1. Choose **Policy actions**, and then choose **Attach**\.

   1. For **Filter**, choose **Groups**\. In the search box, type **FinanceUser**, select the check box next to the name of the group, and then choose **Attach policy**\.

1. Sign out of the console, and then proceed to [Step 4: Test Access to the Billing Console](#tutorial-billing-step4)\.

## Step 4: Test Access to the Billing Console<a name="tutorial-billing-step4"></a>

You can test user access in a couple of ways\. For this tutorial, we recommend that you test access by signing in as each of the test users so you can see what your users might experience\. Another \(optional\) way to test user access permissions is to use the [IAM policy simulator](https://policysim.aws.amazon.com/)\. Use the following steps if you want to see another way to view the effective result of these actions\.

Select either of the following procedures based on your preferred testing method\. In the first one, you sign in using both test accounts to see the difference between access rights\.

**To test billing access by signing in with both test user accounts**

1. Use your AWS account ID or account alias, your IAM user name, and your password to sign in to the [IAM console](https://console.aws.amazon.com/iam)\.
**Note**  
For your convenience, the AWS sign\-in page uses a browser cookie to remember your IAM user name and account information\. If you previously signed in as a different user, choose **Sign in to a different account** near the bottom of the page to return to the main sign\-in page\. From there, you can type your AWS account ID or account alias to be redirected to the IAM user sign\-in page for your account\.

1. Sign\-in with each account using the steps provided below so you can compare the different user experiences\.

   **Full access**

   1. Sign in to your AWS account as the user FinanceManager\.

   1. On the navigation bar, choose **FinanceManager@*<account alias or ID number>*** , and then choose **Billing & Cost Management**\.

   1. Browse through the pages and choose the various buttons to ensure that you have full modify permissions\. 

   **Read\-only access**

   1. Sign in to your AWS account as the user FinanceUser\.

   1. On the navigation bar, choose **FinanceUser@*<account alias or ID number>***, and then choose **Billing & Cost Management**\.

   1. Browse through the pages\. Notice that you can display costs, reports, and billing data with no problems\. However, if you choose an option to modify a value, you receive an **Access Denied **message\. For example, on the **Preferences** page, choose any of the check boxes on the page, and then choose **Save preferences**\. The console message informs you that you need **ModifyBilling** permissions to make changes to that page\.

The following optional procedure demonstrates how you could alternatively use the IAM policy simulator to test your delegated user’s effective permissions to billing pages\. 

**To test billing access by viewing effective permissions in the IAM policy simulator**

1. Open the IAM policy simulator at [https://policysim\.aws\.amazon\.com/](https://policysim.aws.amazon.com/)\. \(If you are not already signed in to AWS, you are prompted to sign in\)\. 

1. Under **Users, Groups, and Roles**, select one of the users that is a member of the group you recently attached the policy to\. 

1. Under **Policy Simulator**, choose **Select service**, and then choose **Billing**\. 

1. Next to **Select actions**, choose **Select All\.** 

1. Choose **Run Simulation** and compare the user’s listed permissions with all possible billing\-related permission options to make sure that the correct rights have been applied\. 

## Related Resources<a name="tutorial-billing-addl-resources"></a>

For related information found in the *AWS Billing and Cost Management User Guide*, see the following resources:
+ [Activate Access to the AWS Website](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/grantaccess.html#ControllingAccessWebsite-Activate) 
+ [Example 4: Allow full access to AWS services but deny IAM users access to the Billing and Cost Management console](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#ExampleAllowAllDenyBilling)\.
+ [Billing Permissions Descriptions](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)

For related information in the *IAM User Guide*, see the following resources:
+ [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)
+ [Controlling User Access to the AWS Management Console](console_controlling-access.md)
+ [Attaching a Policy to an IAM Group](id_groups_manage_attach-policy.md)

## Summary<a name="tutorial-billing-summary"></a>

You’ve now successfully completed all of the steps necessary to delegate user access to the Billing and Cost Management console\. As a result, you've seen firsthand what your users billing console experience will be like and can now proceed to implement this logic in your production environment at your convenience\. 