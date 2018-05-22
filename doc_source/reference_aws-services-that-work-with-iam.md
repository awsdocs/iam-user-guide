# AWS Services That Work with IAM<a name="reference_aws-services-that-work-with-iam"></a>

The AWS services listed below are grouped by their [AWS product categories](https://aws.amazon.com/products/) and include information about what IAM features they support:
+ **Service** – You can choose the name of a service to view the AWS documentation for that service\.
+ **Actions** – You can specify individual actions in a policy\. If the service does not support this feature, then **All actions** is selected in the [visual editor](access_policies_create.md#access_policies_create-visual-editor)\. In a JSON policy document, you must use `*` in the `Action` element\. For a list of actions in each service, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\.
+ **Resource\-level permissions** – You can use [ARNs](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) to specify individual resources in the policy\. If the service does not support this feature, then **All resources** is chosen in the [policy visual editor](access_policies_create.md#access_policies_create-visual-editor)\. In a JSON policy document, you must use `*` in the `Resource` element\. Some actions, such as `List*` actions, do not support specifying an ARN because they are designed to return multiple resources\. If a service supports this feature for some resources but not others, it is indicated by yellow cells in the table\. See the documentation for that service for more information\.
+ **Resource\-based policies** – You can attach resource\-based policies to a resource within the service\. Resource\-based policies include a `Principal` element to specify which IAM identities can access that resource\. For more information, see [Identity\-Based Policies and Resource\-Based Policies](access_policies_identity-vs-resource.md)\.
+ **Authorization based on tags** – You can use [resource tags](http://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/tag-editor.html) in the condition of a policy\. For example, you might create a [ policy that allows tag owners full access to Amazon RDS resources](reference_policies_examples_rds_tag-owner.md) that they have tagged\. You do this by using a condition key such as `rds:db-tag/Owner`\.
+ **Temporary credentials** – Users signed in with federation, a cross\-account role, or a [service role](id_roles_terms-and-concepts.md#iam-term-service-role) can access the service\. Temporary security credentials are obtained by calling AWS STS API operations like [AssumeRole](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) or [GetFederationToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)\. For more information, see [Temporary Security Credentials](id_credentials_temp.md)\. 
+ **Service\-linked roles** – A [service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role) gives the service permission to access resources in other services to complete an action on your behalf\. Choose the `Yes` link to see the documentation for services that support these roles\. For more information, see [Using Service\-Linked Roles](using-service-linked-roles.md)\.
+ **More information** – If a service doesn't fully support a feature, you can review the footnotes for an entry to view the limitations and links to related information\.

## Compute Services<a name="compute_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [Application Auto Scaling](http://docs.aws.amazon.com/autoscaling/application/APIReference/Welcome.html)  | Yes | Yes | No | No | Yes | [Yes](http://docs.aws.amazon.com/autoscaling/application/APIReference/application-autoscaling-service-linked-roles.html) | 
|  [Amazon EC2 Auto Scaling](http://docs.aws.amazon.com/autoscaling/latest/userguide/IAM.html)  | Yes | Yes | No | No | Yes | [Yes](http://docs.aws.amazon.com/autoscaling/ec2/userguide/autoscaling-service-linked-role.html) | 
|  [AWS Batch](http://docs.aws.amazon.com/batch/latest/userguide/IAM_policies.html )  | Yes | No | No | No | Yes | No | 
|  [Amazon Elastic Compute Cloud \(Amazon EC2\)](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html)  | Yes | Yes | No | Yes | Yes | Yes¹ | 
|  [AWS Elastic Beanstalk](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.html)  | Yes | Yes | No | No | Yes | [Yes](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-service-linked-roles.html) | 
|  [Amazon Elastic Container Registry \(Amazon ECR\)](http://docs.aws.amazon.com/AmazonECR/latest/userguide/ECR_IAM_policies.html)  | Yes | Yes | Yes | No | Yes | No | 
|  [Amazon Elastic Container Service \(Amazon ECS\)](http://docs.aws.amazon.com/AmazonECS/latest/developerguide//IAM_policies.html)  | Yes | Yes | No | No | Yes | [Yes](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/using-service-linked-roles.html) | 
|  [Elastic Load Balancing](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/index.html?UsingIAM.html)  | Yes | Yes | No | No | Yes | [Yes](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/elb-service-linked-roles.html) | 
|  [AWS Lambda](http://docs.aws.amazon.com/lambda/latest/dg/lambda-auth-and-access-control.html)  | Yes | Yes | Yes² | No | Yes | No | 
|  [Amazon Lightsail](https://lightsail.aws.amazon.com/ls/docs/all) | Yes | No | No | No | Yes | No | 

¹ Amazon EC2 service\-linked roles cannot be created using the AWS Management Console, and can be used only for the following features: [Scheduled Instances](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-scheduled-instances.html#service-linked-roles-scheduled-instances), [Spot Instance Requests](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-requests.html#service-linked-roles-spot-instance-requests), [Spot Fleet Requests](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-fleet-requests.html#service-linked-roles-spot-fleet-requests) 

² The only AWS Lambda API action that can be specified in a resource\-based policy is [lambda:InvokeFunction](http://docs.aws.amazon.com/lambda/latest/dg/API_Invoke.html)\. For more information, see [Using Resource\-Based Policies for AWS Lambda \(Lambda Function Policies\)](http://docs.aws.amazon.com/lambda/latest/dg/access-control-resource-based.html) in the *AWS Lambda Developer Guide*\.

## Storage and Migration Services<a name="storage_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [Amazon Elastic Block Store \(Amazon EBS\)](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html)  | Yes | Yes | No | Yes | Yes | No | 
|  [Amazon Elastic File System \(Amazon EFS\)](http://docs.aws.amazon.com/efs/latest/ug/auth-and-access-control.html)  | Yes | Yes | No | No | Yes | No | 
|  [Amazon Glacier](http://docs.aws.amazon.com/amazonglacier/latest/dev/auth-and-access-control.html)  | Yes | Yes | Yes | Yes | Yes | No | 
|  [AWS Import/Export](http://docs.aws.amazon.com/AWSImportExport/latest/DG/using-iam.html)  | Yes | No | No | No | Yes | No | 
|  [AWS Migration Hub](http://docs.aws.amazon.com/server-migration-service/latest/userguide/auth-and-access-control.html)  | Yes | Yes | No | No | Yes | No | 
|  [Amazon Simple Storage Service \(Amazon S3\)](http://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html)  | Yes | Yes | Yes | [Yes](http://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html) | Yes | No | 
| [AWS Snowball](http://docs.aws.amazon.com/snowball/latest/ug/auth-access-control.html) | Yes | No | No | No | Yes | No | 
| [AWS Snowball Edge](http://docs.aws.amazon.com/snowball/latest/developer-guide/authentication-and-access-control.html) | Yes | No | No | No | No | No | 
|  [AWS Storage Gateway](http://docs.aws.amazon.com/storagegateway/latest/userguide/UsingIAMWithStorageGateway.html)  | Yes | Yes | No | No | Yes | No | 

## Database Services<a name="database_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [AWS Database Migration Service](http://docs.aws.amazon.com/dms/latest/userguide/CHAP_Security.IAMPermissions.html)  | Yes | Yes | No | Yes | Yes | No | 
|  [Amazon DynamoDB](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/UsingIAMWithDDB.html)  | Yes | Yes | No | No | Yes | [Yes](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/using-service-linked-roles.html) | 
|  [Amazon ElastiCache](http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/IAM.html)  | Yes | No¹ | No | No | Yes | [Yes](http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/using-service-linked-roles.html) | 
|  [Amazon Redshift](http://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-authentication-access-control.html)  | Yes | Yes | No | Yes | Yes | [Yes](http://docs.aws.amazon.com/redshift/latest/mgmt/using-service-linked-roles.html) | 
|  [Amazon Relational Database Service \(Amazon RDS\)](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.html)  | Yes | Yes | No | Yes | Yes | [Yes](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.ServiceLinkedRoles.html) | 
|  [Amazon SimpleDB](http://docs.aws.amazon.com/AmazonSimpleDB/latest/DeveloperGuide/UsingIAMWithSDB.html)  | Yes | Yes | No | No | Yes | No | 

¹ Two API operations specify an Amazon S3 ARN resource when seeding a cluster/replication group\.

## Networking and Content Delivery Services<a name="networking_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [Amazon API Gateway](http://docs.aws.amazon.com/apigateway/latest/developerguide/permissions.html)  | Yes | Yes | No | No | Yes | No | 
|   [Amazon CloudFront](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/index.html?UsingWithIAM.html)   | Yes¹ | No | No | No | Yes | No | 
|  [AWS Direct Connect](http://docs.aws.amazon.com/directconnect/latest/UserGuide/using_iam.html)  | Yes | No | No | No | Yes | No | 
|  [Amazon Route 53](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide//auth-and-access-control.html)  | Yes | Yes | No | No | Yes | No | 
|  [Amazon Virtual Private Cloud \(Amazon VPC\)](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_IAM.html)  | Yes | Yes² | Yes³ | Yes | Yes | No | 

¹ CloudFront does not support action\-level permissions for creating CloudFront key pairs\. You must use an AWS account root user to create a CloudFront key pair\. For more information, see [Creating CloudFront Key Pairs for Your Trusted Signers](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-trusted-signers.html#private-content-creating-cloudfront-key-pairs) in the *Amazon CloudFront Developer Guide*\. 

² In an IAM user policy, you cannot restrict permissions to a specific Amazon VPC endpoint\. Any `Action` element that includes the `ec2:*VpcEndpoint*` or `ec2:DescribePrefixLists` API actions must specify "`"Resource": "*"`"\. For more information, see [Controlling the Use of Endpoints](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html#vpc-endpoints-iam-access) in the *Amazon VPC User Guide*\. 

³ Amazon VPC supports attaching a single resource policy to a VPC endpoint to restrict what can be accessed through that endpoint\. For more information about using resource\-based policies to control access to resources from specific Amazon VPC endpoints, see [Using Endpoint Policies](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html#vpc-endpoint-policies) in the *Amazon VPC User Guide*\.

## Developer Tools and Services<a name="deploy_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [AWS Cloud9](http://docs.aws.amazon.com/cloud9/latest/user-guide/auth-and-access-control.html)  | Yes | Yes | Yes | Yes | Yes | [Yes](http://docs.aws.amazon.com/cloud9/latest/user-guide/using-service-linked-roles.html) | 
|  [AWS CodeBuild](http://docs.aws.amazon.com/codebuild/latest/userguide/auth-and-access-control.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS CodeCommit](http://docs.aws.amazon.com/codecommit/latest/userguide/access-permissions.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS CodeDeploy](http://docs.aws.amazon.com/codedeploy/latest/userguide/access-permissions.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS CodePipeline](http://docs.aws.amazon.com/codepipeline/latest/userguide/access-permissions.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS CodeStar](http://docs.aws.amazon.com/codestar/latest/userguide/access-permissions.html)  | Yes | Yes¹ | No | No | No | No | 

## Management Tools and Services<a name="management_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [AWS CloudFormation](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS CloudTrail](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-access-control.html)  | Yes | Yes | No | No | Yes | No | 
|  [Amazon CloudWatch](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/UsingIAM.html)  | Yes | No | No | No | Yes | [Yes](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/using-service-linked-roles.html)¹ | 
|  [Amazon CloudWatch Events](http://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/EventsPoliciesRolesAccessControl.html)  | Yes | Yes | No | No | Yes | No | 
|  [Amazon CloudWatch Logs ](http://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/auth-and-access-control-cwl.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS Config](http://docs.aws.amazon.com/config/latest/developerguide/recommended-iam-permissions-using-aws-config-console-cli.html)  | Yes | No | No | No | Yes | No | 
|  [AWS Health](http://docs.aws.amazon.com/health/latest/ug/controlling-access.html)  | Yes | No | No | No | Yes | No | 
|  [AWS OpsWorks](http://docs.aws.amazon.com/opsworks/latest/userguide/opsworks-security-users.html)  | Yes | Yes | Yes | No | Yes | No | 
|  [AWS OpsWorks for Chef Automate](http://docs.aws.amazon.com/opsworks/latest/userguide/opsworks-security-users.html)  | Yes | Yes | Yes | No | Yes | No | 
|  [AWS Service Catalog](http://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions.html)  | Yes | No | No | No | Yes | No | 
|  [AWS Systems Manager](http://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control.html)  | Yes | Yes | No | Yes | Yes | [Yes](http://docs.aws.amazon.com/systems-manager/latest/userguide/using-service-linked-roles.html) | 
| [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/ta-iam/) | Yes² | Yes | No | No | Yes³ | No | 

¹ Amazon CloudWatch service\-linked roles cannot be created using the AWS Management Console, and support only the [ Alarm Actions](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/UsingAlarmActions.html) feature\.

² API access to Trusted Advisor is through the AWS Support API and is controlled by AWS Support IAM policies\.

³ Trusted Advisor supports the following tagging condition: `ssm:resourceTag` for Key/Value pairs and `ssm:Overwrite`\.

## Media Services<a name="media_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [Amazon Elastic Transcoder](http://docs.aws.amazon.com/elastictranscoder/latest/developerguide/security.html)  | Yes | Yes | No | No | Yes | No | 
| [AWS Elemental MediaConvert](http://docs.aws.amazon.com/mediaconvert/latest/ug/iam-role.html) | Yes | Yes | No | No | Yes | No | 
| [AWS Elemental MediaStore](http://docs.aws.amazon.com/mediastore/latest/ug/setting-up.html) | Yes | Yes | No | No | Yes | No | 
| [AWS Elemental MediaTailor](http://docs.aws.amazon.com/mediatailor/latest/ug/setting-up.html) | Yes | Yes | Yes | No | Yes | No | 
| [Kinesis Video Streams](http://docs.aws.amazon.com/kinesisvideostreams/latest/dg/how-iam.html) | Yes | Yes | No | No | Yes | No | 

## Machine Learning Services<a name="machine_learning"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
| [Amazon Comprehend](http://docs.aws.amazon.com/comprehend/latest/dg/auth-and-access-control.html) | Yes | No | No | No | Yes | No | 
| [Amazon Lex](http://docs.aws.amazon.com/lex/latest/dg/auth-and-access-control.html) | Yes | Yes | No | No | Yes | [Yes](http://docs.aws.amazon.com/lex/latest/dg/howitworks-service-permissions.html) | 
|  [Amazon Machine Learning](http://docs.aws.amazon.com/machine-learning/latest/dg/reference.html#controlling-access-to-amazon-ml-resources-by-using-iam)  | Yes | Yes | No | Yes | Yes | No | 
|  [Amazon Polly](http://docs.aws.amazon.com/polly/latest/dg/authentication-and-access-control.html)  | Yes | Yes | No | No | Yes | No | 
|  [Amazon Rekognition](http://docs.aws.amazon.com/rekognition/latest/dg/authentication-and-access-control.html)  | Yes | Yes | No | No | No | No | 
|  [Amazon SageMaker](http://docs.aws.amazon.com/sagemaker/latest/dg/authentication-and-access-control.html)  | Yes | Yes¹ | No | No | Yes | No | 
| [Amazon Transcribe](http://docs.aws.amazon.com/transcribe/latest/dg/auth-and-access-control.html) | Yes | No | No | No | Yes | No | 
| [Amazon Translate](http://docs.aws.amazon.com/translate/latest/dg/auth-and-access-control.html)  | Yes | No | No | No | Yes | No | 

¹ Amazon SageMaker does not check external resources referenced in a call\. For example, Amazon SageMaker does not support policies that restrict training jobs to certain AWS KMS keys or Amazon S3 buckets\.

## Analytics Services<a name="analytics_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [Amazon Athena](http://docs.aws.amazon.com/athena/latest/ug/access.html)  | Yes | No | No | No | No | No | 
|  [Amazon CloudSearch](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/configureaccess.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS Data Pipeline](http://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-concepts-roles.html)  | Yes | No | No | Yes | Yes | No | 
|  [Amazon Elasticsearch Service](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-createupdatedomains.html#es-createdomain-configure-access-policies)  | Yes | Yes | Yes | No | Yes | [Yes](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/slr-es.html) | 
|  [Amazon EMR](http://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-access-iam.html)  | Yes | No | No | Yes | Yes | [Yes](http://docs.aws.amazon.com/emr/latest/ManagementGuide/using-service-linked-roles.html) | 
|  [AWS Glue](http://docs.aws.amazon.com/glue/latest/dg/authentication-and-access-control.html)  | Yes | No | No | No | No | No | 
|  [Amazon Kinesis Data Analytics](http://docs.aws.amazon.com/kinesisanalytics/latest/dev/authentication-and-access-control.html)  | Yes | Yes | No | No | Yes | No | 
| [Amazon Kinesis Data Firehose](http://docs.aws.amazon.com/firehose/latest/dev/controlling-access.html) | Yes | Yes | No | No | Yes | No | 
| [Amazon Kinesis Data Streams](http://docs.aws.amazon.com/streams/latest/dev/controlling-access.html) | Yes | Yes | No | No | Yes | No | 
| [Amazon QuickSight](http://docs.aws.amazon.com/quicksight/latest/user/managing-access.html) | Yes | No | No | No | No | No | 

## Security, Identity, and Compliance Services<a name="admin_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [AWS Artifact](http://docs.aws.amazon.com/artifact/latest/ug/getting-started.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS Certificate Manager \(ACM\)](http://docs.aws.amazon.com/acm/latest/userguide/assets.html)  | Yes | Yes | No | No | Yes | No | 
|  [AWS CloudHSM](http://docs.aws.amazon.com/cloudhsm/latest/userguide/prerequisites.html#permissions-for-cloudhsm)  | Yes | No | No | No | Yes | No | 
|  [AWS CloudHSM Classic](http://docs.aws.amazon.com/cloudhsm/classic/userguide/iam-policy.html)  | Yes | No | No | No | No | No | 
|  [Amazon Cognito](http://docs.aws.amazon.com/cognito/devguide/resource-permissions/)  | Yes | Yes | No | No | Yes | No | 
|  [AWS Directory Service](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/iam_policy.html)  | Yes | No | No | No | Yes | No | 
|  [Amazon GuardDuty](http://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html)  | Yes | Yes | No | No | No | [Yes](http://docs.aws.amazon.com/guardduty/latest/ug/guardduty_managing_access.html#guardduty_service-access)¹ | 
|  [AWS Identity and Access Management \(IAM\)](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions-required.html)  | Yes | Yes | No | No | Yes² | No | 
|  [Amazon Inspector](http://docs.aws.amazon.com/inspector/latest/userguide/inspector_introduction.html)  | Yes | No | No | No | Yes | [Yes](http://docs.aws.amazon.com/inspector/latest/userguide/inspector_slr.html) | 
|  [AWS Key Management Service \(AWS KMS\)](http://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html)  | Yes | Yes | Yes | No | Yes | No | 
| [AWS Organizations](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_permissions_overview.html) | Yes | Yes | No | No | Yes | Yes | 
| [AWS Secrets Manager](http://docs.aws.amazon.com/secretsmanager/latest/userguide/auth-and-access.html) | Yes | Yes | No | Yes | Yes | No | 
|  [AWS Single Sign\-On \(AWS SSO\)](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access.html)  | Yes | No | Yes | No | Yes | No | 
|  [AWS Security Token Service \(AWS STS\)](http://docs.aws.amazon.com/STS/latest/UsingSTS/TokenPermissions.html)  | Yes | Yes³ | No | No | Yes⁴ | No | 
|  [AWS Shield Advanced](http://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html)  | Yes | No | No | No | Yes | No | 
|  [AWS WAF](http://docs.aws.amazon.com/waf/latest/developerguide/waf-auth-and-access-control.html)  | Yes | Yes | No | No | Yes | No | 

¹ GuardDuty does not support creating a service\-linked role using the IAM console\.

² Only some of the API actions for IAM can be called with temporary credentials\. For more information, see [Comparing your API options](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_request.html)

³ AWS STS does not have "resources," but does allow restricting access in a similar way to users\. For more information, see [Denying Access to Temporary Security Credentials by Name](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_control-access_disable-perms.html#denying-access-to-credentials-by-name)\. 

⁴ Only some of the API operations for AWS STS support calling with temporary credentials\. For more information, see [Comparing your API options](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_request.html)\.

## Mobile Services<a name="mobile_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [AWS Device Farm](http://docs.aws.amazon.com/devicefarm/latest/developerguide/permissions.html)  | Yes | No | No | No | Yes | No | 
| Amazon Mobile Analytics | Yes | No | No | No | Yes | No | 
| [AWS Mobile Hub](http://docs.aws.amazon.com/aws-mobile/latest/developerguide/reference-mobile-hub-iam.html) | Yes | Yes | No | No | Yes | No | 
|  [Amazon Pinpoint](http://docs.aws.amazon.com/pinpoint/latest/developerguide/permissions-actions.html)  | Yes | Yes | No | No | Yes | No | 

## Application Integration Services<a name="app_integration_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [Amazon MQ](http://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html#create-iam-user)  | Yes | No | No | No | Yes | No | 
|  [Amazon Simple Email Service \(Amazon SES\)](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/UsingWithIAM.html)  | Yes | Yes¹ | No | No | Yes² | No | 
|  [Amazon Simple Notification Service \(Amazon SNS\)](http://docs.aws.amazon.com/sns/latest/dg/UsingIAMwithSNS.html)  | Yes | Yes | Yes | No | Yes | No | 
|  [Amazon Simple Queue Service \(Amazon SQS\)](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/UsingIAM.html)  | Yes | Yes | Yes | No | Yes | No | 
|  [Amazon Simple Workflow Service \(Amazon SWF\)](http://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-dev-iam.html)  | Yes | Yes | No | Yes | Yes | No | 

¹ Amazon SES supports resource\-level permissions in policies that grant permissions to delegate senders to access specific SES identities\.

² Only the Amazon SES API supports temporary security credentials\. The Amazon SES SMTP interface does not support SMTP credentials that are derived from temporary security credentials\. 

## Business Productivity Services<a name="enterprise_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
| Alexa for Business  | Yes | Yes | No | Yes | Yes | No | 
|  [Amazon WorkDocs](http://docs.aws.amazon.com/workdocs/latest/adminguide/setting_up.html#iam_policies)  | Yes | No | No | No | Yes | No | 
|  [Amazon WorkMail](http://docs.aws.amazon.com/workmail/latest/adminguide/iam_users_groups.html)  | Yes | No | No | No | Yes | No | 

## Desktop and App Streaming Services<a name="desktop-app_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [Amazon AppStream](http://docs.aws.amazon.com//appstream/latest/developerguide/appstream-security.html)  | Yes | No | No | No | Yes | No | 
|  [Amazon AppStream 2\.0](http://docs.aws.amazon.com//appstream2/latest/developerguide/controlling-access.html)  | Yes | No | No | No | Yes | No | 
|  [Amazon WorkSpaces](http://docs.aws.amazon.com/workspaces/latest/adminguide/wsp_iam.html)  | Yes | Yes | No | No | Yes | No | 
|  [Amazon WAM](http://docs.aws.amazon.com/wam/latest/adminguide/iam.html)  | Yes | No | No | No | Yes | No | 

## Internet of Things Services<a name="iot_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [AWS Greengrass](http://docs.aws.amazon.com/greengrass/latest/userguide/gg-ug.html)  | Yes | Yes | Yes | No | Yes | No | 
|  [AWS IoT](http://docs.aws.amazon.com/iot/latest/developerguide/iot-security-identity.html)  | [Yes](http://docs.aws.amazon.com/iot/latest/developerguide/policy-actions.html) | [Yes](http://docs.aws.amazon.com/iot/latest/developerguide/action-resources.html) | Yes¹ | No | Yes | No | 

¹ Devices connected to AWS IoT are authenticated by using X\.509 certificates\. You can attach AWS IoT policies to an X\.509 certificate to control what the device is authorized to do\. For more information, see [Create an AWS IoT Policy](http://docs.aws.amazon.com/iot/latest/developerguide/create-iot-policy.html) in the *AWS IoT Developer Guide*\. 

## Game Development Services<a name="game_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [Amazon GameLift](http://docs.aws.amazon.com/gamelift/latest/developerguide/gamelift-iam-policy-intro.html)  | Yes | No | No | No | Yes | No | 

## Software Services<a name="software_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [AWS Marketplace](http://docs.aws.amazon.com/marketplace/latest/controlling-access/ControllingAccessToAWSMarketplaceSubscriptions.html)  | Yes | Yes | No | No | Yes | No | 

## Additional Resources<a name="resources_svcs"></a>


|  |  |  |  |  |  |  | 
| --- |--- |--- |--- |--- |--- |--- |
|  Service  |  Actions  |  Resource\-level permissions  | Resource\-based policies |  Authorization based on tags  |  Temporary credentials  |  Service\-linked roles  | 
|  [AWS Billing and Cost Management](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/ControllingAccessWebsite.html)  | Yes | No | No | No | Yes | No | 
|  [AWS Support](http://docs.aws.amazon.com/awssupport/latest/user/getting-started.html#accessing-support)  | No | No | No | No | Yes | No | 