# Controlling Access Using Tags<a name="access_tags"></a>

Before you use tags to control access, you must understand how AWS grants access\. AWS is composed of collections of *resources*\. An Amazon EC2 instance is a resource\. An Amazon S3 bucket is a resource\. When you use the AWS API, the AWS CLI, or the AWS Management Console to take an action \(such as creating an Amazon S3 bucket\), you send a *request* for that action\. Your request specifies an action, a resource, a *principal* \(user or role\), a *principal account*, and any necessary request information\. All of this information provides *context*\. 

AWS then checks that you \(the principal\) are authenticated \(signed in\) and authorized \(have permission\) to perform the specified action on the specified resource\. During authorization, IAM checks all the policies attached to your user or role and the policies attached to the resource that you are trying to access\. These checks are based on the context of your request\. AWS authorizes the request only if each part of your request is allowed by the policies\. 

To view a diagram and learn more about the IAM infrastructure, see [Understanding How IAM Works](intro-structure.md)\. For details about how IAM determines whether a request is allowed, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.

Tags can complicate this process because tags can be attached to the *resource* or passed in the *request* to services that support tagging\. To control access based on tags, you provide tag information in the [condition element](reference_policies_elements_condition.md) of a policy\. To learn whether an AWS service supports tagging, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Authorization based on tags** column\. Choose the name of the service to view the authorization and access control documentation for that service\.

When you create an IAM policy, you can use tag condition keys to control access to do any of the following:
+ **[Resource](#access_tags_control-resources)** – Control access to AWS service resources based on the tags on those resources\. To do this, use the **ResourceTag/*key\-name*** condition key to determine whether to allow access to the resource based on the tags that are attached to the resource\.
+ **[Request](#access_tags_control-requests)** – Control what tags can be passed in an IAM request\. To do this, use the **aws:RequestTag/*key\-name*** condition key to specify what tag key–value pairs can be added, changed, or removed from a resource\.
+ **[Tag Keys](#access_tags_control-tag-keys)** – Use the **aws:TagKeys** condition key to control whether specific tag keys can be used on a resource or in a request\. 

You can create an IAM policy visually, using JSON, or by importing an existing managed policy\. For details, see [Creating IAM Policies](access_policies_create.md)\.

## Controlling Access to Resources<a name="access_tags_control-resources"></a>

You can use conditions in your IAM policies to control access to AWS resources based on tags\.

 This example shows how you might create a policy that allows starting or stopping Amazon EC2 instances, but only if the instance tag `Owner` has the value of that user's user name\. This policy also grants the permissions necessary to complete this action on the console\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:StartInstances",
                "ec2:StopInstances"
            ],
            "Resource": "arn:aws:ec2:*:*:instance/*",
            "Condition": {
                "StringEquals": {"ec2:ResourceTag/Owner": "${aws:username}"}
            }
        },
        {
            "Effect": "Allow",
            "Action": "ec2:DescribeInstances",
            "Resource": "*"
        }
    ]
}
```

You can attach this policy to the IAM users in your account\. If a user named `richard-roe` attempts to start an Amazon EC2 instance, the instance must be tagged `Owner=richard-roe` or `owner=richard-roe`\. Otherwise he will be denied access\. The tag key `Owner` matches both `Owner` and `owner` because condition key names are not case\-sensitive\. For more information, see [IAM JSON Policy Elements: Condition](reference_policies_elements_condition.md)\.

## Controlling Access to Requests<a name="access_tags_control-requests"></a>

You can use conditions in your IAM policies to control what tags can be added, changed, or removed from an AWS resource\. 

This example shows how you might create a policy that allows using the Amazon EC2 `CreateTags` action to attach tags to an instance only if the tag contains the `environment` key and the `preprod` or `production` values\. As a best practice, use the `ForAllValues` modifier with the `aws:TagKeys` condition key to indicate that only the key `environment` is allowed in the request\. This stops users from including other keys, such as accidentally using `Environment` instead of `environment`\. 

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": "ec2:CreateTags",
        "Resource": "arn:aws:ec2:*:*:instance/*",
        "Condition": {
            "StringEquals": {
                "aws:RequestTag/environment": [
                    "preprod",
                    "production"
                ]
            },
            "ForAllValues:StringEquals": {"aws:TagKeys": "environment"}
        }
    }
}
```

## Controlling Tag Keys<a name="access_tags_control-tag-keys"></a>

You can use a condition in your IAM policies to control whether specific tag keys can be used on a resource or in a request\.

As a best practice, when you use policies to control access using tags, you should use the [`aws:TagKeys` condition key](reference_policies_condition-keys.md#condition-keys-tagkeys)\. AWS services that support tags might allow you to create multiple tag key names that differ only by case, such as tagging an Amazon EC2 instance with `foo=bar1` and `Foo=bar2`\. Key names are not case sensitive in policy conditions\. This means that if you specify `"ec2:ResourceTag:TagKey1": "Value1"` in the condition element of your policy, then the condition matches a resource tag key named either `TagKey1` or `tagkey1`, but not both\. To prevent duplicate tags with a key that varies only by case, use the `aws:TagKeys` condition to define the tag keys that your users can apply\.

This example shows how you might create a policy that allows creating and tagging a Secrets Manager secret, but only with the tag keys `environment` or `cost-center`\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "secretsmanager:CreateSecret",
            "secretsmanager:TagResource"
        ],
        "Resource": "*",
        "Condition": {
            "ForAllValues:StringEquals": {
                "aws:TagKeys": [
                    "environment",
                    "cost-center"
                ]
            }
        }
    }
}
```