# Attaching a policy to an IAM user group<a name="id_groups_manage_attach-policy"></a>

You can attach an [AWS managed policy](access_policies_managed-vs-inline.md#aws-managed-policies)—that is, a prewritten policy provided by AWS—to a user group, as explained in the following steps\. To attach a customer managed policy—that is, a policy with custom permissions that you create—you must first create the policy\. For information about creating customer managed policies, see [Creating IAM policies](access_policies_create.md)\. 

For more information about permissions and policies, see [Access management for AWS resources](access.md)\. 

**To attach a policy to a user group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **User groups** and then choose the name of the group\.

1. Choose the **Permissions** tab\.

1. Choose **Add permissions** and then choose **Attach policy**\.

1. The current policies attached to the user group are displayed in the **Current permissions policies** list\. In the list of **Other permissions policies**, select the check box next to the names of the policies to attach\. You can use the search box to filter the list of policies by type and policy name\.

1. Choose **Attach policies**\.

**To attach a policy to a user group \(AWS CLI or AWS API\)**

Do either of the following:
+ AWS CLI: [aws iam attach\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html)
+ AWS API: [AttachGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachGroupPolicy.html) 