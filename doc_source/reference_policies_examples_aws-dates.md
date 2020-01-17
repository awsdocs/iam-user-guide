# AWS: Allows Access Within Specific Dates<a name="reference_policies_examples_aws-dates"></a>

This example shows how you might create a policy that allows access to the `ACTION-NAME` action in the service named `SERVICE-NAME`\. Access is restricted to actions that occur between July 1, 2017 and December 31, 2017 \(UTC\), inclusive\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\.

To learn about using multiple conditions within the `Condition` block of an IAM policy, see [Multiple Values in a Condition](reference_policies_elements_condition.md#Condition-multiple-conditions)\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": "service-prefix:action-name",
        "Resource": "*",
        "Condition": {
            "DateGreaterThan": {"aws:CurrentTime": "2017-07-01T00:00:00Z"},
            "DateLessThan": {"aws:CurrentTime": "2017-12-31T23:59:59Z"}
        }
    }
}
```