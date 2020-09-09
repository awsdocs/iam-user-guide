# AWS managed policies for job functions<a name="access_policies_job-functions"></a>

AWS managed policies for job functions are designed to closely align to common job functions in the IT industry\. You can use these policies to easily grant the permissions needed to carry out the tasks expected of someone in a specific job function\. These policies consolidate permissions for many services into a single policy that's easier to work with than having permissions scattered across many policies\.

You can attach these policies for job functions to any group, user, or role\. 

**Use Roles to Combine Services**  
Some of the policies use IAM service roles to help you take advantage of features found in other AWS services\. These policies grant access to `iam:passrole`, which allows a user with the policy to pass a role to an AWS service\. This role delegates IAM permissions to the AWS service to carry out actions on your behalf\.

You must create the roles according to your needs\. For example, the Network Administrator policy allows a user with the policy to pass a role named "flow\-logs\-vpc" to the Amazon CloudWatch service\. CloudWatch uses that role to log and capture IP traffic for VPCs created by the user\.

To follow security best practices, the policies for job functions include filters that limit the names of valid roles that can be passed\. This helps avoid granting unnecessary permissions\. If your users do require the optional service roles, you must create a role that follows the naming convention specified in the policy\. You then grant permissions to the role\. Once that is done, the user can configure the service to use the role, granting it whatever permissions the role provides\.

**Keep Up to Date**  
These policies are all maintained by AWS and are kept up to date to include support for new services and new capabilities as they are added by AWS\. These policies cannot be modified by customers\. You can make a copy of the policy and then modify the copy, but that copy is not automatically updated as AWS introduces new services and API operations\.

## Job functions<a name="jf_names"></a>

