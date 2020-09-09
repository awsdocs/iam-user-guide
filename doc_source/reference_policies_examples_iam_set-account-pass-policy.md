# IAM: Allows setting the account password requirements programmatically and in the console<a name="reference_policies_examples_iam_set-account-pass-policy"></a>

This example shows how you might create a policy that allows a user to view and update their account's password requirements\. The password requirements specify the complexity requirements and mandatory rotation periods for the account members' passwords\. This policy also grants the necessary permissions to complete this action on the console\.

To learn how to set the account password requirements policy for your account, see [Setting an account password policy for IAM users](id_credentials_passwords_account-policy.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "iam:GetAccountPasswordPolicy",
            "iam:UpdateAccountPasswordPolicy"
        ],
        "Resource": "*"
    }
}
```