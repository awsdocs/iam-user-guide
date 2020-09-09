# IAM: Allows read\-only access to the IAM console without reporting<a name="reference_policies_examples_iam_read-only-console-no-reporting"></a>

This example shows how you might create a policy that allows IAM users to perform any IAM action that begins with the string `Get`, `List`, or `Generate`\. As users work with the console, the console makes requests to IAM to list groups, users, roles, and policies, and to generate reports about those resources\.

The asterisk acts as a wildcard\. When you use `iam:Get*` in a policy, the resulting permissions include all IAM actions that begin with `Get`, such as `GetUser` and `GetRole`\. Wildcards are useful if new types of entities are added to IAM in the future\. In that case, the permissions granted by the policy automatically allow the user to list and get the details about those new entities\. 

This policy can't be used for reporting purposes\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "iam:Get*",
            "iam:List*"
        ],
        "Resource": "*"
    }
}
```