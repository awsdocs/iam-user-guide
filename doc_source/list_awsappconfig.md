# Actions, resources, and condition keys for AWS AppConfig<a name="list_awsappconfig"></a>

AWS AppConfig \(service prefix: `appconfig`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/appconfig/2019-10-09/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig-getting-started-permissions.html) permission policies\.

**Topics**
+ [Actions defined by AWS AppConfig](#awsappconfig-actions-as-permissions)
+ [Resource types defined by AWS AppConfig](#awsappconfig-resources-for-iam-policies)
+ [Condition keys for AWS AppConfig](#awsappconfig-policy-keys)

## Actions defined by AWS AppConfig<a name="awsappconfig-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsappconfig.html)

## Resource types defined by AWS AppConfig<a name="awsappconfig-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsappconfig-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ application ](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig-creating-application.html)  |  arn:$\{Partition\}:appconfig:$\{Region\}:$\{Account\}:application/$\{ApplicationId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsappconfig-aws_ResourceTag___TagKey_)   | 
|   [ environment ](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig-creating-environment.html)  |  arn:$\{Partition\}:appconfig:$\{Region\}:$\{Account\}:application/$\{ApplicationId\}/environment/$\{EnvironmentId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsappconfig-aws_ResourceTag___TagKey_)   | 
|   [ configurationprofile ](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig-creating-configuration-and-profile.html)  |  arn:$\{Partition\}:appconfig:$\{Region\}:$\{Account\}:application/$\{ApplicationId\}/configurationprofile/$\{ConfigurationProfileId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsappconfig-aws_ResourceTag___TagKey_)   | 
|   [ deploymentstrategy ](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig-creating-deployment-strategy.html)  |  arn:$\{Partition\}:appconfig:$\{Region\}:$\{Account\}:deploymentstrategy/$\{DeploymentStrategyId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsappconfig-aws_ResourceTag___TagKey_)   | 
|   [ deployment ](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig-deploying.html)  |  arn:$\{Partition\}:appconfig:$\{Region\}:$\{Account\}:application/$\{ApplicationId\}/environment/$\{EnvironmentId\}/deployment/$\{DeploymentNumber\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awsappconfig-aws_ResourceTag___TagKey_)   | 
|   [ hostedconfigurationversion ](https://docs.aws.amazon.com/systems-manager/latest/userguide/appconfig-creating-configuration-and-profile.html)  |  arn:$\{Partition\}:appconfig:$\{Region\}:$\{Account\}:application/$\{ApplicationId\}/configurationprofile/$\{ConfigurationProfileId\}/hostedconfigurationversion/$\{VersionNumber\}  |  | 

## Condition keys for AWS AppConfig<a name="awsappconfig-policy-keys"></a>

AWS AppConfig defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#policy-conditions)  | Filters 'Create' requests based on the allowed set of values for a specified tags | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#policy-conditions)  | Filters access based on a tag key\-value pair assigned to the AWS resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#policy-conditions)  | Filters 'Create' requests based on whether mandatory tags are included in the request | String | 