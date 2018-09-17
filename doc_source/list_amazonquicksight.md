# Actions, Resources, and Condition Keys for Amazon QuickSight<a name="list_amazonquicksight"></a>

Amazon QuickSight \(service prefix: `quicksight`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/quicksight/latest/user/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/quicksight/latest/user/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/quicksight/latest/user/working-with-iam.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon QuickSight](#amazonquicksight-actions-as-permissions)
+ [Resources Defined by QuickSight](#amazonquicksight-resources-for-iam-policies)
+ [Condition Keys for Amazon QuickSight](#amazonquicksight-policy-keys)

## Actions Defined by Amazon QuickSight<a name="amazonquicksight-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateAdmin ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | CreateAdmin enables the user to provision Amazon QuickSight administrators, authors, and readers\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ CreateReader ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | CreateReader enables the user to provision Amazon QuickSight readers\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ CreateUser ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | CreateUser enables the user to provision Amazon QuickSight authors and readers\. | Write |   [ user\* ](#amazonquicksight-user)   |  |  | 
|   [ GetGroupMapping ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | GetGroupMapping is used only in Amazon QuickSight Enterprise edition accounts\. It enables the user to use Amazon QuickSight to identify and display the Microsoft Active Directory \(Microsoft Active Directory\) directory groups that are mapped to roles in Amazon QuickSight\. | Write |  |  |  | 
|   [ SearchDirectoryGroups ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | SearchDirectoryGroups is used only in Amazon QuickSight Enterprise edition accounts\. It enables the user to use Amazon QuickSight to display your Microsoft Active Directory directory groups so that you can choose which ones to map to roles in Amazon QuickSight\. | Write |  |  |  | 
|   [ SetGroupMapping ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | SearchDirectoryGroups is used only in Amazon QuickSight Enterprise edition accounts\. It enables the user to use Amazon QuickSight to display your Microsoft Active Directory directory groups so that you can choose which ones to map to roles in Amazon QuickSight\. | Write |  |  |  | 
|   [ Subscribe ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | Subscribe enables the user to subscribe to Amazon QuickSight\. Enabling this action also allows the user to upgrade the subscription to Enterprise edition\. | Write |  |  |  | 
|   [ Unsubscribe ](https://docs.aws.amazon.com/quicksight/latest/user/iam-actions.html) \[permission only\] | Unsubscribe enables the user to unsubscribe from Amazon QuickSight, which permanently deletes all users and their resources from Amazon QuickSight\. | Write |  |  |  | 

## Resources Defined by QuickSight<a name="amazonquicksight-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonquicksight-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   user  |  arn:$\{Partition\}:quicksight::$\{Account\}:user/$\{ResourceId\}  |  | 

## Condition Keys for Amazon QuickSight<a name="amazonquicksight-policy-keys"></a>

QuickSight has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.