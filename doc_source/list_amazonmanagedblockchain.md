# Actions, Resources, and Condition Keys for Amazon Managed Blockchain<a name="list_amazonmanagedblockchain"></a>

Amazon Managed Blockchain \(service prefix: `managedblockchain`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/) permission policies\.

**Topics**
+ [Actions Defined by Amazon Managed Blockchain](#amazonmanagedblockchain-actions-as-permissions)
+ [Resources Defined by Managed Blockchain](#amazonmanagedblockchain-resources-for-iam-policies)
+ [Condition Keys for Amazon Managed Blockchain](#amazonmanagedblockchain-policy-keys)

## Actions Defined by Amazon Managed Blockchain<a name="amazonmanagedblockchain-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonmanagedblockchain.html)

## Resources Defined by Managed Blockchain<a name="amazonmanagedblockchain-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonmanagedblockchain-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ network ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Network.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}:$\{Account\}:network/$\{NetworkId\}  |  | 
|   [ member ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Member.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}:$\{Account\}:member/$\{NetworkId\}/$\{MemberId\}  |  | 
|   [ node ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Node.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}:$\{Account\}:node/$\{NetworkId\}/$\{MemberId\}/$\{NodeId\}  |  | 
|   [ proposal ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Proposal.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}:$\{Account\}:networks/$\{NetworkId\}/$\{ProposalId\}  |  | 
|   [ invitation ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Invitation.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}:$\{Account\}:invitations/$\{InvitationId\}  |  | 

## Condition Keys for Amazon Managed Blockchain<a name="amazonmanagedblockchain-policy-keys"></a>

Managed Blockchain has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.