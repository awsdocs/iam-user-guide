# Actions, resources, and condition keys for Amazon Rekognition<a name="list_amazonrekognition"></a>

Amazon Rekognition \(service prefix: `rekognition`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/rekognition/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/rekognition/latest/dg/API_Reference.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/rekognition/latest/dg/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Rekognition](#amazonrekognition-actions-as-permissions)
+ [Resource types defined by Amazon Rekognition](#amazonrekognition-resources-for-iam-policies)
+ [Condition keys for Amazon Rekognition](#amazonrekognition-policy-keys)

## Actions defined by Amazon Rekognition<a name="amazonrekognition-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonrekognition.html)

## Resource types defined by Amazon Rekognition<a name="amazonrekognition-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonrekognition-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ collection ](https://docs.aws.amazon.com/rekognition/latest/dg/howitworks-collection.html)  |  arn:$\{Partition\}:rekognition:$\{Region\}:$\{Account\}:collection/$\{CollectionId\}  |  | 
|   streamprocessor  |  arn:$\{Partition\}:rekognition:$\{Region\}:$\{Account\}:streamprocessor/$\{StreamprocessorId\}  |  | 
|   project  |  arn:$\{Partition\}:rekognition:$\{Region\}:$\{Account\}:project/$\{ProjectName\}/$\{CreationTimestamp\}  |  | 
|   projectversion  |  arn:$\{Partition\}:rekognition:$\{Region\}:$\{Account\}:project/$\{ProjectName\}/version/$\{VersionName\}/$\{CreationTimestamp\}  |  | 

## Condition keys for Amazon Rekognition<a name="amazonrekognition-policy-keys"></a>

Rekognition has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.