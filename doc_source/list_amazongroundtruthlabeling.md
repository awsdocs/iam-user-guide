# Actions, Resources, and Condition Keys for Amazon GroundTruth Labeling<a name="list_amazongroundtruthlabeling"></a>

Amazon GroundTruth Labeling \(service prefix: `groundtruthlabeling`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/)\.

**Topics**
+ [Actions Defined by Amazon GroundTruth Labeling](#amazongroundtruthlabeling-actions-as-permissions)
+ [Resources Defined by Amazon GroundTruth Labeling](#amazongroundtruthlabeling-resources-for-iam-policies)
+ [Condition Keys for Amazon GroundTruth Labeling](#amazongroundtruthlabeling-policy-keys)

## Actions Defined by Amazon GroundTruth Labeling<a name="amazongroundtruthlabeling-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DescribeConsoleJob ](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/API_DescribeConsoleJob.html) \[permission only\] | Get status of GroundTruthLabeling Jobs | Read |  |  |  | 
|   [ ListDatasetObjects ](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/API_ListDatasetObjects.html) \[permission only\] | Paginated list api to list dataset objects in a manifest file | Read |  |  |  | 
|   [ RunFilterOrSampleDatasetJob ](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/API_RunFilterOrSampleDatasetJob.html) \[permission only\] | Filter records from a manifest file using S3 select\. Get Sample entries based on random sampling\. | Write |  |  |  | 
|   [ RunGenerateManifestByCrawlingJob ](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/API_RunGenerateManifestByCrawlingJob.html) \[permission only\] | List a S3 prefix and create manifest files from objects in there\. | Write |  |  |  | 

## Resources Defined by Amazon GroundTruth Labeling<a name="amazongroundtruthlabeling-resources-for-iam-policies"></a>

Amazon GroundTruth Labeling has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon GroundTruth Labeling<a name="amazongroundtruthlabeling-policy-keys"></a>

GroundTruth Labeling has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.