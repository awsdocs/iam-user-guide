# Actions, resources, and condition keys for AWS Import Export Disk Service<a name="list_awsimportexportdiskservice"></a>

AWS Import Export Disk Service \(service prefix: `importexport`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AWSImportExport/latest/DG/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AWSImportExport/latest/DG/api-reference.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AWSImportExport/latest/DG/using-iam.html) permission policies\.

**Topics**
+ [Actions defined by AWS Import Export Disk Service](#awsimportexportdiskservice-actions-as-permissions)
+ [Resource types defined by AWS Import Export Disk Service](#awsimportexportdiskservice-resources-for-iam-policies)
+ [Condition keys for AWS Import Export Disk Service](#awsimportexportdiskservice-policy-keys)

## Actions defined by AWS Import Export Disk Service<a name="awsimportexportdiskservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CancelJob ](https://docs.aws.amazon.com/AWSImportExport/latest/DG/WebCancelJob.html)  | This action cancels a specified job\. Only the job owner can cancel it\. The action fails if the job has already started or is complete\. | Write |  |  |  | 
|   [ CreateJob ](https://docs.aws.amazon.com/AWSImportExport/latest/DG/WebCreateJob.html)  | This action initiates the process of scheduling an upload or download of your data\. | Write |  |  |  | 
|   [ GetShippingLabel ](https://docs.aws.amazon.com/AWSImportExport/latest/DG/WebGetShippingLabel.html)  | This action generates a pre\-paid shipping label that you will use to ship your device to AWS for processing\. | Read |  |  |  | 
|   [ GetStatus ](https://docs.aws.amazon.com/AWSImportExport/latest/DG/WebGetStatus.html)  | This action returns information about a job, including where the job is in the processing pipeline, the status of the results, and the signature value associated with the job\. | Read |  |  |  | 
|   [ ListJobs ](https://docs.aws.amazon.com/AWSImportExport/latest/DG/WebListJobs.html)  | This action returns the jobs associated with the requester\. | List |  |  |  | 
|   [ UpdateJob ](https://docs.aws.amazon.com/AWSImportExport/latest/DG/WebUpdateJob.html)  | You use this action to change the parameters specified in the original manifest file by supplying a new manifest file\. | Write |  |  |  | 

## Resource types defined by AWS Import Export Disk Service<a name="awsimportexportdiskservice-resources-for-iam-policies"></a>

AWS Import Export Disk Service does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Import Export Disk Service, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS Import Export Disk Service<a name="awsimportexportdiskservice-policy-keys"></a>

Import/Export has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.