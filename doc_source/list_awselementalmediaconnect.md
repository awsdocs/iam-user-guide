# Actions, resources, and condition keys for AWS Elemental MediaConnect<a name="list_awselementalmediaconnect"></a>

AWS Elemental MediaConnect \(service prefix: `mediaconnect`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/mediaconnect/latest/ug/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/mediaconnect/latest/api/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/mediaconnect/latest/ug/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by AWS Elemental MediaConnect](#awselementalmediaconnect-actions-as-permissions)
+ [Resource types defined by AWS Elemental MediaConnect](#awselementalmediaconnect-resources-for-iam-policies)
+ [Condition keys for AWS Elemental MediaConnect](#awselementalmediaconnect-policy-keys)

## Actions defined by AWS Elemental MediaConnect<a name="awselementalmediaconnect-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddFlowOutputs ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn-outputs.html)  | Grants permission to add outputs to any flow\. | Write |  |  |  | 
|   [ CreateFlow ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows.html)  | Grants permission to create flows\. | Write |  |  |  | 
|   [ DeleteFlow ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn.html)  | Grants permission to delete flows\. | Write |  |  |  | 
|   [ DescribeFlow ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn.html)  | Grants permission to display the details of a flow including the flow ARN, name, and Availability Zone, as well as details about the source, outputs, and entitlements\. | Read |  |  |  | 
|   [ GrantFlowEntitlements ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn-entitlements.html)  | Grants permission to grant entitlements on any flow\. | Write |  |  |  | 
|   [ ListEntitlements ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-entitlements.html)  | Grants permission to display a list of all entitlements that have been granted to the account\. | List |  |  |  | 
|   [ ListFlows ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows.html)  | Grants permission to display a list of flows that are associated with this account\. | List |  |  |  | 
|   [ RemoveFlowOutput ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn-outputs-outputarn.html)  | Grants permission to remove outputs from any flow\. | Write |  |  |  | 
|   [ RevokeFlowEntitlement ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn-entitlements-entitlementarn.html)  | Grants permission to revoke entitlements on any flow\. | Write |  |  |  | 
|   [ StartFlow ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-start-flowarn.html)  | Grants permission to start flows\. | Write |  |  |  | 
|   [ StopFlow ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-stop-flowarn.html)  | Grants permission to stop flows\. | Write |  |  |  | 
|   [ UpdateFlowEntitlement ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn-entitlements-entitlementarn.html)  | Grants permission to update entitlements on any flow\. | Write |  |  |  | 
|   [ UpdateFlowOutput ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn-outputs-outputarn.html)  | Grants permission to update outputs on any flow\. | Write |  |  |  | 
|   [ UpdateFlowSource ](https://docs.aws.amazon.com/mediaconnect/latest/api/v1-flows-flowarn-source-sourcearn.html)  | Grants permission to update the source of any flow\. | Write |  |  |  | 

## Resource types defined by AWS Elemental MediaConnect<a name="awselementalmediaconnect-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awselementalmediaconnect-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ Entitlement ](https://docs.aws.amazon.com/mediaconnect/latest/ug/entitlements.html)  |  arn:$\{Partition\}:mediaconnect:$\{Region\}:$\{Account\}:entitlement:$\{FlowId\}:$\{EntitlementName\}  |  | 
|   [ Flow ](https://docs.aws.amazon.com/mediaconnect/latest/ug/flows.html)  |  arn:$\{Partition\}:mediaconnect:$\{Region\}:$\{Account\}:flow:$\{FlowId\}:$\{FlowName\}  |  | 
|   [ Output ](https://docs.aws.amazon.com/mediaconnect/latest/ug/outputs.html)  |  arn:$\{Partition\}:mediaconnect:$\{Region\}:$\{Account\}:output:$\{OutputId\}:$\{OutputName\}  |  | 
|   [ Source ](https://docs.aws.amazon.com/mediaconnect/latest/ug/sources.html)  |  arn:$\{Partition\}:mediaconnect:$\{Region\}:$\{Account\}:source:$\{SourceId\}:$\{SourceName\}  |  | 

## Condition keys for AWS Elemental MediaConnect<a name="awselementalmediaconnect-policy-keys"></a>

MediaConnect has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.