**Topics**
+ [Administrator](#jf_administrator)
+ [Billing](#jf_accounts-payable)
+ [Database administrator](#jf_database-administrator)
+ [Data scientist](#jf_data-scientist)
+ [Developer power user](#jf_developer-power-user)
+ [Network administrator](#jf_network-administrator)
+ [Security auditor](#jf_security-auditor)
+ [Support user](#jf_support-user)
+ [System administrator](#jf_system-administrator)
+ [View\-only user](#jf_view-only-user)

In the following sections, each policy's name is a link to the policy details page in the AWS Management Console\. There you can see the policy document and review the permissions it grants\.

### Administrator<a name="jf_administrator"></a>

**AWS managed policy name:** [AdministratorAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AdministratorAccess)

**Use case:** This user has full access and can delegate permissions to every service and resource in AWS\.

**Policy description:** This policy grants all actions for all AWS services and for all resources in the account\. 

**Note**  
Before an IAM user or role can access the AWS Billing and Cost Management console with the permissions in this policy, you must first activate IAM user and role access\. To do this, follow the instructions in [Step 1 of the tutorial about delegating access to the billing console](tutorial_billing.md)\.

### Billing<a name="jf_accounts-payable"></a>

**AWS managed policy name:** [Billing](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/Billing)

**Use case:** This user needs to view billing information, set up payments, and authorize payments\. The user can monitor the costs accumulated for the entire AWS service\.

**Policy description:** This policy grants full permissions for managing billing, costs, payment methods, budgets, and reports\.

**Note**  
Before an IAM user or role can access the AWS Billing and Cost Management console with the permissions in this policy, you must first activate IAM user and role access\. To do this, follow the instructions in [Step 1 of the tutorial about delegating access to the billing console](tutorial_billing.md)\.

### Database administrator<a name="jf_database-administrator"></a>

**AWS managed policy name:** [DatabaseAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/DatabaseAdministrator)

**Use case:** This user sets up, configures, and maintains databases in the AWS Cloud\.

**Policy description:** This policy grants permissions to create, configure, and maintain databases\. It includes access to AWS database services, such as Amazon DynamoDB, Amazon Relational Database Service \(RDS\), and Amazon Redshift\. View the policy for the full list of database services that this policy supports\.

This job function policy supports the ability to pass roles to AWS services\. The policy allows the `iam:PassRole` action for only those roles named in the following table\. For more information, see [Creating roles and attaching policies \(console\)](#access_policies_job-functions_create-policies) later in this topic\.


**Optional IAM service roles for the database administrator job function**  

| Use case | Role name \(\* is a wildcard\) | Service role type to select | Select this AWS managed policy | 
| --- | --- | --- | --- | 
| Allow the user to monitor RDS databases | [rds\-monitoring\-role](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html) | Amazon RDS Role for Enhanced Monitoring | [AmazonRDSEnhancedMonitoringRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonRDSEnhancedMonitoringRole) | 
| Allow AWS Lambda to monitor your database and access external databases | [rdbms\-lambda\-access](http://aws.amazon.com/blogs/big-data/from-sql-to-microservices-integrating-aws-lambda-with-relational-databases) | Amazon EC2 | [AWSLambdaFullAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/AWSLambdaFullAccess) | 
| Allow Lambda to upload files to Amazon S3 and to Amazon Redshift clusters with DynamoDB | [lambda\_exec\_role](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader) | AWS Lambda | Create a new managed policy as defined in the [AWS Big Data Blog](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader) | 
| Allow Lambda functions to act as triggers for your DynamoDB tables | [lambda\-dynamodb\-\*](https://docs.aws.amazon.com/lambda/latest/dg/with-ddb.html) | AWS Lambda | [AWSLambdaDynamoDBExecutionRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSLambdaDynamoDBExecutionRole) | 
| Allow Lambda functions to access Amazon RDS in a VPC | [lambda\-vpc\-execution\-role](https://docs.aws.amazon.com/lambda/latest/dg/vpc-rds.html) | Create a role with a trust policy as defined in the [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/latest/dg/vpc-rds.html) | [AWSLambdaVPCAccessExecutionRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSLambdaVPCAccessExecutionRole) | 
| Allow AWS Data Pipeline to access your AWS resources | [DataPipelineDefaultRole](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | Create a role with a trust policy as defined in the [AWS Data Pipeline Developer Guide](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | [AWSDataPipelineRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSDataPipelineRole) | 
| Allow your applications running on Amazon EC2 instances to access your AWS resources | [DataPipelineDefaultResourceRole](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | Create a role with a trust policy as defined in the [AWS Data Pipeline Developer Guide](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | [AmazonEC2RoleforDataPipelineRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonEC2RoleforDataPipelineRole) | 

### Data scientist<a name="jf_data-scientist"></a>

**AWS managed policy name:** [DataScientist](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/DataScientist)

**Use case:** This user runs Hadoop jobs and queries\. The user also accesses and analyzes information for data analytics and business intelligence\.

**Policy description:** This policy grants permissions to create, manage, and run queries on an Amazon EMR cluster and perform data analytics with tools such as Amazon QuickSight\. The policy includes access to additional data scientist services, such as AWS Data Pipeline, Amazon EC2, Amazon Kinesis, Amazon Machine Learning, and SageMaker\. View the policy for the full list of data scientist services that this policy supports\.

This job function policy supports the ability to pass roles to AWS services\. One statement allows passing any role to SageMaker\. Another statement allows the `iam:PassRole` action for only those roles named in the following table\. For more information, see [Creating roles and attaching policies \(console\)](#access_policies_job-functions_create-policies) later in this topic\.


**Optional IAM service roles for the data scientist job function**  

| Use case | Role name \(\* is a wildcard\) | Service role type to select | AWS managed policy to select | 
| --- | --- | --- | --- | 
| Allow Amazon EC2 instances access to services and resources suitable for clusters | [EMR\-EC2\_DefaultRole](https://docs.aws.amazon.com/emr/latest/DeveloperGuide/emr-iam-roles-defaultroles.html) | Amazon EMR for EC2  | [AmazonElasticMapReduceforEC2Role](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonElasticMapReduceforEC2Role) | 
| Allow Amazon EMR access to access the Amazon EC2 service and resources for clusters | [EMR\_DefaultRole](https://docs.aws.amazon.com/emr/latest/DeveloperGuide/emr-iam-roles-defaultroles.html) | Amazon EMR | [AmazonElasticMapReduceRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonElasticMapReduceRole) | 
| Allow Kinesis Kinesis Data Analytics to access streaming data sources | [kinesis\-\*](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader) | Create a role with a trust policy as defined in the [AWS Big Data Blog](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader)\. | See the [AWS Big Data Blog](http://aws.amazon.com/blogs/big-data/a-zero-administration-amazon-redshift-database-loader), which outlines four possible options depending on your use case | 
| Allow AWS Data Pipeline to access your AWS resources | [DataPipelineDefaultRole](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | Create a role with a trust policy as defined in the [AWS Data Pipeline Developer Guide](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | [AWSDataPipelineRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSDataPipelineRole) | 
| Allow your applications running on Amazon EC2 instances to access your AWS resources | [DataPipelineDefaultResourceRole](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | Create a role with a trust policy as defined in the [AWS Data Pipeline Developer Guide](https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-iam-roles.html) | [AmazonEC2RoleforDataPipelineRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonEC2RoleforDataPipelineRole) | 

### Developer power user<a name="jf_developer-power-user"></a>

**AWS managed policy name:** [PowerUserAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/PowerUserAccess)

**Use case:** This user performs application development tasks and can create and configure resources and services that support AWS aware application development\.

**Policy description:** The first statement of this policy uses the [`NotAction`](reference_policies_elements_notaction.md) element to allow all actions for all AWS services and for all resources except AWS Identity and Access Management and AWS Organizations\. The second statement grants IAM permissions to create a service\-linked role\. This is required by some services that must access resources in another service, such as an Amazon S3 bucket\. It also grants Organizations permissions to view information about the user's organization, including the master account email and organization limitations\.

### Network administrator<a name="jf_network-administrator"></a>

**AWS managed policy name:** [NetworkAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/NetworkAdministrator)

**Use case:** This user is tasked with setting up and maintaining AWS network resources\.

**Policy description:** This policy grants permissions to create and maintain network resources in Auto Scaling, Amazon EC2, AWS Direct Connect, Route 53, Amazon CloudFront, Elastic Load Balancing, AWS Elastic Beanstalk, Amazon SNS, CloudWatch, CloudWatch Logs, Amazon S3, IAM, and Amazon Virtual Private Cloud\.

This job function requires the ability to pass roles to AWS services\. The policy grants `iam:GetRole` and `iam:PassRole` for only those roles named in the following table\. For more information, see [Creating roles and attaching policies \(console\)](#access_policies_job-functions_create-policies) later in this topic\.


**Optional IAM service roles for the network administrator job function**  

| Use case | Role name \(\* is a wildcard\) | Service role type to select | AWS managed policy to select | 
| --- | --- | --- | --- | 
| Allows Amazon VPC to create and manage logs in CloudWatch Logs on the user's behalf to monitor IP traffic going in and out of your VPC | [flow\-logs\-\*](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html#flow-logs-iam) | Create a role with a trust policy as defined in the [Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html#flow-logs-iam) | This use case does not have an existing AWS managed policy, but the documentation lists the required permissions\. See [Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html#flow-logs-iam)\. | 

### Security auditor<a name="jf_security-auditor"></a>

**AWS managed policy name:** [SecurityAudit](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/SecurityAudit)

**Use case:** This user monitors accounts for compliance with security requirements\. This user can access logs and events to investigate potential security breaches or potential malicious activity\.

**Policy description:** This policy grants permissions to view configuration data for many AWS services and to review their logs\. 

### Support user<a name="jf_support-user"></a>

**AWS managed policy name:** [SupportUser](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/SupportUser)

**Use case:** This user contacts AWS Support, creates support cases, and views the status of existing cases\.

**Policy description:** This policy grants permissions to create and update AWS Support cases\.

### System administrator<a name="jf_system-administrator"></a>

**AWS managed policy name:** [SystemAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/SystemAdministrator)

**Use case:** This user sets up and maintains resources for development operations\.

**Policy description:** This policy grants permissions to create and maintain resources across a large variety of AWS services, including AWS CloudTrail, Amazon CloudWatch, AWS CodeCommit, AWS CodeDeploy, AWS Config, AWS Directory Service, Amazon EC2, AWS Identity and Access Management, AWS Key Management Service, AWS Lambda, Amazon RDS, Route 53, Amazon S3, Amazon SES, Amazon SQS, AWS Trusted Advisor, and Amazon VPC\.

This job function requires the ability to pass roles to AWS services\. The policy grants `iam:GetRole` and `iam:PassRole` for only those roles named in the following table\. For more information, see [Creating roles and attaching policies \(console\)](#access_policies_job-functions_create-policies) later in this topic\.


**Optional IAM service roles for the system administrator job function**  

| Use case | Role name \(\* is a wildcard\) | Service role type to select | AWS managed policy to select | 
| --- | --- | --- | --- | 
| Allow apps running in EC2 instances in an Amazon ECS cluster to access Amazon ECS | [ecr\-sysadmin\-\*](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/instance_IAM_role.html) | Amazon EC2 Role for EC2 Container Service  | [AmazonEC2ContainerServiceforEC2Role](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonEC2ContainerServiceforEC2Role) | 
| Allow a user to monitor databases | [rds\-monitoring\-role](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html) | Amazon RDS Role for Enhanced Monitoring | [AmazonRDSEnhancedMonitoringRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AmazonRDSEnhancedMonitoringRole) | 
| Allow apps running in EC2 instances to access AWS resources\. | [ec2\-sysadmin\-\*](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) | Amazon EC2 | Sample policy for role that grants access to an S3 bucket as shown in the [Amazon EC2 User Guide for Linux Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html); customize as needed | 
| Allow Lambda to read DynamoDB streams and write to CloudWatch Logs | [lambda\-sysadmin\-\*](https://docs.aws.amazon.com/lambda/latest/dg/with-ddb.html) | AWS Lambda | [AWSLambdaDynamoDBExecutionRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSLambdaDynamoDBExecutionRole) | 

### View\-only user<a name="jf_view-only-user"></a>

**AWS managed policy name:** [ViewOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/ViewOnlyAccess)

**Use case:** This user can view a list of AWS resources and basic metadata in the account across all services\. The user cannot read resource content or metadata that goes beyond the quota and list information for resources\.

**Policy description:** This policy grants `List*`, `Describe*`, `Get*`, `View*`, and `Lookup*` access to resources for most AWS services\. To see what actions this policy includes for each service, see [ViewOnlyAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/ViewOnlyAccess)\.

## Creating roles and attaching policies \(console\)<a name="access_policies_job-functions_create-policies"></a>

Several of the previously listed policies grant the ability to configure AWS services with roles that enable those services to perform operations on your behalf\. The job function policies either specify exact role names that you must use or at least include a prefix that specifies the first part of the name that can be used\. To create one of these roles, perform the steps in the following procedure\.

**To create a role for an AWS service \(IAM console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. Choose the **AWS service** role type, and then choose the service that you want to allow to assume this role\.

1. Choose the use case for your service\. If the specified service has only one use case, it is selected for you\. Use cases are defined by the service to include the trust policy that the service requires\. Then choose **Next: Permissions**\.

1. If possible, select the policy to use for the permissions policy or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see step 4 in the procedure [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-start) in the *IAM User Guide*\. After you create the policy, close that tab and return to your original tab\. Select the check box next to the permissions policies that you want the service to have\.

   Depending on the use case that you selected, the service might allow you to do any of the following:
   + Nothing, because the service defines the permissions for the role
   + Allow you to choose from a limited set of permissions
   + Allow you to choose from any permissions
   + Allow you to select no policies at this time, create the policies later, and then attach them to the role

1. \(Optional\) Set a [permissions boundary](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html)\. This is an advanced feature that is available for service roles, but not service\-linked roles\. 

   Expand the **Set permissions boundary** section and choose **Use a permissions boundary to control the maximum role permissions**\. IAM includes a list of the AWS managed and customer managed policies in your account\. Select the policy to use for the permissions boundary or choose **Create policy** to open a new browser tab and create a new policy from scratch\. For more information, see step 4 in the procedure [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-start) in the *IAM User Guide*\. After you create the policy, close that tab and return to your original tab to select the policy to use for the permissions boundary\.

1. Choose **Next: Tags**\.

1. \(Optional\) Add metadata to the user by attaching tags as key\-value pairs\. For more information about using tags in IAM, see [Tagging IAM Entities](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_tags.html) in the *IAM User Guide*\.

1. Choose **Next: Review**\.

1. For **Role name**, the degree of role name customization is defined by the service\. If the service defines the role's name, this option is not editable\. In other cases, the service might define a prefix for the role and allow you to enter an optional suffix\. Some services allow you to specify the entire name of your role\.

   If possible, enter a role name or role name suffix to help you identify the purpose of this role\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because various entities might reference the role, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Role description**, enter a description for the new role\.

1. Review the role and then choose **Create role**\.

## Example 1: Configuring a user as a database administrator \(console\)<a name="jf_example_1"></a>

This example shows the steps required to configure Alice, an IAM user, as a [Database Administrator](#jf_database-administrator)\. You use the information in first row of the table in that section and allow the user to enable Amazon RDS monitoring\. You attach the [DatabaseAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/DatabaseAdministrator) policy to Alice's IAM user so that she can manage the Amazon database services\. That policy also enables Alice to pass a role called `rds-monitoring-role` to the Amazon RDS service that allows the service to monitor the RDS databases on her behalf\.

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Policies** and then type **database** in the search box\.

1. Select the check box for the **DatabaseAdministrator** policy, choose **Policy actions**, and then choose **Attach**\.

1. In the list of users, select **Alice** and then choose **Attach policy**\. Alice now can administer AWS databases\. However, to allow Alice to monitor those databases, you must configure the service role\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. Choose the **AWS Service** role type, and then choose **Amazon RDS**\.

1. Choose the **Amazon RDS Role for Enhanced Monitoring** use case\.

1. Amazon RDS defines the permissions for your role\. Choose **Next: Review** to continue\.

1. The role name must be one of those specified by the DatabaseAdministrator policy that Alice now has\. One of those is **rds\-monitoring\-role**\. Type that for the **Role name**\.

1. \(Optional\) For **Role description**, type a description for the new role\.

1. After you review the details, choose **Create role**\.

1. Alice can now enable **RDS Enhanced Monitoring** in the **Monitoring** section of the Amazon RDS console\. For example, she might do this when she creates a DB instance, creates a read replica, or modifies a DB instance\. She must type the role name she created \(rds\-monitoring\-role\) in the **Monitoring Role** box when she sets **Enable Enhanced Monitoring** to **Yes**\. 

## Example 2: Configuring a user as a network administrator \(console\)<a name="jf_example_2"></a>

This example shows the steps required to configure Juan, an IAM user, as a [Network Administrator](#jf_network-administrator)\. It uses the information in the table in that section to allow Juan to monitor IP traffic going to and from a VPC\. It also allows Juan to capture that information in the logs in CloudWatch Logs\. You attach the [NetworkAdministrator](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/NetworkAdministrator) policy to Juan's IAM user so that he can configure AWS network resources\. That policy also enables Juan to pass a role whose name begins with `flow-logs*` to Amazon EC2 when you create a flow log\. In this scenario, unlike Example 1, there isn't a predefined service role type, so you must perform a few steps differently\.

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies** and then type **network** in the search box\.

1. Select the check box next to **NetworkAdministrator** policy, choose **Policy actions**, and then choose **Attach**\.

1. In the list of users, select the check box next to **Juan** and then choose **Attach policy**\. Juan now can administer AWS network resources\. However, to enable monitoring of IP traffic in your VPC, you must configure the service role\.

1. Because the service role you need to create doesn't have a predefined managed policy, you must first create it\. In the navigation pane, choose **Policies**, then choose **Create policy**\.

1. Choose the **JSON** tab and copy the text from the following JSON policy document\. Paste this text into the **JSON** text box\. 

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Action": [
           "logs:CreateLogGroup",
           "logs:CreateLogStream",
           "logs:PutLogEvents",
           "logs:DescribeLogGroups",
           "logs:DescribeLogStreams"
         ],
         "Effect": "Allow",
         "Resource": "*"
       }
     ]
   }
   ```

1. When you are finished, choose **Review policy**\. The [Policy Validator](access_policies_policy-validator.md) reports any syntax errors\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review** page, type **vpc\-flow\-logs\-policy\-for\-service\-role** for the policy name\. Review the policy **Summary** to see the permissions granted by your policy, and then choose **Create policy** to save your work\.

   The new policy appears in the list of managed policies and is ready to attach\.

1. In the navigation pane of the IAM console, choose **Roles**, and then choose **Create role**\.

1. Choose the **AWS Service** role type, and then choose **Amazon EC2**\.

1. Choose the **Amazon EC2** use case\.

1. On the **Attach permissions policies** page, choose the policy you created earlier, **vpc\-flow\-logs\-policy\-for\-service\-role**, and then choose **Next: Review**\.

1. The role name must be permitted by the NetworkAdministrator policy that Juan now has\. Any name that begins with `flow-logs-` is allowed\. For this example, type **flow\-logs\-for\-juan** for the **Role name**\.

1. \(Optional\) For **Role description**, type a description for the new role\.

1. After you review the details, choose **Create role**\.

1. Now you can configure the trust policy required for this scenario\. On the **Roles** page, choose the **flow\-logs\-for\-juan** role \(the name, not the check box\)\. On the details page for your new role, choose the **Trust relationships** tab, and then choose **Edit trust relationship**\.

1. Change the "Service" line to read as follows, replacing the entry for `ec2.amazonaws.com`:

   ```
           "Service": "vpc-flow-logs.amazonaws.com"
   ```

1. Juan can now create flow logs for a VPC or subnet in the Amazon EC2 console\. When you create the flow log, specify the **flow\-logs\-for\-juan** role\. That role has the permissions to create the log and write data to it\.