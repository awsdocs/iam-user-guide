# Actions, resources, and condition keys for Amazon Machine Learning<a name="list_amazonmachinelearning"></a>

Amazon Machine Learning \(service prefix: `machinelearning`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/machine-learning/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/machine-learning/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/machine-learning/latest/dg/controlling-access-to-amazon-ml-resources-by-using-iam.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Machine Learning](#amazonmachinelearning-actions-as-permissions)
+ [Resource types defined by Amazon Machine Learning](#amazonmachinelearning-resources-for-iam-policies)
+ [Condition keys for Amazon Machine Learning](#amazonmachinelearning-policy-keys)

## Actions defined by Amazon Machine Learning<a name="amazonmachinelearning-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonmachinelearning.html)

## Resource types defined by Amazon Machine Learning<a name="amazonmachinelearning-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonmachinelearning-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ batchprediction ](https://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#batch-predictions)  |  arn:$\{Partition\}:machinelearning:$\{Region\}:$\{Account\}:batchprediction/$\{BatchPredictionId\}  |  | 
|   [ datasource ](https://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#datasources)  |  arn:$\{Partition\}:machinelearning:$\{Region\}:$\{Account\}:datasource/$\{DatasourceId\}  |  | 
|   [ evaluation ](https://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#evaluations)  |  arn:$\{Partition\}:machinelearning:$\{Region\}:$\{Account\}:evaluation/$\{EvaluationId\}  |  | 
|   [ mlmodel ](https://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#ml-models)  |  arn:$\{Partition\}:machinelearning:$\{Region\}:$\{Account\}:mlmodel/$\{MlModelId\}  |  | 

## Condition keys for Amazon Machine Learning<a name="amazonmachinelearning-policy-keys"></a>

Machine Learning has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.