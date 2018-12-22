# AWS CodeCommit: Allows `Read` Access to an AWS CodeCommit Repository, Programmatically and in the Console<a name="reference_policies_examples_codecommit_pull"></a>

This example shows how you might create a policy that allows `Read` access to the `MyDemoRepo` CodeCommit repository\. This policy also grants the permissions necessary to complete this action on the console\. To use this policy, replace the red italicized text in the example policy with your own information\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AccessSpecificRepo",
            "Effect": "Allow",
            "Action": ["codecommit:GitPull"],
            "Resource": "arn:aws:codecommit:*:*:MyDemoRepo"
        },
        {
            "Sid": "ViewRepositoriesConsole",
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