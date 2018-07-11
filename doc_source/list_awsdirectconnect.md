# Actions, Resources, and Condition Keys for AWS Direct Connect<a name="list_awsdirectconnect"></a>

AWS Direct Connect \(service prefix: `directconnect`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/directconnect/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/directconnect/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/directconnect/latest/UserGuide/using_iam.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Direct Connect](#awsdirectconnect-actions-as-permissions)
+ [Resources Defined by Direct Connect](#awsdirectconnect-resources-for-iam-policies)
+ [Condition Keys for AWS Direct Connect](#awsdirectconnect-policy-keys)

## Actions Defined by AWS Direct Connect<a name="awsdirectconnect-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AllocateConnectionOnInterconnect ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_AllocateConnectionOnInterconnect.html)  | Creates a hosted connection on an interconnect\. | Write |  |  |  | 
|   [ AllocatePrivateVirtualInterface ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_AllocatePrivateVirtualInterface.html)  | Provisions a private virtual interface to be owned by a different customer\. | Write |  |  |  | 
|   [ AllocatePublicVirtualInterface ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_AllocatePublicVirtualInterface.html)  | Provisions a public virtual interface to be owned by a different customer\. | Write |  |  |  | 
|   [ ConfirmConnection ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_ConfirmConnection.html)  | Confirm the creation of a hosted connection on an interconnect\. | Read |  |  |  | 
|   [ ConfirmPrivateVirtualInterface ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_ConfirmPrivateVirtualInterface.html)  | Accept ownership of a private virtual interface created by another customer\. | Read |  |  |  | 
|   [ ConfirmPublicVirtualInterface ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_ConfirmPublicVirtualInterface.html)  | Accept ownership of a public virtual interface created by another customer | Read |  |  |  | 
|   [ CreateConnection ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreateConnection.html)  | Creates a new connection between the customer network and a specific AWS Direct Connect location\. | Write |  |  |  | 
|   [ CreateInterconnect ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreateInterconnect.html)  | Creates a new interconnect between a AWS Direct Connect partner's network and a specific AWS Direct Connect location\. | Write |  |  |  | 
|   [ CreatePrivateVirtualInterface ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreatePrivateVirtualInterface.html)  | Creates a new private virtual interface\. | Write |  |  |  | 
|   [ CreatePublicVirtualInterface ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreatePublicVirtualInterface.html)  | Creates a new public virtual interface\. | Write |  |  |  | 
|   [ DeleteConnection ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteConnection.html)  | Deletes the connection\. | Write |  |  |  | 
|   [ DeleteInterconnect ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteInterconnect.html)  | Deletes the specified interconnect\. | Write |  |  |  | 
|   [ DeleteVirtualInterface ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteVirtualInterface.html)  | Deletes a virtual interface\. | Write |  |  |  | 
|   [ DescribeConnectionLoa ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeConnectionLoa.html)  | Returns the LOA\-CFA for a Connection\. | List |  |  |  | 
|   [ DescribeConnections ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeConnections.html)  | Displays all connections in this region\. | List |  |  |  | 
|   [ DescribeConnectionsOnInterconnect ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeConnectionsOnInterconnect.html)  | Return a list of connections that have been provisioned on the given interconnect\. | List |  |  |  | 
|   [ DescribeInterconnectLoa ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeInterconnectLoa.html)  | Returns the LOA\-CFA for an Interconnect\. | List |  |  |  | 
|   [ DescribeInterconnects ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeInterconnects.html)  | Returns a list of interconnects owned by the AWS account\. | List |  |  |  | 
|   [ DescribeLocations ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeLocations.html)  | Returns the list of AWS Direct Connect locations in the current AWS region\. | List |  |  |  | 
|   [ DescribeVirtualGateways ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeVirtualGateways.html)  | Returns a list of virtual private gateways owned by the AWS account\. | List |  |  |  | 
|   [ DescribeVirtualInterfaces ](http://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeVirtualInterfaces.html)  | Displays all virtual interfaces for an AWS account\. | List |  |  |  | 

## Resources Defined by Direct Connect<a name="awsdirectconnect-resources-for-iam-policies"></a>

AWS Direct Connect has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Direct Connect<a name="awsdirectconnect-policy-keys"></a>

Direct Connect has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.