# IAM Tutorial: Create and attach your first customer managed policy<a name="tutorial_managed-policies"></a>

In this tutorial, you use the AWS Management Console to create a [customer managed policy](access_policies_managed-vs-inline.md#customer-managed-policies) and then attach that policy to an IAM user in your AWS account\. The policy you create allows an IAM test user to sign in directly to the AWS Management Console with read\-only permissions\. 

This workflow has three basic steps:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

**[Step 1: Create the policy](#step1-create-policy)**  
By default, IAM users do not have permissions to do anything\. They cannot access the AWS Management Console or manage the data within unless you allow it\. In this step, you create a customer managed policy that allows any attached user to sign in to the console\.

**[Step 2: Attach the policy](#step2-attach-policy)**  
When you attach a policy to a user, the user inherits all of the access permissions that are associated with that policy\. In this step, you attach the new policy to a test user account\.

**[Step 3: Test user access ](#step3-test-access)**  
Once the policy is attached, you can sign in as the user and test the policy\. 

## Prerequisites<a name="tutorial-managed-policies-prereqs"></a>

To perform the steps in this tutorial, you need to already have the following:
+ An AWS account that you can sign in to as an IAM user with administrative permissions\.
+ A test IAM user that has no permissions assigned or group memberships as follows:  
****    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_managed-policies.html)

## Step 1: Create the policy<a name="step1-create-policy"></a>

In this step, you create a customer managed policy that allows any attached user to sign in to the AWS Management Console with read\-only access to IAM data\.

**To create the policy for your test user**

1. Sign in to the IAM console at https://console\.aws\.amazon\.com/iam/ with your user that has administrator permissions\.

1. In the navigation pane, choose **Policies**\. 

1. In the content pane, choose **Create policy**\. 

1. Choose the **JSON** tab and copy the text from the following JSON policy document\. Paste this text into the **JSON** text box\. 

   ```
   {
       "Version": "2012-10-17",
       "Statement": [ {
           "Effect": "Allow",
           "Action": [
               "iam:GenerateCredentialReport",
               "iam:Get*",
               "iam:List*"
           ],
           "Resource": "*"
       } ]
   }
   ```

1. When you are finished, choose **Review policy**\. The [Policy Validator](access_policies_policy-validator.md) reports any syntax errors\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs anytime\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review** page, type **UsersReadOnlyAccessToIAMConsole** for the policy name\. Review the policy **Summary** to see the permissions granted by your policy, and then choose **Create policy** to save your work\.

   The new policy appears in the list of managed policies and is ready to attach\.

## Step 2: Attach the policy<a name="step2-attach-policy"></a>

Next you attach the policy you just created to your test IAM user\. 

**To attach the policy to your test user**

1. In the IAM console, in the navigation pane, choose **Policies**\.

1. At the top of the policy list, in the search box, start typing **UsersReadOnlyAccesstoIAMConsole** until you can see your policy\. Then check the box next to **UsersReadOnlyAccessToIAMConsole** in the list\. 

1. Choose the **Policy actions** button, and then chose **Attach**\. 

1. For **Filter**, choose **Users**\. 

1. In the search box, start typing **PolicyUser** until that user is visible on the list\. Then check the box next to that user in the list\.

1. Choose **Attach Policy**\. 

You have attached the policy to your IAM test user, which means that user now has read\-only access to the IAM console\. 

## Step 3: Test user access<a name="step3-test-access"></a>

For this tutorial, we recommend that you test access by signing in as the test user so you can see what your users might experience\. 

**To test access by signing in with your test user account**

1. Sign in to the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/) with your `PolicyUser` test user\.

1. Browse through the pages of the console and try to create a new user or group\. Notice that `PolicyUser` can display data but cannot create or modify existing IAM data\.

## Related resources<a name="tutorial-managed-policies-addl-resources"></a>

For related information in the *IAM User Guide*, see the following resources:
+ [Managed policies and inline policies](access_policies_managed-vs-inline.md)
+ [Controlling user access to the AWS Management Console](console_controlling-access.md)
+ [Create individual IAM users](best-practices.md#create-iam-users)

## Summary<a name="tutorial-managed-policies-summary"></a>

You've now successfully completed all of the steps necessary to create and attach a customer managed policy\. As a result, you are able to sign in to the IAM console with your test account to see what the experience is like for your users\.