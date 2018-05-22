# Actions, Resources, and Condition Keys for Amazon Machine Learning<a name="list_amazonmachinelearning"></a>

Amazon Machine Learning \(service prefix: `machinelearning`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/machine-learning/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/machine-learning/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/machine-learning/latest/dg/controlling-access-to-amazon-ml-resources-by-using-iam.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Machine Learning](#amazonmachinelearning-actions-as-permissions)
+ [Resources Defined by Machine Learning](#amazonmachinelearning-resources-for-iam-policies)
+ [Condition Keys for Amazon Machine Learning](#amazonmachinelearning-policy-keys)

## Actions Defined by Amazon Machine Learning<a name="amazonmachinelearning-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonmachinelearning.html)

## Resources Defined by Machine Learning<a name="amazonmachinelearning-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonmachinelearning-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#batch-predictions](http://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#batch-predictions) | arn:$\{Partition\}:machinelearning:$\{Region\}:$\{Account\}:batchprediction/$\{BatchPredictionId\} |  | 
| [http://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#datasources](http://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#datasources) | arn:$\{Partition\}:machinelearning:$\{Region\}:$\{Account\}:datasource/$\{DatasourceId\} |  | 
| [http://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#evaluations](http://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#evaluations) | arn:$\{Partition\}:machinelearning:$\{Region\}:$\{Account\}:evaluation/$\{EvaluationId\} |  | 
| [http://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#ml-models](http://docs.aws.amazon.com/machine-learning/latest/dg/amazon-machine-learning-key-concepts.html#ml-models) | arn:$\{Partition\}:machinelearning:$\{Region\}:$\{Account\}:mlmodel/$\{MlModelId\} |  | 

## Condition Keys for Amazon Machine Learning<a name="amazonmachinelearning-policy-keys"></a>

Machine Learning has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.