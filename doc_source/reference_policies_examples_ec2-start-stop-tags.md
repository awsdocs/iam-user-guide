# EC2: Start or stop instances based on tags<a name="reference_policies_examples_ec2-start-stop-tags"></a>

This example shows how you might create a policy that allows starting or stopping instances with the tag key–value pair `Project = DataAnalytics`, but only by principals with the tag key–value pair `Department = Data`\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

The condition in the policy returns true if both parts of the condition are true\. The instance must have the `Project=DataAnalytics` tag\. In addition, the IAM principal \(user or role\) making the request must have the `Department=Data` tag\. 

**Note**  
As a best practice, attach policies with the `aws:PrincipalTag` condition key to IAM groups, for the case where some users might have the specified tag and some might not\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "StartStopIfTags",
            "Effect": "Allow",
            "Action": [
                "ec2:StartInstances",
                "ec2:StopInstances",
                "ec2:DescribeTags"
            ],
            "Resource": "arn:aws:ec2:region:account-id:instance/*",
            "Condition": {
                "StringEquals": {
                    "ec2:ResourceTag/Project": "DataAnalytics",
                    "aws:PrincipalTag/Department": "Data"
                }
            }
        }
    ]
}
```