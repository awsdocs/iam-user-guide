# IAM Access Analyzer policy generation<a name="access-analyzer-policy-generation"></a>

As an administrator or developer, you might grant permissions to IAM entities \(users or roles\) beyond what they require\. IAM provides several options to help you refine the permissions that you grant\. One option is to generate an IAM policy that is based on access activity for an entity\. IAM Access Analyzer reviews your AWS CloudTrail logs and generates a policy template that contains the permissions that the entity used in your specified date range\. You can use the template to create a policy with fine\-grained permissions that grant only the permissions that are required to support your specific use case\. 

**Topics**
+ [How policy generation works](#access-analyzer-policy-generation-howitworks)
+ [Service and action\-level information](#access-analyzer-policy-generation-service-action)
+ [Things to know about generating policies](#access-analyzer-policy-generation-know)
+ [Permissions required to generate a policy](#access-analyzer-policy-generation-perms)
+ [Generate a policy based on CloudTrail activity \(console\)](#access-analyzer-policy-generation-console)
+ [Generate a policy using AWS CloudTrail data in another account](#access-analyzer-policy-generation-cross-account)
+ [Generate a policy based on CloudTrail activity \(AWS CLI\)](#access-analyzer-policy-generation-cli)
+ [Generate a policy based on CloudTrail activity \(AWS API\)](#access-analyzer-policy-generation-api)

## How policy generation works<a name="access-analyzer-policy-generation-howitworks"></a>

IAM Access Analyzer analyzes your CloudTrail events to identify actions and services that have been used by an IAM entity \(user or role\)\. It then generates an IAM policy that is based on that activity\. You can refine an entity's permissions when you replace a broad permissions policy attached to the entity with the generated policy\. The following is a high\-level overview of the policy generation process\.
+ **Set up for policy template generation** – You specify a time period of up to 90 days for IAM Access Analyzer to analyze your historical AWS CloudTrail events\. You must specify an existing service role or create a new one\. The service role gives IAM Access Analyzer access to your CloudTrail trail and service last accessed information to identify the services and actions that were used\. You must specify the CloudTrail trail that is logging events for the account before you can generate a policy\. For more information about IAM Access Analyzer quotas for CloudTrail data, see [IAM Access Analyzer quotas](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-getting-started.html#access-analyzer-quotas)\.
+ **Generate policy** – IAM Access Analyzer generates a policy based on the access activity in your CloudTrail events\. 
+ **Review and customize policy** – After the policy is generated, you can review the services and actions that were used by the entity during the specified date range\. You can further customize the policy by adding or removing permissions, specifying resources, and adding conditions to the policy template\.
+ **Create and attach policy** – You have the option to save the generated policy by creating a managed policy\. You can attach the policy that you create to the user or role whose activity was used to generate the policy\.

## Service and action\-level information<a name="access-analyzer-policy-generation-service-action"></a>

When IAM Access Analyzer generates an IAM policy, information is returned to help you to further customize the policy\. Two categories of information can be returned when a policy is generated:
+ **Policy with action\-level information –** For some AWS services, such as Amazon EC2, IAM Access Analyzer can identify the actions found in your CloudTrail events and lists the actions used in the generated policy\. For some services, we prompt you to add actions for the services to the generated policy\.
+ **Policy with service\-level information –** IAM Access Analyzer uses [last accessed](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_access-advisor.html) information to create a policy template with all of the recently used services\. When using the AWS Management Console, we prompt you to review the services and add actions to complete the policy\.

IAM Access Analyzer generates policies with action\-level information for the following AWS services\. For a list of actions in each service, see [Actions, Resources, and Condition Keys for AWS Services](https://docs.aws.amazon.com/service-authorization/latest/reference/reference_policies_actions-resources-contextkeys.html) in the Service Authorization Reference\.

### Supported services for action\-level information<a name="services-action-level"></a>
+ IAM Access Analyzer
+ AWS Amplify
+ Amazon AppIntegrations
+ Amazon AppFlow
+ AWS Application Cost Profiler
+ Amazon Athena
+ AWS Batch
+ Amazon Braket
+ AWS CloudTrail
+ Amazon CloudWatch
+ Amazon CloudWatch Logs
+ Amazon CloudWatch Synthetics
+ Amazon CodeGuru Profiler
+ Amazon Cognito Identity
+ Amazon Cognito Sync
+ Amazon Cognito user pools
+ AWS Cost and Usage Report
+ Amazon DevOps Guru
+ Device Advisor
+ AWS Directory Service
+ Amazon Elastic Block Store
+ Amazon EC2
+ Amazon Elastic Container Registry
+ Amazon ECS
+ Elastic Load Balancing
+ Amazon EventBridge Schemas
+ Fleet Hub for AWS IoT Device Management
+ AWS Ground Station
+ Amazon GuardDuty
+ IAM
+ Amazon Interactive Video Service
+ AWS KMS
+ Amazon Kinesis Data Firehose
+ AWS Lambda
+ Amazon MQ
+ Amazon Managed Blockchain
+ Amazon Managed Streaming for Apache Kafka
+ AWS Marketplace
+ Amazon Nimble Studio
+ AWS OpsWorks
+ AWS Outposts
+ AWS Performance Insights
+ Amazon RDS
+ AWS RAM
+ AWS Resource Groups
+ Resource Groups Tagging API
+ Savings Plans
+ AWS Secrets Manager
+ AWS Security Hub
+ AWS Security Token Service
+ AWS Server Migration Service
+ Service Quotas
+ AWS Signer
+ Amazon Simple Email Service
+ Amazon Simple Storage Service
+ AWS Systems Manager
+ Amazon Textract
+ Amazon Translate
+ AWS Well\-Architected Tool
+ Amazon WorkLink

## Things to know about generating policies<a name="access-analyzer-policy-generation-know"></a>

Before you generate a policy, review the following important details\.
+ **Enable a CloudTrail trail** – You must have a CloudTrail trail enabled for your account to generate a policy based on access activity\. When you create a CloudTrail trail, CloudTrail sends events related to your trail to an Amazon S3 bucket that you specify\. To learn how to create a CloudTrail trail, see [Creating a trail for your AWS account](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html) in the *AWS CloudTrail User Guide*\.
+ **Data events not available** – IAM Access Analyzer does not identify action\-level activity for data events, such as Amazon S3 data events, in generated policies\.
+ **PassRole** – The `iam:PassRole` action is not tracked by CloudTrail and is not included in generated policies\.
+ **Reduce policy generation time** – To generate a policy faster, reduce the date range that you specify during setup for policy generation\.
+ **Use CloudTrail for auditing** – Do not use policy generation for auditing purposes; use CloudTrail instead\. For more information about using CloudTrail see, [Logging IAM and AWS STS API calls with AWS CloudTrail](https://docs.aws.amazon.com/IAM/latest/UserGuide/cloudtrail-integration.html)\.
+ **One policy IAM console** – You can have one generated policy at a time in the IAM console\.
+ **Generated policy availability IAM console** – You can review a generated policy in the IAM console for up to 7 days after it is generated\. After 7 days, you must generate a new policy\.
+ **Policy generation quotas** – For additional information about IAM Access Analyzer policy generation quotas, see [IAM Access Analyzer quotas](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-getting-started.html#access-analyzer-quotas)\.
+ **Amazon S3 standard rates apply** – When you use the policy generation feature, IAM Access Analyzer reviews CloudTrail logs in your S3 bucket\. There are no additional storage charges to access your CloudTrail logs for policy generation\. AWS charges standard Amazon S3 rates for requests and data transfer of CloudTrail logs stored in your S3 bucket\.

## Permissions required to generate a policy<a name="access-analyzer-policy-generation-perms"></a>

The permissions that you need to generate a policy for the first time differ from those that you need to generate a policy for subsequent uses\.

**First\-time setup**  
When you generate a policy for the first time, you must choose a suitable existing [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) in your account or create a new service role\. The service role gives IAM Access Analyzer access to CloudTrail and service last accessed information in your account\. Only administrators should have the permissions necessary to create and configure roles\. Therefore, we recommend that an administrator creates the service role during the first\-time setup\. To learn more about the permissions required to create service roles, see [Creating a role to delegate permissions to an AWS service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html)\.

### Permissions required for service role<a name="collapsible-section-1"></a>

When you create a service role, you configure two policies for the role\. You attach an IAM *permissions policy* to the role that specifies what the role can do\. You also attach a *role trust policy* to the role that specifies the principal who can use the role\.

The first example policy shows the permissions policy for the service role that is required to generate a policy\. The second example policy shows the role trust policy that is required for the service role\. You can use these policies to help you create a service role when you use the AWS API or AWS CLI to generate a policy\. When you use the IAM console to create a service role as part of the policy generation process, we generate these policies for you\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "cloudtrail:GetTrail",
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "iam:GenerateServiceLastAccessedDetails",
                "iam:GetServiceLastAccessedDetails"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::DOC-EXAMPLE-BUCKET",
                "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*"
            ]
        }
    ]
}
```

The following example policy shows the role trust policy with the permissions that allows IAM Access Analyzer to assume the role\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "access-analyzer.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

**Subsequent uses**  
To generate policies in the AWS Management Console, an IAM user must have a permissions policy that allows them to pass the service role that is used for policy generation to IAM Access Analyzer\. `iam:PassRole` is usually accompanied by `iam:GetRole` so that the user can get the details of the role to be passed\. In this example, the user can pass only roles that exist in the specified account with names that begin with `AccessAnalyzerMonitorServiceRole*`\. To learn more about passing IAM roles to AWS services, see [Granting a user permissions to pass a role to an AWS service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_passrole.html)\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowUserToPassRole",
      "Effect": "Allow",
      "Action": [
        "iam:GetRole",
        "iam:PassRole"
      ],
      "Resource": "arn:aws:iam::123456789012:role/service-role/AccessAnalyzerMonitorServiceRole*"
    }
  ]
}
```

You must also have the following IAM Access Analyzer permissions to generate policies in the AWS Management Console, AWS API, or AWS CLI as shown in the following policy statement\.

```
{
      "Sid": "AllowUserToGeneratePolicy",
      "Effect": "Allow",
      "Action": [
        "access-analyzer:ListPolicyGenerations",
        "access-analyzer:StartPolicyGeneration",
        "access-analyzer:GetGeneratedPolicy",
        "access-analyzer:CancelPolicyGeneration"
      ],
      "Resource": "*"
    }
  ]
}
```

**For both first\-time and subsequent uses**  
When you use the AWS Management Console to generate a policy, you must have `cloudtrail:ListTrails` permission to list the CloudTrail trails in your account as shown in the following policy statement\.

```
    {
      "Sid": "AllowUserToListTrails",
      "Effect": "Allow",
      "Action": [
        "CloudTrail:ListTrails"
      ],
      "Resource": "*"
    }
```

## Generate a policy based on CloudTrail activity \(console\)<a name="access-analyzer-policy-generation-console"></a>

You can generate a policy for an IAM user or role\.

### Step 1: Generate a policy based on CloudTrail activity<a name="access-analyzer-policy-generation-generate"></a>

The following procedure explains how to generate a policy for a role using the AWS Management Console\. 

**Generate a policy for an IAM role**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane on the left, choose **Roles**\.
**Note**  
The steps to generate a policy based on activity for an IAM user are almost identical\. To do this, choose **Users** instead of **Roles**\.

1. In the list of roles in your account, choose the name of the role whose activity you want to use to generate a policy\.

1. On the **Permissions** tab, in the **Generate policy based on CloudTrail events** section, choose **Generate policy**\.

1. On the **Generate policy** page, specify the time period that you want IAM Access Analyzer to analyze your CloudTrail events for actions taken with the role\. You can choose a range of up to 90 days\. We recommend that you choose the shortest time period possible to reduce the policy generation time\.

1. In the **CloudTrail access** section, choose a suitable existing role or create a new role if a suitable role does not exist\. The role gives IAM Access Analyzer permissions to access your CloudTrail data on your behalf to review access activity to identify the services and actions that have been used\. To learn more about the permissions required for this role, see [Permissions required to generate a policy](#access-analyzer-policy-generation-perms)\.

1. In the **CloudTrail trail to be analyzed** section, specify the CloudTrail trail that logs events for the account\.

   If you choose a CloudTrail trail that stores logs in a different account, an information box about cross\-account access is displayed\. Cross\-account access requires additional set up\. To learn more, see [Choose a role for cross-account access](#chooserole) later in this topic\.

1. Choose **Generate policy**\.

1. While policy generation is in progress, you are returned to the **Roles** **Summary** page on the **Permissions** tab\. Wait until the status in the **Policy request details** section displays **Success**, and then choose **View generated policy**\. You can view the generated policy for up to seven days\. If you generate another policy, the existing policy is replaced with the new one that you generate\.

### Step 2: Review permissions and add actions for services used<a name="access-analyzer-policy-generation-console-review"></a>

Review the services and actions that IAM Access Analyzer identified that the role used\. You can add actions for any services that were used to the generated policy template\.

1. Review the following sections:
   + On the **Review permissions** page, review the list of **Actions included in the generated policy**\. The list displays the services *and* actions that IAM Access Analyzer identified were used by the role in the specified date range\.
   + The **Services used** section displays additional services that IAM Access Analyzer identified that were used by the role in the specified date range\. Information about which actions were used might not be available for the services listed in this section\. Use the menus for each service listed to manually choose the actions that you want to include in the policy\.

1. When you are done adding actions, choose **Next**\.

### Step 3: Further customize the generated policy<a name="access-analyzer-policy-generation-customize"></a>

You can further customize the policy by adding or removing permissions or specifying resources\.

**To customize the generated policy**

1. Update the policy template\. The policy template contains resource ARN placeholders for actions that support resource\-level permissions, as shown in the following image\. *Resource\-level permissions* refers to the ability to specify which resources users are allowed to perform actions on\. We recommend that you use [ARNs](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html#identifiers-arns) to specify your individual resources in the policy for actions that support resource\-level permissions\. You can replace the placeholder resource ARNs with valid resource ARNs for your use case\.

   If an action does not support resource\-level permissions, you must use a wildcard \(`*`\) to specify that all resources can be affected by the action\. To learn which AWS services support resource\-level permissions, see [AWS services that work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)\. For a list of actions in each service, and to learn which actions support resource\-level permissions, see [Actions, Resources, and Condition Keys for AWS Services](https://docs.aws.amazon.com/service-authorization/latest/reference/reference_policies_actions-resources-contextkeys.html)\.  
![\[Resource ARN placeholder in policy template\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/res_plc_lg.png)

1. \(Optional\) Add, modify, or remove JSON policy statements in the template\. To learn more about writing JSON policies, see [Creating IAM policies \(console\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html)\.

1. When you are done customizing the policy template, you have the following options:
   + \(Optional\) You can copy the JSON in the template to use separately outside of the **Generated policy** page\. For example, if you want to use the JSON to create a policy in a different account\. If the policy in your template exceeds the 6,144 character limit for JSON policies, the policy is split into multiple policies\.
   + Choose **Next** to review and create a managed policy in the same account\.

### Step 4: Review and create a managed policy<a name="access-analyzer-policy-generation-console-create"></a>

If you have permissions to create and attach IAM policies, you can create a managed policy from the policy that was generated\. You can then attach the policy to a user or role in your account\.

**To review and create a policy**

1. On the **Review and create managed policy** page, enter a **Name** and **Description** \(optional\) for the policy that you are creating\.

1. \(Optional\) In the **Summary** section, you can review the permissions that will be included in the policy\.

1. \(Optional\) Add metadata to the policy by attaching tags as key\-value pairs\. For more information about using tags in IAM, see [Tagging IAM resources](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html)\.

1. When you are finished, do one of the following:
   + You can attach the new policy directly to the role that was used to generate the policy\. To do this, near the bottom of the page, select the check box next to the **Attach policy to *YourRoleName***\. Then choose **Create and attach policy**\.
   + Otherwise, choose **Create policy**\. You can find the policy that you created in the list of policies in the **Policies** navigation pane of the IAM console\.

1. You can attach the policy that you created to an entity in your account\. After you attach the policy, you can remove any other overly broad policies that might be attached to the entity\. To learn how to attach a managed policy, see [Adding IAM identity permissions \(console\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html#add-policies-console)\.

## Generate a policy using AWS CloudTrail data in another account<a name="access-analyzer-policy-generation-cross-account"></a>

You might create CloudTrail trails that store data in central accounts to streamline governing activities\. For example, you can use AWS Organizations to create a trail that logs all events for all of the AWS accounts in that organization\. The trail belongs to a central account\. If you want to generate a policy for a user or role in an account that is different from the account where your CloudTrail log data is stored, you must grant cross\-account access\. To do this, you need both a role and a bucket policy that grant IAM Access Analyzer permissions to your CloudTrail logs\. For more information about creating Organizations trails, see [Creating a trail for an organization](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/creating-trail-organization.html)\.

In this example, assume that you want to generate a policy for a user or role in account A\. The CloudTrail trail in account A stores CloudTrail logs in a bucket in account B\. Before you can generate a policy, you must make the following updates:

1. Choose an existing role, or create a new service role that grants IAM Access Analyzer access to the bucket in account B \(where your CloudTrail logs are stored\)\.

1. Verify your Amazon S3 bucket object ownership and bucket permissions policy in account B so that IAM Access Analyzer can access objects in the bucket\.

**Step 1: Choose or create a role for cross\-account access**
+ On the **Generate policy** screen, the option to **Use an existing role** is pre\-selected for you if a role with the required permissions exists in your account\. Otherwise, choose **Create and use a new service role**\. The new role is used to grant IAM Access Analyzer access to your CloudTrail logs in account B\.

**Step 2: Verify or update your Amazon S3 bucket configuration in account B**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In the **Buckets** list, choose the name of the bucket where your CloudTrail trail logs are stored\.

1. Choose the **Permissions** tab and go to the **Object Ownership** section\.

   Use Amazon S3 Object Ownership bucket settings to control ownership of objects that you upload to your buckets\. By default, when other AWS accounts upload objects to your bucket, the uploading account owns the objects\. To generate a policy, the bucket owner must own all of the objects in the bucket\. Depending on your ACL use case, you might need to change the **Object Ownership** setting for your bucket\. Set **Object Ownership** to one of the following options\.
   + **Bucket owner enforced** \(recommended\)
   + **Bucket owner preferred**
**Important**  
To successfully generate a policy, the objects in the bucket must be owned by the bucket owner\. If you choose to use **Bucket owner preferred**, you can only generate a policy for the time period after the object ownership change was made\.

   To learn more about object ownership in Amazon S3, see [Controlling ownership of objects and disabling ACLs for your bucket](https://docs.aws.amazon.com/AmazonS3/latest/userguide/about-object-ownership.html) in the *Amazon S3 User Guide*\.

1. Add permissions to your Amazon S3 bucket policy in account B to allow access for the role in account A\.

   The following example policy allows `ListBucket` and `GetObject` for the bucket named `DOC-EXAMPLE-BUCKET`\. It allows access if the role accessing the bucket belongs to an account in your organization and has a name that starts with `AccessAnalyzerMonitorServiceRole`\. Using [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-principalarn](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-principalarn) as a `Condition` in the `Resource` element ensures that the role can only access activity for the account if it belongs to account A\. You can replace `DOC-EXAMPLE-BUCKET` with your bucket name and `organization-id` with your organization ID\.

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PolicyGenerationBucketPolicy",
         "Effect": "Allow",
         "Principal": {
           "AWS": "*"
         },
         "Action": [
           "s3:GetObject",
           "s3:ListBucket"
         ],
         "Resource": [
           "arn:aws:s3:::DOC-EXAMPLE-BUCKET",
           "arn:aws:s3:::DOC-EXAMPLE-BUCKET/organization-id/AWSLogs/${aws:PrincipalAccount}/*"
         ],
         "Condition": {
           "StringEquals": {
             "aws:PrincipalOrgID": "organization-id"
           },
           "StringLike": {
             "aws:PrincipalArn": "arn:aws:iam::${aws:PrincipalAccount}:role/service-role/AccessAnalyzerMonitorServiceRole*"
           }
         }
       }
     ]
   }
   ```

1. If you encrypt your logs using AWS KMS, update your AWS KMS key policy to grant IAM Access Analyzer access to use your key, as shown in the following policy example\. Replace `CROSS_ACCOUNT_ORG_TRAIL_FULL_ARN` with the ARN for your trail and `organization-id` with your organization ID\.

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Principal": {
           "AWS": "*"
         },
         "Action": "kms:Decrypt",
         "Resource": "*",
         "Condition": {
           "StringEquals": {
             "kms:EncryptionContext:aws:cloudtrail:arn": "CROSS_ACCOUNT_ORG_TRAIL_FULL_ARN",
             "aws:PrincipalOrgID": "organization-id"
           },
           "StringLike": {
             "kms:ViaService": "s3.*.amazonaws.com",
             "aws:PrincipalArn": "arn:aws:iam::${aws:PrincipalAccount}:role/service-role/AccessAnalyzerMonitorServiceRole*"
           }
         }
       }
     ]
   }
   ```

## Generate a policy based on CloudTrail activity \(AWS CLI\)<a name="access-analyzer-policy-generation-cli"></a>

You can use the following commands to generate a policy using the AWS CLI\. 

**To generate a policy**
+ [aws accessanalyzer start\-policy\-generation](https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/start-policy-generation.html)

**To view a generated policy**
+ [aws accessanalyzer get\-generated\-policy](https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/get-generated-policy.html)

**To cancel a policy generation request**
+ [aws accessanalyzer cancel\-policy\-generation](https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/cancel-policy-generation.html)

**To view a list of policy generation requests**
+ [aws accessanalyzer list\-policy\-generations](https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/list-policy-generations.html)

## Generate a policy based on CloudTrail activity \(AWS API\)<a name="access-analyzer-policy-generation-api"></a>

You can use the following operations to generate a policy using the AWS API\.

**To generate a policy**
+ [StartPolicyGeneration](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_StartPolicyGeneration.html)

**To view a generated policy**
+ [GetGeneratedPolicy](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_GetGeneratedPolicy.html)

**To cancel a policy generation request**
+ [CancelPolicyGeneration](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_CancelPolicyGeneration.html)

**To view a list of policy generation requests**
+ [ListPolicyGenerations](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_ListPolicyGenerations.html)