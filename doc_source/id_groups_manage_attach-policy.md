# Attaching a policy to an IAM group<a name="id_groups_manage_attach-policy"></a>

You can attach an [AWS managed policy](access_policies_managed-vs-inline.md#aws-managed-policies)—that is, a prewritten policy provided by AWS—to a group, as explained in the following steps\. To attach a customer managed policy—that is, a policy with custom permissions that you create—you must first create the policy\. For information about creating customer managed policies, see [Creating IAM policies](access_policies_create.md)\. 

For more information about permissions and policies, see [Access management for AWS resources](access.md)\. 

**To attach a policy to a group \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, select **Policies**\. 

1. In the list of policies, select the check box next to the name of the policy to attach\. You can use the **Filter** menu and the search box to filter the list of policies\. 

1. Click **Policy actions**, then click **Attach**\.

1. For **Filter**, choose **All Types**, then click **Groups**\. 

1. Select the check box next to the name of the group to attach the policy to, then click **Attach policy**\. 

**To attach a policy to a group \(AWS CLI or AWS API\)**

Do either of the following:
+ AWS CLI: [aws iam attach\-group\-policy](https://docs.aws.amazon.com/cli/latest/reference/iam/attach-group-policy.html)
+ AWS API: [AttachGroupPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachGroupPolicy.html) 