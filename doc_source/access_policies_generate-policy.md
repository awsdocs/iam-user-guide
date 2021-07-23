# Generate policies based on access activity<a name="access_policies_generate-policy"></a>

As an administrator or developer, you might grant permissions to IAM entities \(users or roles\) beyond what they require\. IAM provides several options to help you refine the permissions that you grant\. One option is to generate an IAM policy that is based on access activity for an entity\. IAM Access Analyzer reviews your AWS CloudTrail logs and generates a policy template that contains the permissions that the entity used in your specified date range\. You can use the template to create a policy with fine\-grained permissions that grant only the permissions that are required to support your specific use case\. 

For example, imagine that you are a developer and your engineering team has been working on a project to create a new application\. To encourage experimentation and enable your team to move fast, you’ve configured a role with broad permissions while the application is in development\. Now the application is ready for production\. Before the application can launch in the production account, you want to identify only the permissions that the role needs for the application to function\. This helps you to adhere to the best practice of [granting least privilege](best-practices.md#grant-least-privilege)\. You can generate a policy based on the access activity of the role that you have been using for the application in the development account\. You can further refine the generated policy and then attach the policy to an entity in your production account\. 

**Topics**
+ [How policy generation works](#access_policies_generate-policy-howitworks)
+ [Service and action\-level information](#access_policies_generate-policy-service-action)
+ [Things to know about generating policies](#access_policies_generate-policy-know)
+ [Permissions required to generate a policy](#access_policies_generate-policy-perms)
+ [Generate a policy based on CloudTrail activity \(console\)](#access_policies_gen-pol-proc-console)
+ [Generate a policy based on CloudTrail activity \(AWS CLI\)](#access_policies_gen-pol-proc-cli)
+ [Generate a policy based on CloudTrail activity \(AWS API\)](#access_policies_gen-pol-proc-api)

## How policy generation works<a name="access_policies_generate-policy-howitworks"></a>

IAM Access Analyzer analyzes your CloudTrail events to identify actions and services that have been used by an IAM entity \(user or role\)\. It then generates an IAM policy that is based on that activity\. You can refine an entity's permissions when you replace a broad permissions policy attached to the entity with the generated policy\. The following is a high\-level overview of the policy generation process\.
+ **Set up for policy template generation** – You specify a time period of up to 90 days for IAM Access Analyzer to analyze your historical AWS CloudTrail events\. You must specify an existing service role or create a new one\. The service role gives IAM Access Analyzer access to your CloudTrail trail and service last accessed information to identify the services and actions that were used\. You must specify the CloudTrail trail that is logging events for the account before you can generate a policy\. For more information about IAM Access Analyzer quotas for CloudTrail data, see [IAM Access Analyzer quotas](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-getting-started.html#access-analyzer-quotas)\.
+ **Generate policy** – IAM Access Analyzer generates a policy based on the access activity in your CloudTrail events\. 
+ **Review and customize policy** – After the policy is generated, you can review the services and actions that were used by the entity during the specified date range\. You can further customize the policy by adding or removing permissions, specifying resources, and adding conditions to the policy template\.
+ **Create and attach policy** – You have the option to save the generated policy by creating a managed policy\. You can attach the policy that you create to the user or role whose activity was used to generate the policy\.

## Service and action\-level information<a name="access_policies_generate-policy-service-action"></a>

When IAM Access Analyzer generates an IAM policy, information is returned to help you to further customize the policy\. Two categories of information can be returned when a policy is generated:
+ **Policy with action\-level information –** For some AWS services, such as Amazon EC2, IAM Access Analyzer can identify the actions found in your CloudTrail events and lists the actions used in the generated policy\. For some services, we prompt you to add actions for the services to the generated policy\.

  IAM Access Analyzer generates policies with action\-level information for the following AWS services:
  + IAM Access Analyzer
  + Amazon CloudWatch
  + Amazon Cognito Identity
  + Amazon Cognito user pools
  + Amazon EC2
  + Amazon ECS
  + Elastic Load Balancing
  + IAM
  + AWS KMS
  + AWS Lambda
  + AWS RAM
  + Amazon RDS
  + AWS Resource Groups
  + Amazon S3
  + AWS Security Token Service
  + AWS Systems Manager
+ **Policy with service\-level information –** IAM Access Analyzer uses [last accessed](access_policies_access-advisor.md) information to create a policy template with all of the recently used services\. When using the AWS Management Console, we prompt you to review the services and add actions to complete the policy\.

## Things to know about generating policies<a name="access_policies_generate-policy-know"></a>

Before you generate a policy, review the following important details\.
+ **Enable a CloudTrail trail** – You must have a CloudTrail trail enabled for your account to generate a policy based on access activity\. When you create a CloudTrail trail, CloudTrail sends events related to your trail to an Amazon S3 bucket that you specify\. To learn how create a CloudTrail trail, see [Creating a trail for your AWS account](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html) in the *AWS CloudTrail User Guide*\.
+ **Trail and associated Amazon S3 bucket must be in the same account** – To generate a policy, you must specify a CloudTrail trail in the same account as the IAM entity \(user or role\) that you are using to generate the policy\. Additionally, the logs should be stored in a bucket in the same account\. For example, if you have separate development and production accounts, create a CloudTrail trail in both accounts and store the logs locally in the account\. After you test the policy in your development account, you can later copy the managed policy that you generated into your production account\.
+ **AWS Organizations** – You can't generate a policy using an Organizations CloudTrail trail\.
+ **PassRole** – The `iam:PassRole` action is not tracked by CloudTrail and is not included in generated policies\. 
+ **Reduce policy generation time** – To generate a policy faster, reduce the date range that you specify during setup for policy generation\.
+ **Use CloudTrail for auditing** – Do not use policy generation for auditing purposes; use CloudTrail instead\. For more information about using CloudTrail see, [Logging IAM and AWS STS API calls with AWS CloudTrail](cloudtrail-integration.md)\.
+ **One policy IAM console** – You can have one generated policy at a time in the IAM console\.
+ **Generated policy availability IAM console** – You can review a generated policy in the IAM console for up to 7 days after it is generated\. After 7 days, you must generate a new policy\.
+ **Policy generation quotas** – For additional information about IAM Access Analyzer policy generation quotas, see [IAM Access Analyzer quotas](reference_iam-quotas.md#reference_access-analyzer-quotas)\.

## Permissions required to generate a policy<a name="access_policies_generate-policy-perms"></a>

The permissions that you need to generate a policy for the first time differ from those that you need to generate a policy for subsequent uses\. 

**First\-time setup**  
When you generate a policy for the first time, you must choose a suitable existing [service role](id_roles_terms-and-concepts.md#iam-term-service-role) in your account or create a new service role\. The service role gives IAM Access Analyzer access to CloudTrail and service last accessed information in your account\. Only administrators should have the permissions necessary to create and configure roles\. Therefore, we recommend that an administrator creates the service role during the first\-time setup\. To learn more about the permissions required to create service roles, see [Creating a role to delegate permissions to an AWS service](id_roles_create_for-service.md)\.

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
                "s3:ListBucket",
                "s3:GetBucketLocation"
            ],
            "Resource": [
                "arn:aws:s3:::{{cloudtrail-bucket}}",
                "arn:aws:s3:::{{cloudtrail-bucket}}/*"
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
To generate policies in the AWS Management Console, an IAM user must have a permissions policy that allows them to pass the service role that is used for policy generation to IAM Access Analyzer\. `iam:PassRole` is usually accompanied by `iam:GetRole` so that the user can get the details of the role to be passed\. In this example, the user can pass only roles that exist in the specified account with names that begin with `AccessAnalyzerMonitorServiceRole*`\. To learn more about passing IAM roles to AWS services, see [Granting a user permissions to pass a role to an AWS service](id_roles_use_passrole.md)\.

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

## Generate a policy based on CloudTrail activity \(console\)<a name="access_policies_gen-pol-proc-console"></a>

You can generate a policy for an IAM user or role\.

### Step 1: Generate a policy based on CloudTrail activity<a name="access_policies_gen-pol-proc-generate"></a>

The following procedure explains how to generate a policy for a role using the AWS Management Console\. 

**Generate a policy for an IAM role**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane on the left, choose **Roles**\.
**Note**  
The steps to generate a policy based on activity for an IAM user are almost identical\. To do this, choose **Users** instead of **Roles**\.

1. In the list of roles in your account, choose the name of the role whose activity you want to use to generate a policy\.

1. On the **Permissions** tab, in the **Generate policy based on CloudTrail events** section, choose **Generate policy**\.

1. On the **Generate policy** page, specify the time period that you want IAM Access Analyzer to analyze your CloudTrail events for actions taken with the role\. You can choose a range of up to 90 days\. We recommend that you choose the shortest time period possible to reduce the policy generation time\.

1. In the **CloudTrail access** section, choose an existing service role or create a new service role\. This service role gives IAM Access Analyzer permissions to access your CloudTrail trail on your behalf to review access and identify the services and actions that have been used\.

1. In the **CloudTrail trail to be analyzed** section, specify the CloudTrail trail that logs events for the account\.

1. Choose **Generate policy**\.

1. While policy generation is in progress, you are returned to the **Roles** **Summary** page on the **Permissions** tab\. Wait until the status in the **Policy request details** section displays **Success**, and then choose **View generated policy**\. You can view the generated policy for up to 7 days\. If you generate another policy, the existing policy is replaced with the new one that you generate\.

### Step 2: Review permissions and add actions for services used<a name="access_policies_gen-pol-proc-console-review-add"></a>

Review the services and actions that IAM Access Analyzer identified that the role used\. You can add actions for any services that were used to the generated policy template\.

1. Review the following sections:
   + On the **Review permissions** page, review the list of **Actions included in the generated policy**\. The list displays the services *and* actions that IAM Access Analyzer identified were used by the role in the specified date range\.
   + The **Services used** section displays additional services that IAM Access Analyzer identified that were used by the role in the specified date range\. Information about which actions were used might not be available for the services listed in this section\. Use the menus for each service listed to manually choose the actions that you want to include in the policy\.

1. When you are done adding actions, choose **Next**\.

### Step 3: Further customize the generated policy<a name="access_policies_gen-pol-proc-console-customize"></a>

You can further customize the policy by adding or removing permissions or specifying resources\.

**To customize the generated policy**

1. Update the policy template\. The policy template contains resource ARN placeholders for actions that support resource\-level permissions, as shown in the following image\. *Resource\-level permissions* refers to the ability to specify which resources users are allowed to perform actions on\. We recommend that you use [ARNs](reference_identifiers.md#identifiers-arns) to specify your individual resources in the policy for actions that support resource\-level permissions\. You can replace the placeholder resource ARNs with valid resource ARNs for your use case\.

   If an action does not support resource\-level permissions, you must use a wildcard \(`*`\) to specify that all resources can be affected by the action\. To learn which AWS services support resource\-level permissions, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. For a list of actions in each service, and to learn which actions support resource\-level permissions, see [Actions, Resources, and Condition Keys for AWS Services](https://docs.aws.amazon.com/service-authorization/latest/reference/)\.  
![\[Resource ARN placeholder in policy template\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/res_plc_lg.png)

1. \(Optional\) Add, modify, or remove JSON policy statements in the template\. To learn more about writing JSON policies, see [Creating IAM policies \(console\)](access_policies_create-console.md)\.

1. When you are done customizing the policy template, you have the following options:
   + \(Optional\) You can copy the JSON in the template to use separately outside of the **Generated policy** page\. For example, if you want to use the JSON to create a policy in a different account\. If the policy in your template exceeds the 6,144 character limit for JSON policies, the policy is split into multiple policies\.
   + Choose **Next** to review and create a managed policy in the same account\.

### Step 4: Review and create a managed policy<a name="access_policies_gen-pol-proc-console-create"></a>

If you have permissions to create and attach IAM policies, you can create a managed policy from the policy that was generated\. You can then attach the policy to a user or role in your account\.

**To review and create a policy**

1. On the **Review and create managed policy** page, enter a **Name** and **Description** \(optional\) for the policy that you are creating\.

1. \(Optional\) In the **Summary** section, you can review the permissions that will be included in the policy\.

1. \(Optional\) Add metadata to the policy by attaching tags as key\-value pairs\. For more information about using tags in IAM, see [Tagging IAM resources](id_tags.md)\.

1. When you are finished, do one of the following:
   + You can attach the new policy directly to the role that was used to generate the policy\. To do this, near the bottom of the page, select the check box next to the **Attach policy to *YourRoleName***\. Then choose **Create and attach policy**\.
   + Otherwise, choose **Create policy**\. You can find the policy that you created in the list of policies in the **Policies** navigation pane of the IAM console\.

1. You can attach the policy that you created to an entity in your account\. After you attach the policy, you can remove any other overly broad policies that might be attached to the entity\. To learn how to attach a managed policy, see [Adding IAM identity permissions \(console\)](access_policies_manage-attach-detach.md#add-policies-console)\.

## Generate a policy based on CloudTrail activity \(AWS CLI\)<a name="access_policies_gen-pol-proc-cli"></a>

You can use the following commands to generate a policy using the AWS CLI\. 

**To generate a policy**
+ [aws accessanalyzer start\-policy\-generation](https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/start-policy-generation.html)

**To view a generated policy**
+ [aws accessanalyzer get\-generated\-policy](https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/get-generated-policy.html)

**To cancel a policy generation request**
+ [aws accessanalyzer cancel\-policy\-generation](https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/cancel-policy-generation.html)

**To view a list of policy generation requests**
+ [aws accessanalyzer list\-policy\-generations](https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/list-policy-generations.html)

## Generate a policy based on CloudTrail activity \(AWS API\)<a name="access_policies_gen-pol-proc-api"></a>

You can use the following operations to generate a policy using the AWS API\.

**To generate a policy**
+ [StartPolicyGeneration](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_StartPolicyGeneration.html)

**To view a generated policy**
+ [GetGeneratedPolicy](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_GetGeneratedPolicy.html)

**To cancel a policy generation request**
+ [CancelPolicyGeneration](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_CancelPolicyGeneration.html)

**To view a list of policy generation requests**
+ [ListPolicyGenerations](https://docs.aws.amazon.com/access-analyzer/latest/APIReference/API_ListPolicyGenerations.html)