# AWS: Access only resources in your account<a name="reference_policies_examples_aws_access-resource-policy"></a>

This example shows how you might create an IAM policy that allows access only to resources in your account\. Add this statement to your identity\-based policies when you want to restrict access only to trusted resources in a particular account\. This policy grants the permissions necessary to complete this action programatically from the AWS API or AWS CLI\.

To use this policy, replace the example account number with your account information\. To learn more about creating or editing IAM policies, see [Creating IAM policies](access_policies_create.md) and [Managing IAM policies](access_policies_manage.md)\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccounts",
      "Action": "s3:*",
      "Effect": "Deny",
      "Resource": [
        "arn:aws:s3:::*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
         "1234567890abcdef0"
          ]
      }
    }
 }
}
```

## Adapting the policy to your environment<a name="adapt-your-environ"></a>

The use of `aws:ResourceAccount` in your identity\-based policies can impact the user or the ability of the role to utilize some AWS services interacting with resources in accounts owned by a service\. The following table displays some services that require your principals to interact with Amazon resources such as [Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html) buckets owned by the service accounts\.


**Services that require principal interaction with AWS service accounts**  

| Service | Link to documentation | Service owned resources list | Actions | 
| --- | --- | --- | --- | 
| AWS Data Exchange | [AWS Data Exchange Access Control](https://docs.aws.amazon.com/data-exchange/latest/userguide/access-control.html) | arn:aws:s3:::\*aws\-data\-exchange\* |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_examples_aws_access-resource-policy.html)  | 
| AWS CloudFormation Stack Sets | [AWS CloudFormation Grant self\-managed permissions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-prereqs-self-managed.html) | arn:aws:sns:us\-east\-1:stack set service account number: stack set name |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_examples_aws_access-resource-policy.html)  | 
|  IAM  |  IAM managed policies are owned by the IAM service accounts\.  | Managed IAM Policies |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_examples_aws_access-resource-policy.html)  | 

For example, AWS Data Exchange sends requests to Amazon S3 buckets owned by the AWS Data Exchange service on behalf of the IAM principal \(user or role\) invoking the AWS Data Exchange APIs\. Therefore, the following policy example demonstrates you can exclude AWS Data Exchange from the `Deny` statement as follows:
+ The first statement, `AllowAccessToS3ResourceInSpecificAccountsAndSpecificService1`, uses a combination of the effect [Deny](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_effect.html) and the condition operator `NotAction` to explicitly deny access to every action not listed in the `NotAction` block, for Amazon S3 resources not in your account\. 
+ The second statement, `AllowAccessToS3ResourceInSpecificAccountsAndSpecificService2`, uses a combination of the `ResourceAccount` and `CalledVia` conditions to deny the three Amazon S3 actions in the previous statement to resources not in your account for calls that do not originate from AWS Data Exchange\. 

A combination of these two statements creates a policy that allows access to Amazon S3 resources only in your account and allows the three Amazon S3 actions to any bucket made by the AWS Data Exchange service on your behalf\. For more information about the logic for this statement, see [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_notaction.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_notaction.html)\. When you use the [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-calledvia%EF%BB%BF](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-calledvia%EF%BB%BF) condition key, you allow calls sent by the AWS Data Exchange service on your behalf to Amazon S3 buckets owned by the AWS Data Exchange service\.

The following example shows how you can configure the policy to allow access to the required Amazon S3 buckets\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService1",
      "Effect": "Deny",
      "Principal": { "AWS": "123456789012"
      },
      "NotAction":[
            "s3:GetObject",
            "s3:PutObject",
            "s3:PutObjectAcl"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "1234567890abcdef0"
          ]
        }
      }
     },
     {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService2",
      "Effect": "Deny",
      "Principal": { "AWS": "123456789012"
      }
      "Action":[
            "s3:GetObject",
            "s3:PutObject",
            "s3:PutObjectAcl"
      ],
       "Resource": "*",
       "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "1234567890abcdef0"
          ]
        },
        "ForAllValues:StringNotEquals":{
            "aws:CalledVia":[
               "dataexchange.amazonaws.com"
            ]
        }
      }
     }
   ]
 }
```

