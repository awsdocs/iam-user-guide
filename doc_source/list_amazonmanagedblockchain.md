# Actions, resources, and condition keys for Amazon Managed Blockchain<a name="list_amazonmanagedblockchain"></a>

Amazon Managed Blockchain \(service prefix: `managedblockchain`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/managed-blockchain/latest/managementguide/) permission policies\.

**Topics**
+ [Actions defined by Amazon Managed Blockchain](#amazonmanagedblockchain-actions-as-permissions)
+ [Resource types defined by Amazon Managed Blockchain](#amazonmanagedblockchain-resources-for-iam-policies)
+ [Condition keys for Amazon Managed Blockchain](#amazonmanagedblockchain-policy-keys)

## Actions defined by Amazon Managed Blockchain<a name="amazonmanagedblockchain-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateMember ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_CreateMember.html)  | Grants permission to create a member of an Amazon Managed Blockchain network\. | Write |   [ network\* ](#amazonmanagedblockchain-network)   |  |  | 
|   [ CreateNetwork ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_CreateNetwork.html)  | Grants permission to create an Amazon Managed Blockchain network\. | Write |  |  |  | 
|   [ CreateNode ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_CreateNode.html)  | Grants permission to create a node within a member of an Amazon Managed Blockchain network\. | Write |   [ member\* ](#amazonmanagedblockchain-member)   |  |  | 
|   [ CreateProposal ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_CreateProposal.html)  | Grants permission to create a proposal that other blockchain network members can vote on to add or remove a member in an Amazon Managed Blockchain network\. | Write |   [ network\* ](#amazonmanagedblockchain-network)   |  |  | 
|   [ DeleteMember ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_DeleteMember.html)  | Grants permission to delete a member and all associated resources from an Amazon Managed Blockchain network\. | Write |   [ member\* ](#amazonmanagedblockchain-member)   |  |  | 
|   [ DeleteNode ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_DeleteNode.html)  | Grants permission to delete a node from a member of an Amazon Managed Blockchain network\. | Write |   [ node\* ](#amazonmanagedblockchain-node)   |  |  | 
|   [ GetMember ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_GetMember.html)  | Grants permission to return detailed information about a member of an Amazon Managed Blockchain network\. | Read |   [ member\* ](#amazonmanagedblockchain-member)   |  |  | 
|   [ GetNetwork ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_GetNetwork.html)  | Grants permission to return detailed information about an Amazon Managed Blockchain network\. | Read |   [ network\* ](#amazonmanagedblockchain-network)   |  |  | 
|   [ GetNode ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_GetNode.html)  | Grants permission to return detailed information about a node within a member of an Amazon Managed Blockchain network\. | Read |   [ node\* ](#amazonmanagedblockchain-node)   |  |  | 
|   [ GetProposal ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_GetProposal.html)  | Grants permission to return detailed information about a proposal of an Amazon Managed Blockchain network\. | Read |   [ proposal\* ](#amazonmanagedblockchain-proposal)   |  |  | 
|   [ ListInvitations ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_ListInvitations.html)  | Grants permission to list the invitations extended to the active AWS account from any Managed Blockchain network\. | List |  |  |  | 
|   [ ListMembers ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_ListMembers.html)  | Grants permission to list the members of an Amazon Managed Blockchain network and the properties of their memberships\. | List |   [ network\* ](#amazonmanagedblockchain-network)   |  |  | 
|   [ ListNetworks ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_ListNetworks.html)  | Grants permission to return information about the Amazon Managed Blockchain networks in which the current AWS account has members\. | List |  |  |  | 
|   [ ListNodes ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_ListNodes.html)  | Grants permission to list the nodes within a member of an Amazon Managed Blockchain network\. | List |   [ member\* ](#amazonmanagedblockchain-member)   |  |  | 
|   [ ListProposalVotes ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_ListProposalVotes.html)  | Grants permission to list all votes for a proposal, including the value of the vote and the unique identifier of the member that cast the vote for the given Amazon Managed Blockchain network\. | List |   [ proposal\* ](#amazonmanagedblockchain-proposal)   |  |  | 
|   [ ListProposals ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_ListProposals.html)  | Grants permission to list proposals for the given Amazon Managed Blockchain network\. | List |   [ network\* ](#amazonmanagedblockchain-network)   |  |  | 
|   [ RejectInvitation ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_RejectInvitation.html)  | Grants permission to reject the invitation to join the blockchain network\. | Write |   [ invitation\* ](#amazonmanagedblockchain-invitation)   |  |  | 
|   [ UpdateMember ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_UpdateMember.html)  | Grants permission to update a member of an Amazon Managed Blockchain network\. | Write |   [ member\* ](#amazonmanagedblockchain-member)   |  |   iam:CreateServiceLinkedRole   | 
|   [ UpdateNode ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_UpdateNode.html)  | Grants permission to update a node from a member of an Amazon Managed Blockchain network\. | Write |   [ node\* ](#amazonmanagedblockchain-node)   |  |   iam:CreateServiceLinkedRole   | 
|   [ VoteOnProposal ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_VoteOnProposal.html)  | Grants permission to cast a vote for a proposal on behalf of the blockchain network member specified\. | Write |   [ proposal\* ](#amazonmanagedblockchain-proposal)   |  |  | 

## Resource types defined by Amazon Managed Blockchain<a name="amazonmanagedblockchain-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonmanagedblockchain-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ network ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Network.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}::networks/$\{NetworkId\}  |  | 
|   [ member ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Member.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}:$\{Account\}:members/$\{MemberId\}  |  | 
|   [ node ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Node.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}:$\{Account\}:nodes/$\{NodeId\}  |  | 
|   [ proposal ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Proposal.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}::proposals/$\{ProposalId\}  |  | 
|   [ invitation ](https://docs.aws.amazon.com/managed-blockchain/latest/APIReference/API_Invitation.html)  |  arn:$\{Partition\}:managedblockchain:$\{Region\}:$\{Account\}:invitations/$\{InvitationId\}  |  | 

## Condition keys for Amazon Managed Blockchain<a name="amazonmanagedblockchain-policy-keys"></a>

Managed Blockchain has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.