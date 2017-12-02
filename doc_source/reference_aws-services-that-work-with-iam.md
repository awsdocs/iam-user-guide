# AWS Services That Work with IAM<a name="reference_aws-services-that-work-with-iam"></a>

Many AWS services are integrated with AWS Identity and Access Management\. The following tables group these services by category and show the IAM permission types that each service supports, tips to help you write policies to control service access, and links to related information\.

Specifically, each table provides the following information:

+ **Action\-level permissions**\. The service supports specifying individual actions in a policy's `Action` element\. If the service does not support action\-level permissions, policies for the service use `*` in the `Action` element\. For a list of all of the permissions for the AWS services can be used in IAM policies, see [AWS Service Actions and Condition Context Keys for Use in IAM Policies](reference_policies_actionsconditions.md)\.

+ **Resource\-level permissions**\. The service has one or more APIs that support specifying individual resources \(using [ARNs](http://alpha-docs-aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html)\) in the policy's `Resource` element\. If an API does not support resource\-level permissions, then that statement in the policy must use `*` in the `Resource` element\. See the footnotes after each table for more information\. 

+ **Resource\-based permissions**\. The service enables you to attach resource\-based policies to the service's resources\. Resource\-based policies include a `Principal` element to specify an IAM identity that can access that resource\. Identity\-based \( IAM\) permissions are different\. They are attached to users, groups, or roles and include a `Resource` element to specify the resource that can be accessed by the identity\. For more details, see [Identity\-Based Policies and Resource\-Based Policies](access_policies_identity-vs-resource.md)\.

+ **Tag\-based permissions**\. The service supports testing [resource tags](http://alpha-docs-aws.amazon.com/awsconsolehelpdocs/latest/gsg/tag-editor.html) in a `Condition` element\. 

+ **Temporary security credentials**\. The service lets users make requests using temporary security credentials that are obtained by calling AWS STS APIs like [AssumeRole](http://alpha-docs-aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) or [GetFederationToken](http://alpha-docs-aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)\. Temporary credentials are commonly used in federation scenarios\. For more information, see [Temporary Security Credentials](id_credentials_temp.md)\. 

+ **Service\-linked roles**\. The service requires that you use a unique type of service role that is linked directly to the service\. This service\-linked role is predefined by the service, and includes all the permissions that the service requires\. To learn how to create a role used to delegate permissions to a service, see [Creating a Role to Delegate Permissions to an AWS Service](id_roles_create_for-service.md)\.

+ **More information**\. Links to more information in the documentation of the product\.

## Compute Services<a name="compute_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ Amazon EC2 supports resource\-level permissions and tags only for some APIs\. For more information, see [ Supported Resources and Conditions for Amazon EC2 API Actions ](http://alpha-docs-aws.amazon.com/AWSEC2/latest/DeveloperGuide/iam-policies-for-amazon-ec2.html#ec2-supported-iam-actions-resources) in the *Amazon EC2 User Guide for Linux Instances*\. 

² Amazon EC2 service\-linked roles cannot be created using the AWS Management Console, and can be used only for the following features: [Scheduled Instances](http://alpha-docs-aws.amazon.com/AWSEC2/latest/UserGuide/ec2-scheduled-instances.html#service-linked-roles-scheduled-instances), [Spot Instance Requests](http://alpha-docs-aws.amazon.com/AWSEC2/latest/UserGuide/spot-requests.html#service-linked-roles-spot-instance-requests), [Spot Fleet Requests](http://alpha-docs-aws.amazon.com/AWSEC2/latest/UserGuide/spot-fleet-requests.html#service-linked-roles-spot-fleet-requests) 

³ Amazon ECS supports resource\-level permissions only for some APIs\. For more information, see [Supported Resource\-Level Permissions for Amazon ECS API Actions](http://alpha-docs-aws.amazon.com/AmazonECS/latest/developerguide/ecs-supported-iam-actions-resources.html) in the *Amazon Elastic Container Service Developer Guide*\.

⁴ Only some API actions for Elastic Beanstalk can be used as permissions against specific resources\. For more information, see [Resources and Conditions for Elastic Beanstalk Actions](http://alpha-docs-aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html) in the *AWS Elastic Beanstalk Developer Guide*\. 

⁵ The only AWS Lambda API action that can be specified in a resource\-based policy is [lambda:InvokeFunction](http://alpha-docs-aws.amazon.com/lambda/latest/dg/API_Invoke.html)\. For more information, see [Using Resource\-Based Policies for AWS Lambda \(Lambda Function Policies\)](http://alpha-docs-aws.amazon.com/lambda/latest/dg/access-control-resource-based.html) in the *AWS Lambda Developer Guide*\.

⁶ Only some API actions for Elastic Load Balancing can be used as permissions against specific resources\. For more information, see [Control Access to Your Load Balancer](http://alpha-docs-aws.amazon.com/elasticloadbalancing/latest/userguide/UsingIAM.html) in the *Elastic Load Balancing User Guide*\.

## Storage and Content Delivery Services<a name="storage_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ For information about which EBS actions support resource\-level permissions, see [ Supported Resources and Conditions for Amazon EC2 API Actions ](http://alpha-docs-aws.amazon.com/AWSEC2/latest/DeveloperGuide/iam-policies-for-amazon-ec2.html#ec2-supported-iam-actions-resources) in the *Amazon EC2 User Guide for Linux Instances*\. 

² Specifies ARNs for related services \(Amazon S3\)\.

³ Specifies ARNs for related services \(Amazon S3, AWS Lambda, AWS Greengrass\)\.

## Database Services<a name="database_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ Two APIs specify an Amazon S3 ARN resource when seeding a cluster/replication group\.

## Networking and Content Delivery Services<a name="networking_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ In an IAM user policy, you cannot restrict permissions to a specific Amazon VPC endpoint\. Any `Action` element that includes the `ec2:*VpcEndpoint*` or `ec2:DescribePrefixLists` API actions must specify "`"Resource": "*"`"\. For more information, see [Controlling the Use of Endpoints](http://alpha-docs-aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html#vpc-endpoints-iam-access) in the *Amazon VPC User Guide*\. 

² Amazon VPC supports attaching a single resource policy to a VPC endpoint to restrict what can be accessed through that endpoint\. For more information about using resource\-based policies to control access to resources from specific Amazon VPC endpoints, see [Using Endpoint Policies](http://alpha-docs-aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html#vpc-endpoint-policies) in the *Amazon VPC User Guide*\.

³ CloudFront does not support action\-level permissions for creating CloudFront key pairs\. You must use an AWS account root user to create a CloudFront key pair\. For more information, see [Creating CloudFront Key Pairs for Your Trusted Signers](http://alpha-docs-aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-trusted-signers.html#private-content-creating-cloudfront-key-pairs) in the *Amazon CloudFront Developer Guide*\. 

## Migration Services<a name="migration_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

## Developer Tools and Services<a name="deploy_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ Only some API actions for AWS CodePipeline can be used as permissions against specific resources\. For more information, see [AWS CodePipeline Resources and Operations](http://alpha-docs-aws.amazon.com/codepipeline/latest/userguide/iam-access-control-identity-based.html#ACP_ARN_Format) in the *AWS CodePipeline User Guide*\. 

## Management Tools and Services<a name="management_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ Amazon CloudWatch service\-linked roles cannot be created using the AWS Management Console, and support only the [ Alarm Actions](http://alpha-docs-aws.amazon.com/AmazonCloudWatch/latest/monitoring/UsingAlarmActions.html) feature\.

² API access to Trusted Advisor is through the AWS Support API and is controlled by AWS Support IAM policies\.

## Security, Identity, and Compliance Services<a name="admin_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ GuardDuty does not support creating a service\-linked role using the IAM console\.

² Only some of the API actions for IAM can be called with temporary credentials\. For more information, see [Comparing your API options](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_request.html)

³ AWS STS does not have "resources," but does allow restricting access in a similar way to users\. For more information, see [Denying Access to Temporary Security Credentials by Name](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_control-access_disable-perms.html#denying-access-to-credentials-by-name)\. Only some of the APIs for AWS STS support calling with temporary credentials\. For more information, see [Comparing your API options](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_request.html)\.

## Analytics Services<a name="analytics_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

## Media Services<a name="media_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

## Artificial Intelligence<a name="ai_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹Amazon Rekognition supports resource\-level permissions only for collections\. For example, CollectionArn:"aws:rekognition:us\-west\-2:11111111111:collection/mycollection\.

## Internet of Things<a name="iot_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ For more information about AWS IoT action\-level permissions, see [AWS IoT Policy Actions](http://alpha-docs-aws.amazon.com/iot/latest/developerguide/authorization.html#policy-actions) in the *AWS IoT User Guide*\.

² For information about which AWS IoT actions support resource\-level permissions and which resources you can specify for each, see [Action Resources](http://alpha-docs-aws.amazon.com/iot/latest/developerguide/authorization.html#action-resources) in the *AWS IoT Developer Guide*\.

³ Devices connected to AWS IoT are authenticated by using X\.509 certificates\. You can attach AWS IoT policies to an X\.509 certificate to control what the device is authorized to do\. For more information, see [Create an AWS IoT Policy](http://alpha-docs-aws.amazon.com/iot/latest/developerguide/create-iot-policy.html) in the *AWS IoT Developer Guide*\. 

## Game Development Services<a name="game_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

## Mobile Services<a name="mobile_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

## Application Services<a name="app_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

## Messaging Services<a name="messaging_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

¹ Amazon SES supports resource\-level permissions in policies that grant permissions to delegate senders to access specific SES identities\.

² Only the Amazon SES API supports temporary security credentials\. The Amazon SES SMTP interface does not support SMTP credentials that are derived from temporary security credentials\. 

## Business Productivity<a name="enterprise_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

## Desktop and App Streaming Services<a name="desktop-app_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

## Additional Resources<a name="resources_svcs"></a>

[\[See the AWS documentation website for more details\]](http://alpha-docs-aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)