# Actions, resources, and condition keys for Amazon Detective<a name="list_amazondetective"></a>

Amazon Detective \(service prefix: `detective`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/detective/latest/adminguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/detective/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/detective/latest/adminguide/security_iam_service-with-iam.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Detective](#amazondetective-actions-as-permissions)
+ [Resource types defined by Amazon Detective](#amazondetective-resources-for-iam-policies)
+ [Condition keys for Amazon Detective](#amazondetective-policy-keys)

## Actions defined by Amazon Detective<a name="amazondetective-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AcceptInvitation ](https://docs.aws.amazon.com/detective/latest/APIReference/API_AcceptInvitation.html)  | Grants permission to accept an invitation to become a member of a behavior graph | Write |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   [ CreateGraph ](https://docs.aws.amazon.com/detective/latest/APIReference/API_CreateGraph.html)  | Grants permission to create a behavior graph and begin to aggregate security information | Write |  |  |  | 
|   [ CreateMembers ](https://docs.aws.amazon.com/detective/latest/APIReference/API_CreateMembers.html)  | Grants permission to request the membership of one or more accounts in a behavior graph managed by this account | Write |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   [ DeleteGraph ](https://docs.aws.amazon.com/detective/latest/APIReference/API_DeleteGraph.html)  | Grants permission to delete a behavior graph and stop aggregating security information | Write |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   [ DeleteMembers ](https://docs.aws.amazon.com/detective/latest/APIReference/API_DeleteMembers.html)  | Grants permission to remove member accounts from a behavior graph managed by this account | Write |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   [ DisassociateMembership ](https://docs.aws.amazon.com/detective/latest/APIReference/API_DisassociateMembership.html)  | Grants permission to remove the association of this account with a behavior graph | Write |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   GetFreeTrialEligibility \[permission only\] | Grants permission to retrieve a behavior graph's eligibility for a free trial period | Read |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   GetGraphIngestState \[permission only\] | Grants permission to retrieve the data ingestion state of a behavior graph | Read |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   [ GetMembers ](https://docs.aws.amazon.com/detective/latest/APIReference/API_GetMembers.html)  | Grants permission to retrieve details on specified members of a behavior graph | Read |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   GetPricingInformation \[permission only\] | Grants permission to retrieve information about Amazon Detective's pricing | Read |  |  |  | 
|   GetUsageInformation \[permission only\] | Grants permission to list usage information of a behavior graph | Read |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   [ ListGraphs ](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html)  | Grants permission to list behavior graphs managed by this account | List |  |  |  | 
|   [ ListInvitations ](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListInvitations.html)  | Grants permission to retrieve details on the behavior graphs to which this account has been invited to join | List |  |  |  | 
|   [ ListMembers ](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListMembers.html)  | Grants permission to retrieve details on all members of a behavior graph | List |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   [ RejectInvitation ](https://docs.aws.amazon.com/detective/latest/APIReference/API_RejectInvitation.html)  | Grants permission to reject an invitation to become a member of a behavior graph | Write |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   SearchGraph \[permission only\] | Grants permission to search the data stored in a behavior graph | Read |   [ Graph\* ](#amazondetective-Graph)   |  |  | 
|   [ StartMonitoringMember ](https://docs.aws.amazon.com/detective/latest/APIReference/API_StartMonitoringMember.html)  | Grants permission to start data ingest for a member account that has a status of ACCEPTED\_BUT\_DISABLED\. | Write |   [ Graph\* ](#amazondetective-Graph)   |  |  | 

## Resource types defined by Amazon Detective<a name="amazondetective-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazondetective-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ Graph ](https://docs.aws.amazon.com/detective/latest/adminguide/security_iam_service-with-iam.html#security_iam_service-with-iam-id-based-policies-resources)  |  arn:$\{Partition\}:detective:$\{Region\}:$\{Account\}:graph:$\{ResourceId\}  |  | 

## Condition keys for Amazon Detective<a name="amazondetective-policy-keys"></a>

Detective has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.