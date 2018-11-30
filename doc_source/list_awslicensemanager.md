# Actions, Resources, and Condition Keys for AWS License Manager<a name="list_awslicensemanager"></a>

AWS License Manager \(service prefix: `license-manager`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/license-manager/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/license-manager/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/license-manager/latest/userguide/using-service-linked-roles.html) permission policies\.

**Topics**
+ [Actions Defined by AWS License Manager](#awslicensemanager-actions-as-permissions)
+ [Resources Defined by License Manager](#awslicensemanager-resources-for-iam-policies)
+ [Condition Keys for AWS License Manager](#awslicensemanager-policy-keys)

## Actions Defined by AWS License Manager<a name="awslicensemanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateLicenseConfiguration ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_CreateLicenseConfiguration.html)  | Creates a new license configuration | Tagging |  |  |  | 
|   [ DeleteLicenseConfiguration ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_DeleteLicenseConfiguration.html)  | Permanently deletes a license configuration | Write |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ GetLicenseConfiguration ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_GetLicenseConfiguration.html)  | Gets a license configuration | List |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ GetServiceSettings ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_GetServiceSettings.html)  | Gets service settings | List |  |  |  | 
|   [ ListAssociationsForLicenseConfiguration ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_ListAssociationsForLicenseConfiguration.html)  | Lists associations for a selected license configuration | List |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ ListLicenseConfigurations ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_ListLicenseConfigurations.html)  | Lists license configurations | List |  |  |  | 
|   [ ListLicenseSpecificationsForResource ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_ListLicenseSpecificationsForResource.html)  | Lists license specifications associated with a selected resource | List |  |  |  | 
|   [ ListResourceInventory ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_ListResourceInventory.html)  | Lists resource inventory | List |  |  |  | 
|   [ ListTagsForResource ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_ListTagsForResource.html)  | Lists tags for a selected resource | List |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ ListUsageForLicenseConfiguration ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_ListUsageForLicenseConfiguration.html)  | Lists usage records for selected license configuration | List |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_TagResource.html)  | Tags a selected resource | Tagging |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_UntagResource.html)  | Untags a selected resource | Tagging |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ UpdateLicenseConfiguration ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_UpdateLicenseConfiguration.html)  | Updates an existing license configuration | Write |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ UpdateLicenseSpecificationsForResource ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_UpdateLicenseSpecificationsForResource.html)  | Updates license specifications for a selected resource | Write |   [ license\-configuration\* ](#awslicensemanager-license-configuration)   |  |  | 
|   [ UpdateServiceSettings ](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_UpdateServiceSettings.html)  | Updates service settings | Permissions management |  |  |  | 

## Resources Defined by License Manager<a name="awslicensemanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awslicensemanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   license\-configuration  |  arn:$\{Partition\}:license\-manager:$\{Region\}:$\{Account\}:license\-configuration/$\{LicenseConfigurationId\}  |  | 

## Condition Keys for AWS License Manager<a name="awslicensemanager-policy-keys"></a>

AWS License Manager defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   aws:TagKeys  | Enforce tag keys that are used in the request | String | 