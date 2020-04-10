# Actions, Resources, and Condition Keys for AWS DeepComposer<a name="list_awsdeepcomposer"></a>

AWS DeepComposer \(service prefix: `deepcomposer`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/latest/devguide/get-started.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/latest/devguide/get-started.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/latest/devguide/get-started.html) permission policies\.

**Topics**
+ [Actions Defined by AWS DeepComposer](#awsdeepcomposer-actions-as-permissions)
+ [Resource Types Defined by AWS DeepComposer](#awsdeepcomposer-resources-for-iam-policies)
+ [Condition Keys for AWS DeepComposer](#awsdeepcomposer-policy-keys)

## Actions Defined by AWS DeepComposer<a name="awsdeepcomposer-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   AssociateCoupon \[permission only\] | Associates a DeepComposer coupon \(or DSN\) with the account associated with the sender of the request\. | Write |  |  |  | 
|   [ CreateAudio ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html) \[permission only\] | Creates an audio file by converting the midi composition into a wav or mp3 file\. | Write |   [ composition\* ](#awsdeepcomposer-composition)   |  |  | 
|   [ CreateComposition ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html) \[permission only\] | Creates a multi\-track midi composition\. | Write |  |  |  | 
|   [ CreateModel ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-train-custom-model.html) \[permission only\] | Starts creating/training a generative\-model that is able to perform inference against the user\-provided piano\-melody to create a multi\-track midi composition\. | Write |  |  |  | 
|   [ DeleteComposition ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html) \[permission only\] | Deletes the composition\. | Write |   [ composition\* ](#awsdeepcomposer-composition)   |  |  | 
|   [ DeleteModel ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-train-custom-model.html)  | Deletes the model\. | Write |   [ model\* ](#awsdeepcomposer-model)   |  |  | 
|   [ GetComposition ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html) \[permission only\] | Returns information about the composition\. | Read |   [ composition\* ](#awsdeepcomposer-composition)   |  |  | 
|   [ GetModel ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-train-custom-model.html) \[permission only\] | Returns information about the model\. | Read |   [ model\* ](#awsdeepcomposer-model)   |  |  | 
|   [ GetSampleModel ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html) \[permission only\] | Returns information about the sample/pre\-trained DeepComposer model\. | Read |  |  |  | 
|   [ ListCompositions ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html) \[permission only\] | Returns a list of all the compositions owned by the sender of the request\. | List |  |  |  | 
|   [ ListModels ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-train-custom-model.html) \[permission only\] | Returns a list of all the models owned by the sender of the request\. | List |  |  |  | 
|   [ ListSampleModels ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html) \[permission only\] | Returns a list of all the sample/pre\-trained models provided by the DeepComposer service\. | List |  |  |  | 
|   ListTrainingTopics \[permission only\] | Returns a list of all the training options or topic for creating/training a model\. | List |  |  |  | 
|   [ UpdateComposition ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html) \[permission only\] | Modifies the mutable properties associated with a composition\. | Write |   [ composition\* ](#awsdeepcomposer-composition)   |  |  | 
|   [ UpdateModel ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-train-custom-model.html) \[permission only\] | Modifies the mutable properties associated with a model\. | Write |   [ model\* ](#awsdeepcomposer-model)   |  |  | 

## Resource Types Defined by AWS DeepComposer<a name="awsdeepcomposer-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsdeepcomposer-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ model ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-train-custom-model.html)  |  arn:$\{Partition\}:deepcomposer:$\{Region\}:$\{Account\}:model/$\{ModelId\}  |  | 
|   [ composition ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html)  |  arn:$\{Partition\}:deepcomposer:$\{Region\}:$\{Account\}:composition/$\{CompositionId\}  |  | 
|   [ audio ](https://docs.aws.amazon.com/latest/devguide/get-started.htmlget-started-compose-with-trained-model.html)  |  arn:$\{Partition\}:deepcomposer:$\{Region\}:$\{Account\}:audio/$\{AudioId\}  |  | 

## Condition Keys for AWS DeepComposer<a name="awsdeepcomposer-policy-keys"></a>

DeepComposer has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.