# Previewing access in Amazon S3 console<a name="access-analyzer-preview-access-s3-console"></a>

After you complete your bucket policy in the Amazon S3 console you have the option to preview public and cross\-account access to your Amazon S3 bucket\. You can validate that your policy changes grant only intended external access before you choose **Save changes**\. This optional step enables you to preview AWS IAM Access Analyzer findings for your bucket\. You can validate whether the policy change introduces new findings or resolves existing findings for external access\. You can skip this validation step and save your Amazon S3 bucket policy at any time\.

To preview external access to your bucket, you must have an active account analyzer in your bucket’s region with the account as the zone of trust\. You must also have the permissions required to use Access Analyzer and preview access\. For more information on enabling Access Analyzer and permissions required, see [Enabling Access Analyzer](access-analyzer-getting-started.md#access-analyzer-enabling)\.

**To preview access to your Amazon S3 bucket when you create or edit your bucket policy**

1. Once you are done creating or editing your bucket policy, ensure your policy is a valid Amazon S3 bucket policy\. The policy ARN must match the bucket ARN and the [policy elements](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-policy-language-overview.html) must be valid\.

1. Below the policy, under **Preview external access**, choose an active account analyzer, then choose **Preview**\. A preview of Access Analyzer findings is generated for your bucket\. The preview analyzes the displayed Amazon S3 bucket policy, together with the existing bucket permissions\. This includes the bucket and account BPA settings, bucket ACL, the Amazon S3 access points attached to the bucket, and their policies and BPA settings\.

1. When the access preview is complete, a preview of Access Analyzer findings is displayed\. Each finding reports an instance of a principal outside of the account that would have access to your bucket after you save the policy\. You can validate access to your bucket by reviewing each finding\. The finding header provides a summary of the access and you can expand the finding to review the [finding details](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-findings-view.html)\. Finding badges provide context on how saving the bucket policy would change access to the bucket\. For example, they help you validate whether the policy change introduces new findings or resolves existing findings for external access:

   1. **New** – indicates a finding for new external access that the policy would introduce\.

   1. **Resolved** – indicates a finding for existing external access that the policy would remove\.

   1. **Archived** – indicates a finding for new external access that would be automatically archived, based on the archive rules for the analyzer that define when findings should be marked as intended\.

   1. **Existing** – indicates an existing finding for external access that would remain unchanged\.

   1. **Public** – if a finding is for public access to the resource, it will have a **Public** badge, in addition to one of the badges above\.

1. If you identify external access you do not intend to introduce or remove, you can revise the policy and then choose **Preview** again until you have achieved the external access you intend\. If you have a finding labeled **Public**, we recommend you revise the policy to remove public access before you choose **Save changes**\. Previewing access is an optional step and you can choose **Save changes** at any time\. 