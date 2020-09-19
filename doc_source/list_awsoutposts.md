# Actions, resources, and condition keys for AWS Outposts<a name="list_awsoutposts"></a>

AWS Outposts \(service prefix: `outposts`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/outposts/latest/userguide/get-started-outposts.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/outposts/latest/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/outposts/latest/identity-access-management.html) permission policies\.

**Topics**
+ [Actions defined by AWS Outposts](#awsoutposts-actions-as-permissions)
+ [Resource types defined by AWS Outposts](#awsoutposts-resources-for-iam-policies)
+ [Condition keys for AWS Outposts](#awsoutposts-policy-keys)

## Actions defined by AWS Outposts<a name="awsoutposts-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateOutpost ](https://docs.aws.amazon.com/outposts/latest/APIReference/API_CreateOutpost.html)  | Creates an Outpost | Write |  |  |  | 
|   [ GetOutpost ](https://docs.aws.amazon.com/outposts/latest/APIReference/API_GetOutpost.html)  | Gets information about the specified Outpost | Read |  |  |  | 
|   [ GetOutpostInstanceTypes ](https://docs.aws.amazon.com/outposts/latest/APIReference/API_GetOutpostInstanceTypes.html)  | Lists the instance types for the specified Outpost | Read |  |  |  | 
|   [ ListOutposts ](https://docs.aws.amazon.com/outposts/latest/APIReference/API_ListOutposts.html)  | List the Outposts for your AWS account | List |  |  |  | 
|   [ ListSites ](https://docs.aws.amazon.com/outposts/latest/APIReference/API_ListSites.html)  | Lists the sites for the specified AWS account | List |  |  |  | 

## Resource types defined by AWS Outposts<a name="awsoutposts-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsoutposts-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ Outpost ](https://docs.aws.amazon.com/outposts/latest/APIReference/API_Outpost.html)  |  arn:$\{Partition\}:outposts:$\{Region\}:$\{Account\}:outpost/$\{OutpostId\}  |  | 
|   [ Site ](https://docs.aws.amazon.com/outposts/latest/APIReference/API_Site.html)  |  arn:$\{Partition\}:outposts:$\{Region\}:$\{Account\}:site/$\{SiteId\}  |  | 
|   [ Order ](https://docs.aws.amazon.com/outposts/latest/APIReference/Welcome.html)  |  arn:$\{Partition\}:outposts:$\{Region\}:$\{Account\}:order/$\{OrderId\}  |  | 

## Condition keys for AWS Outposts<a name="awsoutposts-policy-keys"></a>

Outposts has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.