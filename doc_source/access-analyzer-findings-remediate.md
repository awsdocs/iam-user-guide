# Resolving Findings<a name="access-analyzer-findings-remediate"></a>

To resolve findings generated from access that you did not intend to allow, modify the policy statement to remove the permissions that allow access to the identified resource\. For example, for findings on S3 buckets, use the Amazon S3 console to configure the permissions on the bucket\. For IAM roles, use the IAM console to [modify the trust policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_manage_modify.html#roles-managingrole_edit-trust-policy) for the listed IAM role\. Use the console for the other supported resources to modify the policy statements that resulted in a generated finding\.

After you make a change to resolve a finding, such as modifying a policy applied to an IAM role, Access Analyzer scans the resource again\. If the resource is no longer shared outside of your zone of trust, the status of the finding is changed to Resolved\. The finding is no longer displayed in the **Active findings** table, and instead is displayed in the **Resolved findings** table\.

**Note**  
This does not apply to Error findings\. When Access Analyzer is not able to access a resource, it generates an error finding\. If you resolve the issue that prevented Access Analyzer from accessing the resource, the error finding is removed completely rather than changing to a resolved finding\.

If the changes you made resulted in the resource being shared outside of your zone of trust, but in a different way, such as with a different principal or for a different permission, Access Analyzer generates a new Active finding\.

**Note**  
It may take up to 30 minutes after a policy is modified for Access Analyzer to again analyze the resource and then update the finding\. Resolved findings are deleted 90 after the last update to the finding status\.