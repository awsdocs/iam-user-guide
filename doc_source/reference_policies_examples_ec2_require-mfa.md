# Amazon EC2: Requires MFA \(GetSessionToken\) for specific EC2 operations<a name="reference_policies_examples_ec2_require-mfa"></a>

This example shows how you might create a policy that allows full access to all AWS API operations in Amazon EC2\. However, it explicitly denies access to `StopInstances` and `TerminateInstances` API operations if the user is not authenticated using [multi\-factor authentication \(MFA\)](id_credentials_mfa.md)\. To do this programmatically, the user must include optional `SerialNumber` and `TokenCode` values while calling the `GetSessionToken` operation\. This operation returns temporary credentials that were authenticated using MFA\. To learn more about GetSessionToken, see [[GetSessionToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html)—temporary credentials for users in untrusted environments](id_credentials_temp_request.md#api_getsessiontoken)\.

What does this policy do?
+ The `AllowAllActionsForEC2` statement allows all Amazon EC2 actions\.
+ The `DenyStopAndTerminateWhenMFAIsNotPresent` statement denies the `StopInstances` and `TerminateInstances` actions when the MFA context is missing\. This means that the actions are denied when the multi\-factor authentication context is missing \(meaning MFA was not used\)\. A deny overrides the allow\.

**Note**  
The condition check for `MultiFactorAuthPresent` in the `Deny` statement should not be a `{"Bool":{"aws:MultiFactorAuthPresent":false}}` because that key is not present and cannot be evaluated when MFA is not used\. So instead, use the `BoolIfExists` check to see whether the key is present before checking the value\. For more information, see [\.\.\.IfExists condition operators](reference_policies_elements_condition_operators.md#Conditions_IfExists)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowAllActionsForEC2",
            "Effect": "Allow",
            "Action": "ec2:*",
            "Resource": "*"
        },
        {
            "Sid": "DenyStopAndTerminateWhenMFAIsNotPresent",
            "Effect": "Deny",
            "Action": [
                "ec2:StopInstances",
                "ec2:TerminateInstances"
            ],
            "Resource": "*",
            "Condition": {
                "BoolIfExists": {"aws:MultiFactorAuthPresent": false}
            }
        }
    ]
}
```