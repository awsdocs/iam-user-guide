# Actions, Resources, and Condition Keys for Amazon GroundTruth Labeling<a name="list_amazongroundtruthlabeling"></a>

Amazon GroundTruth Labeling \(service prefix: `groundtruthlabeling`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/)\.

**Topics**
+ [Actions Defined by Amazon GroundTruth Labeling](#amazongroundtruthlabeling-actions-as-permissions)
+ [Resources Defined by GroundTruth Labeling](#amazongroundtruthlabeling-resources-for-iam-policies)
+ [Condition Keys for Amazon GroundTruth Labeling](#amazongroundtruthlabeling-policy-keys)

## Actions Defined by Amazon GroundTruth Labeling<a name="amazongroundtruthlabeling-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DescribeConsoleJob ](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/API_DescribeConsoleJob.html)  | Get status of GroundTruthLabeling Jobs | Read |  |  |  | 
|   [ ListDatasetObjects ](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/API_ListDatasetObjects.html)  | Paginated list api to list dataset objects in a manifest file | Read |  |  |  | 
|   [ RunFilterOrSampleDatasetJob ](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/API_RunFilterOrSampleDatasetJob.html)  | Filter records from a manifest file using S3 select\. Get Sample entries based on random sampling\. | Write |  |  |  | 
|   [ RunGenerateManifestByCrawlingJob ](https://docs.aws.amazon.com/groundtruthlabeling/latest/APIReference/API_RunGenerateManifestByCrawlingJob.html)  | List a S3 prefix and create manifest files from objects in there\. | Write |  |  |  | 

## Resources Defined by GroundTruth Labeling<a name="amazongroundtruthlabeling-resources-for-iam-policies"></a>

Amazon GroundTruth Labeling has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon GroundTruth Labeling<a name="amazongroundtruthlabeling-policy-keys"></a>

GroundTruth Labeling has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.