# Actions, Resources, and Condition Keys for Amazon Message Delivery Service<a name="list_amazonmessagedeliveryservice"></a>

Amazon Message Delivery Service \(service prefix: `ec2messages`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by Amazon Message Delivery Service](#amazonmessagedeliveryservice-actions-as-permissions)
+ [Resource Types Defined by Amazon Message Delivery Service](#amazonmessagedeliveryservice-resources-for-iam-policies)
+ [Condition Keys for Amazon Message Delivery Service](#amazonmessagedeliveryservice-policy-keys)

## Actions Defined by Amazon Message Delivery Service<a name="amazonmessagedeliveryservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   AcknowledgeMessage  | Acknowledges a message, ensuring it will not be delivered again | Write |  |  |  | 
|   DeleteMessage  | Deletes a message | Write |  |  |  | 
|   FailMessage  | Fails a message, signifying the message could not be processed successfully, ensuring it cannot be replied to or delivered again | Write |  |  |  | 
|   GetEndpoint  | Routes traffic to the correct endpoint based on the given destination for the messages | Read |  |  |  | 
|   GetMessages  | Delivers messages to clients/instances using long polling | Read |  |  |  | 
|   SendReply  | Sends replies from clients/instances to upstream service | Write |  |  |  | 

## Resource Types Defined by Amazon Message Delivery Service<a name="amazonmessagedeliveryservice-resources-for-iam-policies"></a>

Amazon Message Delivery Service does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Message Delivery Service, specify `“Resource”: “*”` in your policy\.

## Condition Keys for Amazon Message Delivery Service<a name="amazonmessagedeliveryservice-policy-keys"></a>

EC2 Messages has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.