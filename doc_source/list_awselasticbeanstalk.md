# Actions, resources, and condition keys for AWS Elastic Beanstalk<a name="list_awselasticbeanstalk"></a>

AWS Elastic Beanstalk \(service prefix: `elasticbeanstalk`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/elasticbeanstalk/latest/api/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/access_permissions.html) permission policies\.

**Topics**
+ [Actions defined by AWS Elastic Beanstalk](#awselasticbeanstalk-actions-as-permissions)
+ [Resource types defined by AWS Elastic Beanstalk](#awselasticbeanstalk-resources-for-iam-policies)
+ [Condition keys for AWS Elastic Beanstalk](#awselasticbeanstalk-policy-keys)

## Actions defined by AWS Elastic Beanstalk<a name="awselasticbeanstalk-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awselasticbeanstalk.html)

## Resource types defined by AWS Elastic Beanstalk<a name="awselasticbeanstalk-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awselasticbeanstalk-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ application ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html)  |  arn:$\{Partition\}:elasticbeanstalk:$\{Region\}:$\{Account\}:application/$\{ApplicationName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awselasticbeanstalk-aws_ResourceTag___TagKey_)   | 
|   [ applicationversion ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html)  |  arn:$\{Partition\}:elasticbeanstalk:$\{Region\}:$\{Account\}:applicationversion/$\{ApplicationName\}/$\{VersionLabel\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awselasticbeanstalk-aws_ResourceTag___TagKey_)   [ elasticbeanstalk:InApplication ](#awselasticbeanstalk-elasticbeanstalk_InApplication)   | 
|   [ configurationtemplate ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html)  |  arn:$\{Partition\}:elasticbeanstalk:$\{Region\}:$\{Account\}:configurationtemplate/$\{ApplicationName\}/$\{TemplateName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awselasticbeanstalk-aws_ResourceTag___TagKey_)   [ elasticbeanstalk:InApplication ](#awselasticbeanstalk-elasticbeanstalk_InApplication)   | 
|   [ environment ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html)  |  arn:$\{Partition\}:elasticbeanstalk:$\{Region\}:$\{Account\}:environment/$\{ApplicationName\}/$\{EnvironmentName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awselasticbeanstalk-aws_ResourceTag___TagKey_)   [ elasticbeanstalk:InApplication ](#awselasticbeanstalk-elasticbeanstalk_InApplication)   | 
|   [ solutionstack ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html)  |  arn:$\{Partition\}:elasticbeanstalk:$\{Region\}::solutionstack/$\{SolutionStackName\}  |  | 
|   [ platform ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html)  |  arn:$\{Partition\}:elasticbeanstalk:$\{Region\}::platform/$\{PlatformNameWithVersion\}  |  | 

## Condition keys for AWS Elastic Beanstalk<a name="awselasticbeanstalk-policy-keys"></a>

AWS Elastic Beanstalk defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters actions based on the presence of tag key\-value pairs in the request\. | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters actions based on tag key\-value pairs attached to the resource\. | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters actions based on the presence of tag keys in the request\. | String | 
|   [ elasticbeanstalk:FromApplication ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters access by an application as a dependency or a constraint on an input parameter\. | ARN | 
|   [ elasticbeanstalk:FromApplicationVersion ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters access by an application version as a dependency or a constraint on an input parameter\. | ARN | 
|   [ elasticbeanstalk:FromConfigurationTemplate ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters access by a configuration template as a dependency or a constraint on an input parameter\. | ARN | 
|   [ elasticbeanstalk:FromEnvironment ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters access by an environment as a dependency or a constraint on an input parameter\. | ARN | 
|   [ elasticbeanstalk:FromPlatform ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters access by a platform as a dependency or a constraint on an input parameter\. | ARN | 
|   [ elasticbeanstalk:FromSolutionStack ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters access by a solution stack as a dependency or a constraint on an input parameter\. | ARN | 
|   [ elasticbeanstalk:InApplication ](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions)  | Filters access by the application that contains the resource that the action operates on\. | ARN | 