Similarly, CloudFormation Stack Sets send requests to Amazon SNS topics owned by the CloudFormation service on behalf of the IAM principal \(user or role\) invoking the Stack Sets APIs\. To exclude AWS CloudFormation Stack Sets APIs, modify the previous policy as follows:
+ Add `sns:*` in the `NotAction` block of the `AllowAccessToS3ResourceInSpecificAccountsAndSpecificService1` statement of the policy\. This adds all Amazon SNS actions to the list of allowed actions if the Principal does not belong to the account specified in the `ResourceAccount` condition\. 
+ Add another statement, `AllowAccessToS3ResourceInSpecificAccountsAndSpecificService2` statement to the policy\. This statement denies all Amazon SNS actions for all principals unless the calls originate from CloudFormation services on your behalf using the [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-calledvia%EF%BB%BF](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-calledvia%EF%BB%BF) condition key\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService1",
      "Effect": "Deny",
      "Principal": { "AWS":  "123456789012"
      },
      "NotAction":[
            "s3:GetObject",
            "s3:PutObject",
            "s3:PutObjectAcl",
            "sns:*"
      ],
      "Resource":
      [
        "arn:aws:s3:::*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "1234567890abcdef0"
          ]
        }
     }
    },
    {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService2",
      "Effect": "Deny",
      "Principal": { "AWS":  "123456789012"
      },
      "Action":[
            "s3:GetObject",
            "s3:PutObject",
            "s3:PutObjectAcl"
      ],
      "Resource": [
        "arn:aws:s3:::*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "1234567890abcdef0"
          ]
        },
        "ForAllValues:StringNotEquals":{
            "aws:CalledVia":[
               "dataexchange.amazonaws.com"
            ]
        }
     }
    },
    {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService3",
      "Effect": "Deny",
      "Principal": { "AWS":  "123456789012"
      },
      "Action":[
            "sns:*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "1234567890abcdef0"
          ]
        },
        "ForAllValues:StringNotEquals":{
            "aws:CalledVia":[
                  "cloudformation.amazonaws.com"
            ]
        }
     }
    }       
   ]
 }
```

As you continue to build this policy, you can add the exception for AWS Managed IAM Policies\. A service\-managed account outside of your AWS Organizations owns Managed IAM Policies\. There are four IAM actions that list and retrieve AWS\-managed policies\. Add these actions to the [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_notaction.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_notaction.html) element of the statement `AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService1` in the policy\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService1",
      "Effect": "Deny",
      "Principal": { "AWS":  "123456789012"
      },
      "NotAction":[
            "s3:GetObject",
            "s3:PutObject",
            "s3:PutObjectAcl",
            "sns:*",
            "iam:GetPolicy",
            "iam:GetPolicyVersion",
            "iam:ListEntitiesForPolicy",
            "iam:ListPolicies"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "1234567890abcdef0"
          ]
        }
     }
    },
    {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService2",
      "Effect": "Deny",
      "Principal": { "AWS":  "123456789012"
      },
      "Action":[
            "s3:GetObject",
            "s3:PutObject",
            "s3:PutObjectAcl"
      ],
      "Resource": [
        "arn:aws:s3:::*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "1234567890abcdef0"
          ]
        },
        "ForAllValues:StringNotEquals":{
            "aws:CalledVia":[
               "dataexchange.amazonaws.com"
            ]
        }
     }
    },
    {
      "Sid": "AllowAccessToS3ResourcesInSpecificAccountsAndSpecificService3",
      "Effect": "Deny",
      "Principal": { "AWS":  "123456789012"
      },
      "Action":[
            "sns:*"
      ],
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "1234567890abcdef0"
          ]
        },
        "ForAllValues:StringNotEquals":{
            "aws:CalledVia":[
                  "cloudformation.amazonaws.com"
            ]
        }
     }
    }       
   ]
 }
```

In addition to account\-level controls, you might want to restrict access based on the Organizations `ou` or the organization owner of a resource\. You can do this using the `aws:ResourceOrgId` or `aws:ResourceOrgPaths` global condition keys\. To learn more, see [AWS global condition context keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html)\.

 