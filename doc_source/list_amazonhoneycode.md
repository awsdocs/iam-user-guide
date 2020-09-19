# Actions, resources, and condition keys for Amazon Honeycode<a name="list_amazonhoneycode"></a>

Amazon Honeycode \(service prefix: `honeycode`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/honeycode/latest/UserGuide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/honeycode/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/honeycode/latest/UserGuide/getting-started-authorization.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Honeycode](#amazonhoneycode-actions-as-permissions)
+ [Resource types defined by Amazon Honeycode](#amazonhoneycode-resources-for-iam-policies)
+ [Condition keys for Amazon Honeycode](#amazonhoneycode-policy-keys)

## Actions defined by Amazon Honeycode<a name="amazonhoneycode-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ ApproveTeamAssociation ](https://docs.aws.amazon.com/honeycode/latest/UserGuide/team-association.html#approve-team-association) \[permission only\] | Grants permission to approve a team association request for your AWS Account | Write |  |  |  | 
|   [ GetScreenData ](https://docs.aws.amazon.com/honeycode/latest/UserGuide/API_GetScreenData.html)  | Grants permission to load the data from a screen | Read |   [ screen\* ](#amazonhoneycode-screen)   |  |  | 
|   [ InvokeScreenAutomation ](https://docs.aws.amazon.com/honeycode/latest/UserGuide/API_InvokeScreenAutomation.html)  | Grants permission to invoke a screen automation | Write |   [ screen\-automation\* ](#amazonhoneycode-screen-automation)   |  |  | 
|   [ ListTeamAssociations ](https://docs.aws.amazon.com/honeycode/latest/UserGuide/team-association.html#list-team-associations) \[permission only\] | Grants permission to list all pending and approved team associations with your AWS Account | List |  |  |  | 
|   [ RejectTeamAssociation ](https://docs.aws.amazon.com/honeycode/latest/UserGuide/team-association.html#reject-team-association) \[permission only\] | Grants permission to reject a team association request for your AWS Account | Write |  |  |  | 

## Resource types defined by Amazon Honeycode<a name="amazonhoneycode-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonhoneycode-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ screen ](https://docs.aws.amazon.com/honeycode/latest/UserGuide/resource-screen.html)  |  arn:$\{Partition\}:honeycode:$\{Region\}:$\{Account\}:screen:workbook/$\{WorkbookId\}/app/$\{AppId\}/screen/$\{ScreenId\}  |  | 
|   [ screen\-automation ](https://docs.aws.amazon.com/honeycode/latest/UserGuide/resource-screen-automation.html)  |  arn:$\{Partition\}:honeycode:$\{Region\}:$\{Account\}:screen\-automation:workbook/$\{WorkbookId\}/app/$\{AppId\}/screen/$\{ScreenId\}/automation/$\{AutomationId\}  |  | 

## Condition keys for Amazon Honeycode<a name="amazonhoneycode-policy-keys"></a>

Honeycode has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.