# Actions, Resources, and Condition Keys for Amazon FreeRTOS<a name="list_amazonfreertos"></a>

Amazon FreeRTOS \(service prefix: `freertos`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/freertos/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/freertos/latest/userguide/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/freertos/latest/userguide/) permission policies\.

**Topics**
+ [Actions Defined by Amazon FreeRTOS](#amazonfreertos-actions-as-permissions)
+ [Resources Defined by FreeRTOS](#amazonfreertos-resources-for-iam-policies)
+ [Condition Keys for Amazon FreeRTOS](#amazonfreertos-policy-keys)

## Actions Defined by Amazon FreeRTOS<a name="amazonfreertos-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| CreateSoftwareConfiguration | Creates a software configuration\. | Write |  |  |  | 
| DeleteSoftwareConfiguration | Deletes the software configuration\. | Write |  |  |  | 
| DescribeHardwarePlatform | Describes the hardware platform\. | Read |  |  |  | 
| DescribeSoftwareConfiguration | Describes the software configuration\. | Read |  |  |  | 
| GetSoftwareURL | Get the URL for Amazon FreeRTOS software download\. | Read |  |  |  | 
| GetSoftwareURLForConfiguration | Get the URL for Amazon FreeRTOS software download based on the configuration\. | Read |  |  |  | 
| ListFreeRTOSVersions | Lists versions of AmazonFreeRTOS\. | List |  |  |  | 
| ListHardwarePlatforms | Lists the hardware platforms\. | List |  |  |  | 
| ListHardwareVendors | Lists the hardware vendors\. | List |  |  |  | 
| ListSoftwareConfigurations | Lists the software configurations\. | List |  |  |  | 
| UpdateSoftwareConfiguration | Updates the software configuration\. | Write |  |  |  | 

## Resources Defined by FreeRTOS<a name="amazonfreertos-resources-for-iam-policies"></a>

FreeRTOS has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon FreeRTOS<a name="amazonfreertos-policy-keys"></a>

FreeRTOS has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.