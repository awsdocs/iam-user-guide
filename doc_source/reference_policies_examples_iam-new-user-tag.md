# IAM: Create new users only with specific tags<a name="reference_policies_examples_iam-new-user-tag"></a>

This example shows how you might create a policy that allows the creation of IAM users but only with one or both of the `Department` and `JobFunction` tag keys\. The `Department` tag key must have either the `Development` or `QualityAssurance` tag value\. The `JobFunction` tag key must have the `Employee` tag value\. You can use this policy to require that new users have a specific job function and department\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

The first condition in the statement uses the `StringEqualsIfExists` condition operator\. If a tag with the `Department` or `JobFunction` key is present in the request, then the tag must have the specified value\. If neither key is present, then this condition is evaluated as true\. The only way that the condition evaluates as false is if one of the specified condition keys is present in the request, but has a different value than those allowed\. For more information about using `IfExists`, see [\.\.\.IfExists condition operators](reference_policies_elements_condition_operators.md#Conditions_IfExists)\.

The second condition uses the `ForAllValues:StringEquals` condition operator\. The condition returns true if there's a match between all every one of the specified tag keys specified in the request, and at least one value in the policy\. This means that all of the tags in the request must be in this list\. However, the request can include only one of the tags in the list\. For example, you can create an IAM user with only the `Department=QualityAssurance` tag\. However, you cannot create an IAM user with the `JobFunction=employee` tag and the `Project=core` tag\. For more information about using `ForAllValues`, see [Creating a condition with multiple keys or values](reference_policies_multi-value-conditions.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "TagUsersWithOnlyTheseTags",
            "Effect": "Allow",
            "Action": [
                "iam:CreateUser",
                "iam:TagUser"
            ],
            "Resource": "*",
            "Condition": {
                "StringEqualsIfExists": {
                    "aws:RequestTag/Department": [
                        "Development",
                        "QualityAssurance"
                    ],
                    "aws:RequestTag/JobFunction": "Employee"
                },
                "ForAllValues:StringEquals": {
                    "aws:TagKeys": [
                        "Department",
                        "JobFunction"
                    ]
                }
            }
        }
    ]
}
```