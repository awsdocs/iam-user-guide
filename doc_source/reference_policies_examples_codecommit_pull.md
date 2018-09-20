# AWS CodeCommit: Allows `Read` Access to an AWS CodeCommit Repository, Programmatically and in the Console<a name="reference_policies_examples_codecommit_pull"></a>

This example shows how you might create a policy that allows `Read` access to a specific CodeCommit repository\. This policy also provides the permissions necessary to complete this action on the console\. To use this policy, replace the red text in the example policy with your own information\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": ["codecommit:GitPull"],
            "Resource": "arn:aws:codecommit:*:*:<REPO-NAME>"
        },
        {
            "Effect": "Allow",
            "Action": [
                "codecommit:Get*",
                "codecommit:BatchGetRepositories",
                "codecommit:List*"
            ],
            "Resource": "*"
        }
    ]
}
```