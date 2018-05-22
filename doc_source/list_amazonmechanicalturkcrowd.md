# Actions, Resources, and Condition Keys for Amazon Mechanical Turk Crowd<a name="list_amazonmechanicalturkcrowd"></a>

Amazon Mechanical Turk Crowd \(service prefix: `crowd`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMechanicalTurkRequester/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/)\.
+ Learn how to protect this service and its resources by [using IAM]() permission policies\.

**Topics**
+ [Actions Defined by Amazon Mechanical Turk Crowd](#amazonmechanicalturkcrowd-actions-as-permissions)
+ [Resources Defined by Mechanical Turk Crowd](#amazonmechanicalturkcrowd-resources-for-iam-policies)
+ [Condition Keys for Amazon Mechanical Turk Crowd](#amazonmechanicalturkcrowd-policy-keys)

## Actions Defined by Amazon Mechanical Turk Crowd<a name="amazonmechanicalturkcrowd-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.

The following are not actual APIs, they are permissions that allow access to Mechanical Turk operations\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| GetTask | Retrieve information about the specified task | Read | [task\*](#amazonmechanicalturkcrowd-task)  |  |  | 
| PutTask | Create or update a task\. | Write | [task\*](#amazonmechanicalturkcrowd-task)  |  |  | 

## Resources Defined by Mechanical Turk Crowd<a name="amazonmechanicalturkcrowd-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonmechanicalturkcrowd-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| task | arn:$\{Partition\}:crowd:$\{Region\}:$\{Account\}:task/$\{FunctionName\}/$\{TaskName\} |  | 

## Condition Keys for Amazon Mechanical Turk Crowd<a name="amazonmechanicalturkcrowd-policy-keys"></a>

Mechanical Turk Crowd has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.