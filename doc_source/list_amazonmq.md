# Actions, Resources, and Condition Keys for Amazon MQ<a name="list_amazonmq"></a>

Amazon MQ \(service prefix: `mq`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by Amazon MQ](#amazonmq-actions-as-permissions)
+ [Resources Defined by MQ](#amazonmq-resources-for-iam-policies)
+ [Condition Keys for Amazon MQ](#amazonmq-policy-keys)

## Actions Defined by Amazon MQ<a name="amazonmq-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [CreateBroker](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-brokers.html#rest-api-brokers-methods-post) | Creates the broker instance | Write | [brokers\*](#amazonmq-brokers)  |  |  | 
| [CreateConfiguration](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configurations.html#rest-api-configurations-methods-post) | Creates a new configuration for the specified configuration name\. Amazon MQ uses the default configuration \(the engine type and engine version\) | Write | [configurations\*](#amazonmq-configurations)  |  |  | 
| [CreateUser](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-post) | Creates an ActiveMQ user | Write | [brokers\*](#amazonmq-brokers)  |  |  | 
| [DeleteBroker](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-delete) | Deletes the broker instance | Write | [brokers\*](#amazonmq-brokers)  |  |  | 
| [DeleteUser](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-delete) | Deletes an ActiveMQ user | Write | [brokers\*](#amazonmq-brokers)  |  |  | 
| [DescribeBroker](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-get) | Returns information about the specified broker instance\. | Read | [brokers\*](#amazonmq-brokers)  |  |  | 
| [DescribeConfiguration](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration.html#rest-api-configuration-methods-get) | Returns information about the specified configuration\. | Read | [configurations\*](#amazonmq-configurations)  |  |  | 
| [DescribeConfigurationRevision](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration-revision.html#rest-api-configuration-revision-methods-get) | Returns the specified configuration revision for the specified configuration\. | Read | [configurations\*](#amazonmq-configurations)  |  |  | 
| [DescribeUser](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-get) | Return information about an ActiveMQ user | Read | [brokers\*](#amazonmq-brokers)  |  |  | 
| [ListBrokers](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-brokers.html#rest-api-brokers-methods-get) | Returns a list of existing broker instances\. | List | [brokers\*](#amazonmq-brokers)  |  |  | 
| [ListConfigurationRevisions](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-revisions.html#rest-api-revisions-methods-get) | Returns a list of all existing revisions for the specified configuration | List | [configurations\*](#amazonmq-configurations)  |  |  | 
| [ListConfigurations](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configurations.html#rest-api-configurations-methods-get) | Returns a list of all existing configurations\. | List | [configurations\*](#amazonmq-configurations)  |  |  | 
| [ListUsers](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-users.html#rest-api-users-methods-get) | Returns a list of all existing ActiveMQ users\. | List | [brokers\*](#amazonmq-brokers)  |  |  | 
| [RebootBroker](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-restart.html#rest-api-reboot-methods-post) | Reboot the broker instance\. | Write | [brokers\*](#amazonmq-brokers)  |  |  | 
| [UpdateBroker](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-get) | Updates the information for broker instances\. | Write | [brokers\*](#amazonmq-brokers)  |  |  | 
| [UpdateConfiguration](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration.html#rest-api-configuration-methods-put) | Updates the specified configuration\. | Write | [configurations\*](#amazonmq-configurations)  |  |  | 
| [UpdateUser](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-put) | Updates the information for an ActiveMQ user\. | Write | [brokers\*](#amazonmq-brokers)  |  |  | 

## Resources Defined by MQ<a name="amazonmq-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonmq-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [brokers](url-resources-replace-me) | arn:$\{Partition\}:mq:$\{Region\}:$\{Account\}:broker:$\{broker\-id\} |  | 
| [configurations](url-resources-replace-me) | arn:$\{Partition\}:mq:$\{Region\}:$\{Account\}:configuration:$\{configuration\-id\} |  | 

## Condition Keys for Amazon MQ<a name="amazonmq-policy-keys"></a>

MQ has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.