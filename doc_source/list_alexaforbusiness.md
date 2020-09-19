# Actions, resources, and condition keys for Alexa for Business<a name="list_alexaforbusiness"></a>

Alexa for Business \(service prefix: `a4b`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/a4b/latest/APIReference/)\.

**Topics**
+ [Actions defined by Alexa for Business](#alexaforbusiness-actions-as-permissions)
+ [Resource types defined by Alexa for Business](#alexaforbusiness-resources-for-iam-policies)
+ [Condition keys for Alexa for Business](#alexaforbusiness-policy-keys)

## Actions defined by Alexa for Business<a name="alexaforbusiness-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_alexaforbusiness.html)

## Resource types defined by Alexa for Business<a name="alexaforbusiness-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#alexaforbusiness-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ profile ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_Profile.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:profile/$\{Resource\_id\}  |  | 
|   [ room ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_Room.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:room/$\{Resource\_id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#alexaforbusiness-aws_ResourceTag___TagKey_)   | 
|   [ device ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_Device.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:device/$\{Resource\_id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#alexaforbusiness-aws_ResourceTag___TagKey_)   | 
|   [ skillgroup ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_SkillGroup.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:skill\-group/$\{Resource\_id\}  |  | 
|   [ user ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_UserData.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:user/$\{Resource\_id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#alexaforbusiness-aws_ResourceTag___TagKey_)   | 
|   [ addressbook ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_AddressBook.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:address\-book/$\{Resource\_id\}  |  | 
|   [ conferenceprovider ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_ConferenceProvider.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:conference\-provider/$\{Resource\_id\}  |  | 
|   [ contact ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_Contact.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:contact/$\{Resource\_id\}  |  | 
|   [ schedule ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_BusinessReportSchedule.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:schedule/$\{Resource\_id\}  |  | 
|   [ networkprofile ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_NetworkProfile.html)  |  arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:network\-profile/$\{Resource\_id\}  |  | 

## Condition keys for Alexa for Business<a name="alexaforbusiness-policy-keys"></a>

Alexa for Business defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ a4b:amazonId ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_RegisterAVSDevice.html)  | Filters actions based on the Amazon Id in the request | String | 
|   [ a4b:filters\_deviceType ](https://docs.aws.amazon.com/a4b/latest/APIReference/API_SearchDevices.html)  | Filters actions based on the device type in the request | String | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the allowed set of values for each of the tags | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag\-value assoicated with the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of mandatory tags in the request | String | 