# AWS: Allows specific access using MFA within specific dates<a name="reference_policies_examples_aws_mfa-dates"></a>

This example shows how you might create a policy that uses multiple conditions, which are evaluated using a logical `AND`\. It allows full access to the service named `SERVICE-NAME-1`, and access to the `ACTION-NAME-A` and `ACTION-NAME-B` actions in the service named `SERVICE-NAME-2`\. These actions are allowed only when the user is authenticated using [multifactor authentication \(MFA\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html)\. Access is restricted to actions that occur between July 1, 2017 and December 31, 2017 \(UTC\), inclusive\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

To learn about using multiple conditions within the `Condition` block of an IAM policy, see [Multiple values in a condition](reference_policies_elements_condition.md#Condition-multiple-conditions)\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "service-prefix-1:*",
            "service-prefix-2:action-name-a",
            "service-prefix-2:action-name-b"
        ],
        "Resource": "*",
        "Condition": {
            "Bool": {"aws:MultiFactorAuthPresent": true},
            "DateGreaterThan": {"aws:CurrentTime": "2017-07-01T00:00:00Z"},
            "DateLessThan": {"aws:CurrentTime": "2017-12-31T23:59:59Z"}
        }
    }
}
```