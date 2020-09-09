# IAM: View service last accessed information for an Organizations policy<a name="reference_policies_examples_iam_service-accessed-data-orgs"></a>

This example shows how you might create a policy that allows viewing service last accessed information for a specific Organizations policy\. This policy allows retrieving data for the service control policy \(SCP\) with the `p-policy123` ID\. The person who generates and views the report must be authenticated using AWS Organizations master account credentials\. This policy allows the requester to retrieve the data for any Organizations entity in their organization\. This policy also grants the necessary permissions to complete this action on the console\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

For important information about last accessed information, including permissions required, troubleshooting, and supported Regions, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Sid": "AllowOrgsReadOnlyAndIamGetReport",
        "Effect": "Allow",
        "Action": [
            "iam:GetOrganizationsAccessReport",
            "organizations:Describe*",
            "organizations:List*"
        ],
        "Resource": "*"
    },
    {
        "Sid": "AllowGenerateReportOnlyForThePolicy",
        "Effect": "Allow",
        "Action": "iam:GenerateOrganizationsAccessReport",
        "Resource": "*",
        "Condition": {
            "StringEquals": {"iam:OrganizationsPolicyId": "p-policy123"}
        }
    }
}
```