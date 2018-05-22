# Actions, Resources, and Condition Keys for Alexa for Business<a name="list_alexaforbusiness"></a>

Alexa for Business \(service prefix: `a4b`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by Alexa for Business](#alexaforbusiness-actions-as-permissions)
+ [Resources Defined by Alexa for Business](#alexaforbusiness-resources-for-iam-policies)
+ [Condition Keys for Alexa for Business](#alexaforbusiness-policy-keys)

## Actions Defined by Alexa for Business<a name="alexaforbusiness-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_alexaforbusiness.html)

## Resources Defined by Alexa for Business<a name="alexaforbusiness-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#alexaforbusiness-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| device | arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:device/$\{Resource\_id\} |  | 
| profile | arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:profile/$\{Resource\_id\} |  | 
| room | arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:room/$\{Resource\_id\} |  | 
| skillgroup | arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:skill\-group/$\{Resource\_id\} |  | 
| user | arn:$\{Partition\}:a4b:$\{Region\}:$\{Account\}:user/$\{Resource\_id\} |  | 

## Condition Keys for Alexa for Business<a name="alexaforbusiness-policy-keys"></a>

Alexa for Business has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.