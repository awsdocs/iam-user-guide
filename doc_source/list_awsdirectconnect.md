# Actions, Resources, and Condition Keys for AWS Direct Connect<a name="list_awsdirectconnect"></a>

AWS Direct Connect \(service prefix: `directconnect`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/directconnect/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/directconnect/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/directconnect/latest/UserGuide/using_iam.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Direct Connect](#awsdirectconnect-actions-as-permissions)
+ [Resources Defined by AWS Direct Connect](#awsdirectconnect-resources-for-iam-policies)
+ [Condition Keys for AWS Direct Connect](#awsdirectconnect-policy-keys)

## Actions Defined by AWS Direct Connect<a name="awsdirectconnect-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AllocateConnectionOnInterconnect ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_AllocateConnectionOnInterconnect.html)  | Creates a hosted connection on an interconnect\. | Write |  |  |  | 
|   [ AllocateHostedConnection ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_AllocateHostedConnection.html)  | Creates a new hosted connection between a AWS Direct Connect partner's network and a specific AWS Direct Connect location\. | Write |  |  |  | 
|   [ AllocatePrivateVirtualInterface ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_AllocatePrivateVirtualInterface.html)  | Provisions a private virtual interface to be owned by a different customer\. | Write |  |  |  | 
|   [ AllocatePublicVirtualInterface ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_AllocatePublicVirtualInterface.html)  | Provisions a public virtual interface to be owned by a different customer\. | Write |  |  |  | 
|   [ AssociateConnectionWithLag ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_AssociateConnectionWithLag.html)  | Associates a connection with a LAG\. | Write |  |  |  | 
|   [ AssociateHostedConnection ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_AssociateHostedConnection.html)  | Associates a hosted connection and its virtual interfaces with a link aggregation group \(LAG\) or interconnect\. | Write |  |  |  | 
|   [ AssociateVirtualInterface ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_AssociateVirtualInterface.html)  | Associates a virtual interface with a specified link aggregation group \(LAG\) or connection\. | Write |  |  |  | 
|   [ ConfirmConnection ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_ConfirmConnection.html)  | Confirm the creation of a hosted connection on an interconnect\. | Read |  |  |  | 
|   [ ConfirmPrivateVirtualInterface ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_ConfirmPrivateVirtualInterface.html)  | Accept ownership of a private virtual interface created by another customer\. | Read |  |  |  | 
|   [ ConfirmPublicVirtualInterface ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_ConfirmPublicVirtualInterface.html)  | Accept ownership of a public virtual interface created by another customer | Read |  |  |  | 
|   [ CreateBGPPeer ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreateBGPPeer.html)  | Creates a BGP peer on the specified virtual interface\. | Write |  |  |  | 
|   [ CreateConnection ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreateConnection.html)  | Creates a new connection between the customer network and a specific AWS Direct Connect location\. | Write |  |  |  | 
|   [ CreateDirectConnectGateway ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreateDirectConnectGateway.html)  | Creates a Direct Connect gateway, which is an intermediate object that enables you to connect a set of virtual interfaces and virtual private gateways\. | Write |  |  |  | 
|   [ CreateDirectConnectGatewayAssociation ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreateDirectConnectGatewayAssociation.html)  | Creates an association between a Direct Connect gateway and a virtual private gateway\. | Write |  |  |  | 
|   [ CreateInterconnect ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreateInterconnect.html)  | Creates a new interconnect between a AWS Direct Connect partner's network and a specific AWS Direct Connect location\. | Write |  |  |  | 
|   [ CreateLag ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreateLag.html)  | Creates a link aggregation group \(LAG\) with the specified number of bundled physical connections between the customer network and a specific AWS Direct Connect location\. | Write |  |  |  | 
|   [ CreatePrivateVirtualInterface ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreatePrivateVirtualInterface.html)  | Creates a new private virtual interface\. | Write |  |  |  | 
|   [ CreatePublicVirtualInterface ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_CreatePublicVirtualInterface.html)  | Creates a new public virtual interface\. | Write |  |  |  | 
|   [ DeleteBGPPeer ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteBGPPeer.html)  | Deletes the specified BGP peer on the specified virtual interface with the specified customer address and ASN\. | Write |  |  |  | 
|   [ DeleteConnection ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteConnection.html)  | Deletes the connection\. | Write |  |  |  | 
|   [ DeleteDirectConnectGateway ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteDirectConnectGateway.html)  | Deletes the specified Direct Connect gateway\. | Write |  |  |  | 
|   [ DeleteDirectConnectGatewayAssociation ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteDirectConnectGatewayAssociation.html)  | Deletes the association between the specified Direct Connect gateway and virtual private gateway\. | Write |  |  |  | 
|   [ DeleteInterconnect ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteInterconnect.html)  | Deletes the specified interconnect\. | Write |  |  |  | 
|   [ DeleteLag ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteLag.html)  | Deletes the specified link aggregation group \(LAG\)\. | Write |  |  |  | 
|   [ DeleteVirtualInterface ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DeleteVirtualInterface.html)  | Deletes a virtual interface\. | Write |  |  |  | 
|   [ DescribeConnectionLoa ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeConnectionLoa.html)  | Returns the LOA\-CFA for a Connection\. | Read |  |  |  | 
|   [ DescribeConnections ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeConnections.html)  | Displays all connections in this region\. | Read |  |  |  | 
|   [ DescribeConnectionsOnInterconnect ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeConnectionsOnInterconnect.html)  | Return a list of connections that have been provisioned on the given interconnect\. | Read |  |  |  | 
|   [ DescribeDirectConnectGatewayAssociations ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeDirectConnectGatewayAssociations.html)  | Lists the associations between your Direct Connect gateways and virtual private gateways\. | Read |  |  |  | 
|   [ DescribeDirectConnectGatewayAttachments ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeDirectConnectGatewayAttachments.html)  | Lists the attachments between your Direct Connect gateways and virtual interfaces\. | Read |  |  |  | 
|   [ DescribeDirectConnectGateways ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeDirectConnectGateways.html)  | Lists all your Direct Connect gateways or only the specified Direct Connect gateway\. | Read |  |  |  | 
|   [ DescribeHostedConnections ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeHostedConnections.html)  | Lists the hosted connections that have been provisioned on the specified interconnect or link aggregation group \(LAG\)\. | Read |  |  |  | 
|   [ DescribeInterconnectLoa ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeInterconnectLoa.html)  | Returns the LOA\-CFA for an Interconnect\. | Read |  |  |  | 
|   [ DescribeInterconnects ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeInterconnects.html)  | Returns a list of interconnects owned by the AWS account\. | Read |  |  |  | 
|   [ DescribeLags ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeLags.html)  | Describes all your link aggregation groups \(LAG\) or the specified LAG\. | Read |  |  |  | 
|   [ DescribeLoa ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeLoa.html)  | Gets the LOA\-CFA for a connection, interconnect, or link aggregation group \(LAG\)\. | Read |  |  |  | 
|   [ DescribeLocations ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeLocations.html)  | Returns the list of AWS Direct Connect locations in the current AWS region\. | Read |  |  |  | 
|   [ DescribeTags ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeTags.html)  | Describes the tags associated with the specified AWS Direct Connect resources\. | Read |  |  |  | 
|   [ DescribeVirtualGateways ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeVirtualGateways.html)  | Returns a list of virtual private gateways owned by the AWS account\. | Read |  |  |  | 
|   [ DescribeVirtualInterfaces ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DescribeVirtualInterfaces.html)  | Displays all virtual interfaces for an AWS account\. | Read |  |  |  | 
|   [ DisassociateConnectionFromLag ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_DisassociateConnectionFromLag.html)  | Disassociates a connection from a link aggregation group \(LAG\)\. | Read |  |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_TagResource.html)  | Adds the specified tags to the specified AWS Direct Connect resource\. Each resource can have a maximum of 50 tags\. | Read |  |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_UntagResource.html)  | Removes one or more tags from the specified AWS Direct Connect resource\. | Read |  |  |  | 
|   [ UpdateLag ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_UpdateLag.html)  | Updates the attributes of the specified link aggregation group \(LAG\)\. | Read |  |  |  | 
|   [ UpdateVirtualInterfaceAttributes ](https://docs.aws.amazon.com/directconnect/latest/APIReference/API_UpdateVirtualInterfaceAttributes.html)  | Updates the specified attributes of the specified virtual private interface\. | Read |  |  |  | 

## Resources Defined by AWS Direct Connect<a name="awsdirectconnect-resources-for-iam-policies"></a>

AWS Direct Connect has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Direct Connect<a name="awsdirectconnect-policy-keys"></a>

Direct Connect has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.