# AWS managed policies for job functions<a name="access_policies_job-functions"></a>

We recommend using policies that [grant least privilege](best-practices.md#grant-least-privilege), or granting only the permissions required to perform a task\. The most secure way to grant least privilege is to write a custom policy with only the permissions needed by your team\. You must create a process to allow your team to request more permissions when necessary\. It takes time and expertise to [create IAM customer managed policies](access_policies_create-console.md) that provide your team with only the permissions they need\.

To get started adding permissions to your IAM identities \(users, groups of users, and roles\), you can use [AWS managed policies](access_policies_managed-vs-inline.md#aws-managed-policies)\. AWS managed policies cover common use cases and are available in your AWS account\. AWS managed policies don't grant least privilege permissions\. You must consider the security risk of granting your principals more permissions than they need to do their job\.

You can attach AWS managed policies, including job functions, to any IAM identity\. To switch to least privilege permissions, you can run AWS Identity and Access Management Access Analyzer to monitor principals with AWS managed policies\. After learning which permissions they are using, then you can write a custom policy or generate a policy with only the required permissions for your team\. This is less secure, but provides more flexibility as you learn how your team is using AWS\.

AWS managed policies for job functions are designed to closely align to common job functions in the IT industry\. You can use these policies to grant the permissions needed to carry out the tasks expected of someone in a specific job function\. These policies consolidate permissions for many services into a single policy that's easier to work with than having permissions scattered across many policies\.

**Use Roles to Combine Services**  
Some of the policies use IAM service roles to help you take advantage of features found in other AWS services\. These policies grant access to `iam:passrole`, which allows a user with the policy to pass a role to an AWS service\. This role delegates IAM permissions to the AWS service to carry out actions on your behalf\.

You must create the roles according to your needs\. For example, the Network Administrator policy allows a user with the policy to pass a role named "flow\-logs\-vpc" to the Amazon CloudWatch service\. CloudWatch uses that role to log and capture IP traffic for VPCs created by the user\.

To follow security best practices, the policies for job functions include filters that limit the names of valid roles that can be passed\. This helps avoid granting unnecessary permissions\. If your users do require the optional service roles, you must create a role that follows the naming convention specified in the policy\. You then grant permissions to the role\. Once that is done, the user can configure the service to use the role, granting it whatever permissions the role provides\.

In the following sections, each policy's name is a link to the policy details page in the AWS Management Console\. There you can see the policy document and review the permissions it grants\.

## Administrator job function<a name="jf_administrator"></a>

**AWS managed policy name:** [AdministratorAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AdministratorAccess)

**Use case:** This user has full access and can delegate permissions to every service and resource in AWS\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants all actions for all AWS services and for all resources in the account\. 

**Note**  
Before an IAM user or role can access the AWS Billing and Cost Management console with the permissions in this policy, you must first activate IAM user and role access\. To do this, follow the instructions in [Step 1 of the tutorial about delegating access to the billing console](tutorial_billing.md)\.

## Billing job function<a name="jf_accounts-payable"></a>

**AWS managed policy name:** [Billing](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/Billing)

**Use case:** This user needs to view billing information, set up payments, and authorize payments\. The user can monitor the costs accumulated for the entire AWS service\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants full permissions for managing billing, costs, payment methods, budgets, and reports\.

**Note**  
Before an IAM user or role can access the AWS Billing and Cost Management console with the permissions in this policy, you must first activate IAM user and role access\. To do this, follow the instructions in [Step 1 of the tutorial about delegating access to the billing console](tutorial_billing.md)\.

## Database administrator job function<a name="jf_database-administrator"></a>

**AWS managed policy name:** [DatabaseAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/DatabaseAdministrator)

**Use case:** This user sets up, configures, and maintains databases in the AWS Cloud\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants permissions to create, configure, and maintain databases\. It includes access to AWS database services, such as Amazon DynamoDB, Amazon Relational Database Service \(RDS\), and Amazon Redshift\. View the policy for the full list of database services that this policy supports\.

This job function policy supports the ability to pass roles to AWS services\. The policy allows the `iam:PassRole` action for only those roles named in the following table\. For more information, see [Creating roles and attaching policies \(console\)](access_policies_job-functions_create-policies.md) later in this topic\.


**Optional IAM service roles for the database administrator job function**  

| Use case | Role name \(\* is a wildcard\) | Service role type to select | Select this AWS managed policy | 
| --- | --- | --- | --- | 
| Allow the user to monitor RDS databases | [rds\-monitoring\-role](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html) | Amazon RDS Role for Enhanced Monitoring | [AmazonRDSEnhancedMonitoringRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonRDSEnhancedMonitoringRole) | 
| Allow AWS Lambda to monitor your database and access external databases | [rdbms\-lambda\-access](http://aws.amazon.com/blogs/big-data/from-sql-to-microservices-integrating-aws-lambda-with-relational-databases) | Amazon EC2 | [AWSLambda\_FullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AWSLambda_FullAccess) | 
| Allow Lambda to upload files to Amazon S3 and to Amazon Redshift clusters with DynamoDB | [lambda\_exec\_role](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader) | AWS Lambda | Create a new managed policy as defined in the [AWS Big Data Blog](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader) | 
| Allow Lambda functions to act as triggers for your DynamoDB tables | [lambda\-dynamodb\-\*](https://docs.aws.amazon.com/lambda/latest/dg/with-ddb.html) | AWS Lambda | [AWSLambdaDynamoDBExecutionRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSLambdaDynamoDBExecutionRole) | 
| Allow Lambda functions to access Amazon RDS in a VPC | [lambda\-vpc\-execution\-role](https://docs.aws.amazon.com/lambda/latest/dg/vpc-rds.html) | Create a role with a trust policy as defined in the [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/latest/dg/vpc-rds.html) | [AWSLambdaVPCAccessExecutionRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSLambdaVPCAccessExecutionRole) | 
| Allow AWS Data Pipeline to access your AWS resources | [DataPipelineDefaultRole](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | Create a role with a trust policy as defined in the [AWS Data Pipeline Developer Guide](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | The AWS Data Pipeline documentation lists the required permissions for this use case\. See [IAM roles for AWS Data Pipeline](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | 
| Allow your applications running on Amazon EC2 instances to access your AWS resources | [DataPipelineDefaultResourceRole](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | Create a role with a trust policy as defined in the [AWS Data Pipeline Developer Guide](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | [AmazonEC2RoleforDataPipelineRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonEC2RoleforDataPipelineRole) | 

## Data scientist job function<a name="jf_data-scientist"></a>

**AWS managed policy name:** [DataScientist](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/DataScientist)

**Use case:** This user runs Hadoop jobs and queries\. The user also accesses and analyzes information for data analytics and business intelligence\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants permissions to create, manage, and run queries on an Amazon EMR cluster and perform data analytics with tools such as Amazon QuickSight\. The policy includes access to additional data scientist services, such as AWS Data Pipeline, Amazon EC2, Amazon Kinesis, Amazon Machine Learning, and SageMaker\. View the policy for the full list of data scientist services that this policy supports\.

This job function policy supports the ability to pass roles to AWS services\. One statement allows passing any role to SageMaker\. Another statement allows the `iam:PassRole` action for only those roles named in the following table\. For more information, see [Creating roles and attaching policies \(console\)](access_policies_job-functions_create-policies.md) later in this topic\.


**Optional IAM service roles for the data scientist job function**  

| Use case | Role name \(\* is a wildcard\) | Service role type to select | AWS managed policy to select | 
| --- | --- | --- | --- | 
| Allow Amazon EC2 instances access to services and resources suitable for clusters | [EMR\-EC2\_DefaultRole](https://docs.aws.amazon.com/emr/latest/DeveloperGuide/emr-iam-roles-defaultroles.html) | Amazon EMR for EC2  | [AmazonElasticMapReduceforEC2Role](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonElasticMapReduceforEC2Role) | 
| Allow Amazon EMR access to access the Amazon EC2 service and resources for clusters | [EMR\_DefaultRole](https://docs.aws.amazon.com/emr/latest/DeveloperGuide/emr-iam-roles-defaultroles.html) | Amazon EMR | [AmazonEMRServicePolicy\_v2](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonEMRServicePolicy_v2) | 
| Allow Kinesis Kinesis Data Analytics to access streaming data sources | [kinesis\-\*](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader) | Create a role with a trust policy as defined in the [AWS Big Data Blog](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader)\. | See the [AWS Big Data Blog](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader), which outlines four possible options depending on your use case | 
| Allow AWS Data Pipeline to access your AWS resources | [DataPipelineDefaultRole](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | Create a role with a trust policy as defined in the [AWS Data Pipeline Developer Guide](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | The AWS Data Pipeline documentation lists the required permissions for this use case\. See [IAM roles for AWS Data Pipeline](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | 
| Allow your applications running on Amazon EC2 instances to access your AWS resources | [DataPipelineDefaultResourceRole](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | Create a role with a trust policy as defined in the [AWS Data Pipeline Developer Guide](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | [AmazonEC2RoleforDataPipelineRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonEC2RoleforDataPipelineRole) | 

## Developer power user job function<a name="jf_developer-power-user"></a>

**AWS managed policy name:** [PowerUserAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/PowerUserAccess)

**Use case:** This user performs application development tasks and can create and configure resources and services that support AWS aware application development\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** The first statement of this policy uses the [`NotAction`](reference_policies_elements_notaction.md) element to allow all actions for all AWS services and for all resources except AWS Identity and Access Management, AWS Organizations, and AWS Account Management\. The second statement grants IAM permissions to create a service\-linked role\. This is required by some services that must access resources in another service, such as an Amazon S3 bucket\. It also grants Organizations permissions to view information about the user's organization, including the management account email and organization limitations\. Although this policy limits IAM, Organizations, it allows the user to perform all IAM Identity Center actions if IAM Identity Center is enabled\. It also grants Account Management permissions to view which AWS Regions are enabled or disabled for the account\.

## Network administrator job function<a name="jf_network-administrator"></a>

**AWS managed policy name:** [NetworkAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/NetworkAdministrator)

**Use case:** This user is tasked with setting up and maintaining AWS network resources\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants permissions to create and maintain network resources in Auto Scaling, Amazon EC2, AWS Direct Connect, Route 53, Amazon CloudFront, Elastic Load Balancing, AWS Elastic Beanstalk, Amazon SNS, CloudWatch, CloudWatch Logs, Amazon S3, IAM, and Amazon Virtual Private Cloud\.

This job function requires the ability to pass roles to AWS services\. The policy grants `iam:GetRole` and `iam:PassRole` for only those roles named in the following table\. For more information, see [Creating roles and attaching policies \(console\)](access_policies_job-functions_create-policies.md) later in this topic\.


**Optional IAM service roles for the network administrator job function**  

| Use case | Role name \(\* is a wildcard\) | Service role type to select | AWS managed policy to select | 
| --- | --- | --- | --- | 
| Allows Amazon VPC to create and manage logs in CloudWatch Logs on the user's behalf to monitor IP traffic going in and out of your VPC | [flow\-logs\-\*](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html#flow-logs-iam) | Create a role with a trust policy as defined in the [Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html#flow-logs-iam) | This use case does not have an existing AWS managed policy, but the documentation lists the required permissions\. See [Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html#flow-logs-iam)\. | 

## Read\-only access<a name="awsmp_readonlyaccess"></a>

**AWS managed policy name:** [ReadOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/ReadOnlyAccess)

**Use case:** This user requires read\-only access to every resource in an AWS account\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants permissions to list, get, describe, and otherwise view resources and their attributes\. It does not include mutating functions like create or delete\. This policy does include read\-only access to security\-related AWS services, such as AWS Identity and Access Management and AWS Billing and Cost Management\. View the policy for the full list of services and actions that this policy supports\.

## Security auditor job function<a name="jf_security-auditor"></a>

**AWS managed policy name:** [SecurityAudit](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/SecurityAudit)

**Use case:** This user monitors accounts for compliance with security requirements\. This user can access logs and events to investigate potential security breaches or potential malicious activity\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants permissions to view configuration data for many AWS services and to review their logs\. 

## Support user job function<a name="jf_support-user"></a>

**AWS managed policy name:** [SupportUser](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/SupportUser)

**Use case:** This user contacts AWS Support, creates support cases, and views the status of existing cases\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants permissions to create and update AWS Support cases\.

## System administrator job function<a name="jf_system-administrator"></a>

**AWS managed policy name:** [SystemAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/SystemAdministrator)

**Use case:** This user sets up and maintains resources for development operations\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants permissions to create and maintain resources across a large variety of AWS services, including AWS CloudTrail, Amazon CloudWatch, AWS CodeCommit, AWS CodeDeploy, AWS Config, AWS Directory Service, Amazon EC2, AWS Identity and Access Management, AWS Key Management Service, AWS Lambda, Amazon RDS, Route 53, Amazon S3, Amazon SES, Amazon SQS, AWS Trusted Advisor, and Amazon VPC\.

This job function requires the ability to pass roles to AWS services\. The policy grants `iam:GetRole` and `iam:PassRole` for only those roles named in the following table\. For more information, see [Creating roles and attaching policies \(console\)](access_policies_job-functions_create-policies.md) later in this topic\.


**Optional IAM service roles for the system administrator job function**  

| Use case | Role name \(\* is a wildcard\) | Service role type to select | AWS managed policy to select | 
| --- | --- | --- | --- | 
| Allow apps running in EC2 instances in an Amazon ECS cluster to access Amazon ECS | [ecr\-sysadmin\-\*](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/instance_IAM_role.html) | Amazon EC2 Role for EC2 Container Service  | [AmazonEC2ContainerServiceforEC2Role](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonEC2ContainerServiceforEC2Role) | 
| Allow a user to monitor databases | [rds\-monitoring\-role](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html) | Amazon RDS Role for Enhanced Monitoring | [AmazonRDSEnhancedMonitoringRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonRDSEnhancedMonitoringRole) | 
| Allow apps running in EC2 instances to access AWS resources\. | [ec2\-sysadmin\-\*](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) | Amazon EC2 | Sample policy for role that grants access to an S3 bucket as shown in the [Amazon EC2 User Guide for Linux Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html); customize as needed | 
| Allow Lambda to read DynamoDB streams and write to CloudWatch Logs | [lambda\-sysadmin\-\*](https://docs.aws.amazon.com/lambda/latest/dg/with-ddb.html) | AWS Lambda | [AWSLambdaDynamoDBExecutionRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSLambdaDynamoDBExecutionRole) | 

## View\-only user job function<a name="jf_view-only-user"></a>

**AWS managed policy name:** [ViewOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/ViewOnlyAccess)

**Use case:** This user can view a list of AWS resources and basic metadata in the account across all services\. The user cannot read resource content or metadata that goes beyond the quota and list information for resources\.

**Policy updates:** AWS maintains and updates this policy\. For a history of changes for this policy, view the policy in the IAM console and then choose the **Policy versions** tab\. For more information about job function policy updates, see [Updates to AWS managed policies for job functions](#security-iam-awsmanpol-jobfunction-updates)\.

**Policy description:** This policy grants `List*`, `Describe*`, `Get*`, `View*`, and `Lookup*` access to resources for most AWS services\. To see what actions this policy includes for each service, see [ViewOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/ViewOnlyAccess)\.

## Updates to AWS managed policies for job functions<a name="security-iam-awsmanpol-jobfunction-updates"></a>

These policies are all maintained by AWS and are kept up to date to include support for new services and new capabilities as they are added by AWS services\. These policies cannot be modified by customers\. You can make a copy of the policy and then modify the copy, but that copy is not automatically updated as AWS introduces new services and API operations\.

For a job function policy, you can view the version history and the time and date of each update in the IAM console\. To do this, use the links on this page to view the policy details\. Then choose the **Policy versions** tab to view the versions\. This page shows the last 25 versions of a policy\. To view all of the versions for a policy, call the [get\-policy\-version](https://docs.aws.amazon.com/cli/latest/reference/iam/get-policy-version.html) AWS CLI command or the [GetPolicyVersion](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetPolicyVersion.html) API operation\.

**Note**  
You can have up to five versions of a customer managed policy, but AWS retains the full version history of AWS managed policies\.