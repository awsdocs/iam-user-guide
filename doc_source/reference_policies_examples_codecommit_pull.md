# AWS CodeCommit: Allows Performing Git Operations on a CodeCommit Repository<a name="reference_policies_examples_codecommit_pull"></a>

This example shows how you might create a policy that allows using Git to pull from or push to the `MyDemoRepo` CodeCommit repository\. To use this policy, replace the red italicized text in the example policy with your own information\.

 In CodeCommit, `codecommit:GitPull` applies to any Git client command where data is retrieved from CodeCommit\. These commands include **git fetch** and **git clone**\. Similarly, `codecommit:GitPush` applies to any Git client command where data is sent to CodeCommit\. For example, this policy allows the deletion of a branch using the Git protocol\. This action is separate from the `codecommit:DeleteBranch` permission that applies to actions performed with the console, the AWS CLI, the SDKs, and the API, but not the Git protocol\. 

As a [best practice](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#bp-use-aws-defined-policies), get started using CodeCommit permissions with AWS managed policies\. For more information, see [AWS Managed \(Predefined\) Policies for CodeCommit](https://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#managed-policies) in the *AWS CodeCommit User Guide*\. 

When you're ready to update your permissions to [grant least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege), review CodeCommit example policies\. For details, see [Customer Managed Policy Examples](https://docs.aws.amazon.com/codecommit/latest/userguide/auth-and-access-control-iam-identity-based-access-control.html#customer-managed-policies) in the *AWS CodeCommit User Guide*\. 

```
{    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "codecommit:GitPull",
                "codecommit:GitPush"
            ],
            "Resource": "arn:aws:codecommit:us-east-2:111111111111:MyDemoRepo"
        }
    ]
}
```