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
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-brokers.html#rest-api-brokers-methods-post](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-brokers.html#rest-api-brokers-methods-post) | Grants permission to create a broker\. | Write |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configurations.html#rest-api-configurations-methods-post](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configurations.html#rest-api-configurations-methods-post) | Grants permission to create a new configuration for the specified configuration name\. Amazon MQ uses the default configuration \(the engine type and engine version\)\. | Write |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-post](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-post) | Grants permission to create an ActiveMQ user\. | Write |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-delete](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-delete) | Grants permission to delete a broker\. | Write |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-delete](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-delete) | Grants permission to delete an ActiveMQ user\. | Write |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-get) | Grants permission to return information about the specified broker\. | Read |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration.html#rest-api-configuration-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration.html#rest-api-configuration-methods-get) | Grants permission to return information about the specified configuration\. | Read |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration-revision.html#rest-api-configuration-revision-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration-revision.html#rest-api-configuration-revision-methods-get) | Grants permission to return the specified configuration revision for the specified configuration\. | Read |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-get) | Grants permission to return information about an ActiveMQ user\. | Read |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-brokers.html#rest-api-brokers-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-brokers.html#rest-api-brokers-methods-get) | Grants permission to return a list of all brokers\. | List |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-revisions.html#rest-api-revisions-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-revisions.html#rest-api-revisions-methods-get) | Grants permission to return a list of all existing revisions for the specified configuration\. | List |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configurations.html#rest-api-configurations-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configurations.html#rest-api-configurations-methods-get) | Grants permission to return a list of all configurations\. | List |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-users.html#rest-api-users-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-users.html#rest-api-users-methods-get) | Grants permission to return a list of all ActiveMQ users\. | List |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-restart.html#rest-api-reboot-methods-post](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-restart.html#rest-api-reboot-methods-post) | Grants permission to reboot a broker\. | Write |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-get](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-broker.html#rest-api-broker-methods-get) | Grants permission to add a pending configuration change to a broker\. | Write |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration.html#rest-api-configuration-methods-put](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-configuration.html#rest-api-configuration-methods-put) | Grants permission to update the specified configuration\. | Write |  |  |  | 
| [http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-put](http://docs.aws.amazon.com//amazon-mq/latest/api-reference/rest-api-username.html#rest-api-username-methods-put) | Grants permission to update the information for an ActiveMQ user\. | Write |  |  |  | 

## Resources Defined by MQ<a name="amazonmq-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonmq-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| brokers | arn:$\{Partition\}:mq:$\{Region\}:$\{Account\}:broker:$\{broker\-id\} |  | 
| configurations | arn:$\{Partition\}:mq:$\{Region\}:$\{Account\}:configuration:$\{configuration\-id\} |  | 

## Condition Keys for Amazon MQ<a name="amazonmq-policy-keys"></a>

MQ has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.