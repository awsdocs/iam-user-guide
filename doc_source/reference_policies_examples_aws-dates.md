# AWS: Allows access based on date and time<a name="reference_policies_examples_aws-dates"></a>

This example shows how you might create a policy that allows access to actions based on date and time\. This policy restricts access to actions that occur between April 1, 2020 and June 30, 2020 \(UTC\), inclusive\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

To learn about using multiple conditions within the `Condition` block of an IAM policy, see [Multiple values in a condition](reference_policies_elements_condition.md#Condition-multiple-conditions)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "service-prefix:action-name",
            "Resource": "*",
            "Condition": {
                "DateGreaterThan": {"aws:CurrentTime": "2020-04-01T00:00:00Z"},
                "DateLessThan": {"aws:CurrentTime": "2020-06-30T23:59:59Z"}
            }
        }
    ]
}
```