# IAM: Generate and retrieve IAM credential reports<a name="reference_policies_examples_iam-credential-report"></a>

This example shows how you might create a policy that allows users to generate and download a report that lists all IAM users in their AWS account\. The report includes the status of the users' credentials, including passwords, access keys, MFA devices, and signing certificates\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. 

For more information about credential reports, see [Getting credential reports for your AWS account](id_credentials_getting-report.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "iam:GenerateCredentialReport",
            "iam:GetCredentialReport"
        ],
        "Resource": "*"
    }
}
```