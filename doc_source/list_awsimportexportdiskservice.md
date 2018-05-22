# Actions, Resources, and Condition Keys for AWS Import Export Disk Service<a name="list_awsimportexportdiskservice"></a>

AWS Import Export Disk Service \(service prefix: `importexport`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AWSImportExport/latest/DG/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AWSImportExport/latest/DG/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AWSImportExport/latest/DG/using-iam.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Import Export Disk Service](#awsimportexportdiskservice-actions-as-permissions)
+ [Resources Defined by Import/Export](#awsimportexportdiskservice-resources-for-iam-policies)
+ [Condition Keys for AWS Import Export Disk Service](#awsimportexportdiskservice-policy-keys)

## Actions Defined by AWS Import Export Disk Service<a name="awsimportexportdiskservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebCancelJob.html](http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebCancelJob.html) | This action cancels a specified job\. Only the job owner can cancel it\. The action fails if the job has already started or is complete\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebCreateJob.html](http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebCreateJob.html) | This action initiates the process of scheduling an upload or download of your data\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebGetShippingLabel.html](http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebGetShippingLabel.html) | This action generates a pre\-paid shipping label that you will use to ship your device to AWS for processing\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebGetStatus.html](http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebGetStatus.html) | This action returns information about a job, including where the job is in the processing pipeline, the status of the results, and the signature value associated with the job\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebListJobs.html](http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebListJobs.html) | This action returns the jobs associated with the requester\. | List |  |  |  | 
| [http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebUpdateJob.html](http://docs.aws.amazon.com/AWSImportExport/latest/DG/WebUpdateJob.html) | You use this action to change the parameters specified in the original manifest file by supplying a new manifest file\. | Write |  |  |  | 

## Resources Defined by Import/Export<a name="awsimportexportdiskservice-resources-for-iam-policies"></a>

Import/Export has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Import Export Disk Service<a name="awsimportexportdiskservice-policy-keys"></a>

Import/Export has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.