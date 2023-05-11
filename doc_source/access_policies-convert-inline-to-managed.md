# Converting an inline policy to a managed policy<a name="access_policies-convert-inline-to-managed"></a>

If you have inline policies in your account, you can convert them to managed policies\. To do this, copy the policy to a new managed policy\. Next, attach the new policy to the identity that has the inline policy\. Then delete the inline policy\. 

**To convert an inline policy to a managed policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **User groups**, **Users**, or **Roles**\.

1. In the list, choose the name of the user group, user, or role that has the policy you want to remove\.

1. Choose the **Permissions** tab\.

1. For user groups, select the name of the inline policy that you want to remove\. For users and roles, choose **Show *n* more**, if necessary, and then expand the inline policy that you want to remove\.

1. Choose **Copy** to copy the JSON policy document for the policy\.

1. In the navigation pane, choose **Policies**\.

1. Choose **Create policy** and then choose the **JSON** option\.

1. Replace the existing text with your JSON policy text, and then choose **Next**\.

1. Enter a name and optional description for your policy and choose **Create policy**\.

1. In the navigation pane, choose **User groups**, **Users**, or **Roles**, and again choose the name of the user group, user, or role that has the policy you want to remove\.

1. Choose the **Permissions** tab and then choose **Add permissions**\.

1. For user groups, select the check box next to the name of your new policy, choose **Add permissions**, and then choose **Attach policy**\. For users or roles, choose **Add permissions**\. On the next page, choose **Attach existing policies directly**, select the check box next to the name of your new policy, choose **Next**, and then choose **Add permissions**\.

   You are returned to the **Summary** page for your user group, user, or role\.

1. Select the check box next to the inline policy that you want to remove and choose **Remove**\.