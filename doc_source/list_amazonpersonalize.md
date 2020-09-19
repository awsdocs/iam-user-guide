# Actions, resources, and condition keys for Amazon Personalize<a name="list_amazonpersonalize"></a>

Amazon Personalize \(service prefix: `personalize`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/personalize/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/personalize/latest/dg/API_Reference.html)\.

**Topics**
+ [Actions defined by Amazon Personalize](#amazonpersonalize-actions-as-permissions)
+ [Resource types defined by Amazon Personalize](#amazonpersonalize-resources-for-iam-policies)
+ [Condition keys for Amazon Personalize](#amazonpersonalize-policy-keys)

## Actions defined by Amazon Personalize<a name="amazonpersonalize-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateBatchInferenceJob ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateBatchInferenceJob.html)  | Creates a batch inference job | Write |   [ batchInferenceJob\* ](#amazonpersonalize-batchInferenceJob)   |  |  | 
|   [ CreateCampaign ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateCampaign.html)  | Creates a campaign | Write |   [ campaign\* ](#amazonpersonalize-campaign)   |  |  | 
|   [ CreateDataset ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateDataset.html)  | Creates a dataset | Write |   [ dataset\* ](#amazonpersonalize-dataset)   |  |  | 
|   [ CreateDatasetGroup ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateDatasetGroup.html)  | Creates a dataset group | Write |   [ datasetGroup\* ](#amazonpersonalize-datasetGroup)   |  |  | 
|   [ CreateDatasetImportJob ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateDatasetImportJob.html)  | Creates a dataset import job | Write |   [ datasetImportJob\* ](#amazonpersonalize-datasetImportJob)   |  |  | 
|   [ CreateEventTracker ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateEventTracker.html)  | Creates an event tracker | Write |   [ eventTracker\* ](#amazonpersonalize-eventTracker)   |  |  | 
|   [ CreateFilter ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateFilter.html)  | Creates a filter | Write |   [ filter\* ](#amazonpersonalize-filter)   |  |  | 
|   [ CreateSchema ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateSchema.html)  | Creates a schema | Write |   [ schema\* ](#amazonpersonalize-schema)   |  |  | 
|   [ CreateSolution ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateSolution.html)  | Creates a solution | Write |   [ solution\* ](#amazonpersonalize-solution)   |  |  | 
|   [ CreateSolutionVersion ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_CreateSolutionVersion.html)  | Creates a solution version | Write |   [ solution\* ](#amazonpersonalize-solution)   |  |  | 
|   [ DeleteCampaign ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DeleteCampaign.html)  | Deletes a campaign | Write |   [ campaign\* ](#amazonpersonalize-campaign)   |  |  | 
|   [ DeleteDataset ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DeleteDataset.html)  | Deletes a dataset | Write |   [ dataset\* ](#amazonpersonalize-dataset)   |  |  | 
|   [ DeleteDatasetGroup ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DeleteDatasetGroup.html)  | Deletes a dataset group | Write |   [ datasetGroup\* ](#amazonpersonalize-datasetGroup)   |  |  | 
|   [ DeleteEventTracker ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DeleteEventTracker.html)  | Deletes an event tracker | Write |   [ eventTracker\* ](#amazonpersonalize-eventTracker)   |  |  | 
|   [ DeleteFilter ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DeleteFilter.html)  | Deletes a filter | Write |   [ filter\* ](#amazonpersonalize-filter)   |  |  | 
|   [ DeleteSchema ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DeleteSchema.html)  | Deletes a schema | Write |   [ schema\* ](#amazonpersonalize-schema)   |  |  | 
|   [ DeleteSolution ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DeleteSolution.html)  | Deletes a solution including all versions of the solution | Write |   [ solution\* ](#amazonpersonalize-solution)   |  |  | 
|   [ DescribeAlgorithm ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeAlgorithm.html)  | Describes an algorithm | Read |   [ algorithm\* ](#amazonpersonalize-algorithm)   |  |  | 
|   [ DescribeBatchInferenceJob ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeBatchInferenceJob.html)  | Describes a batch inference job | Read |   [ batchInferenceJob\* ](#amazonpersonalize-batchInferenceJob)   |  |  | 
|   [ DescribeCampaign ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeCampaign.html)  | Describes a campaign | Read |   [ campaign\* ](#amazonpersonalize-campaign)   |  |  | 
|   [ DescribeDataset ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeDataset.html)  | Describes a dataset | Read |   [ dataset\* ](#amazonpersonalize-dataset)   |  |  | 
|   [ DescribeDatasetGroup ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeDatasetGroup.html)  | Describes a dataset group | Read |   [ datasetGroup\* ](#amazonpersonalize-datasetGroup)   |  |  | 
|   [ DescribeDatasetImportJob ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeDatasetImportJob.html)  | Describes a dataset import job | Read |   [ datasetImportJob\* ](#amazonpersonalize-datasetImportJob)   |  |  | 
|   [ DescribeEventTracker ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeEventTracker.html)  | Describes an event tracker | Read |   [ eventTracker\* ](#amazonpersonalize-eventTracker)   |  |  | 
|   [ DescribeFeatureTransformation ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeFeatureTransformation.html)  | Describes a feature transformation | Read |   [ featureTransformation\* ](#amazonpersonalize-featureTransformation)   |  |  | 
|   [ DescribeFilter ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeFilter.html)  | Describes a filter | Read |   [ filter\* ](#amazonpersonalize-filter)   |  |  | 
|   [ DescribeRecipe ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeRecipe.html)  | Describes a recipe | Read |   [ recipe\* ](#amazonpersonalize-recipe)   |  |  | 
|   [ DescribeSchema ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeSchema.html)  | Describes a schema | Read |   [ schema\* ](#amazonpersonalize-schema)   |  |  | 
|   [ DescribeSolution ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeSolution.html)  | Describes a solution | Read |   [ solution\* ](#amazonpersonalize-solution)   |  |  | 
|   [ DescribeSolutionVersion ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_DescribeSolutionVersion.html)  | Describes a version of a solution | Read |   [ solution\* ](#amazonpersonalize-solution)   |  |  | 
|   [ GetPersonalizedRanking ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_RS_GetPersonalizedRanking.html)  | Gets a re\-ranked list of recommendations | Write |   [ campaign\* ](#amazonpersonalize-campaign)   |  |  | 
|   [ GetRecommendations ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_RS_GetRecommendations.html)  | Gets a list of recommendations from a campaign | Read |   [ campaign\* ](#amazonpersonalize-campaign)   |  |  | 
|   [ GetSolutionMetrics ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_GetSolutionMetrics.html)  | Gets metrics for a solution version | Read |   [ solution\* ](#amazonpersonalize-solution)   |  |  | 
|   [ ListBatchInferenceJobs ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListBatchInferenceJobs.html)  | Lists batch inference jobs | List |  |  |  | 
|   [ ListCampaigns ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListCampaigns.html)  | Lists campaigns | List |  |  |  | 
|   [ ListDatasetGroups ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListDatasetGroups.html)  | Lists dataset groups | List |  |  |  | 
|   [ ListDatasetImportJobs ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListDatasetImportJobs.html)  | Lists dataset import jobs | List |  |  |  | 
|   [ ListDatasets ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListDatasets.html)  | Lists datasets | List |  |  |  | 
|   [ ListEventTrackers ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListEventTrackers.html)  | Lists event trackers | List |  |  |  | 
|   [ ListFilters ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListFilters.html)  | Lists filters | List |  |  |  | 
|   [ ListRecipes ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListRecipes.html)  | Lists recipes | List |  |  |  | 
|   [ ListSchemas ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListSchemas.html)  | Lists schemas | List |  |  |  | 
|   [ ListSolutionVersions ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListSolutionVersions.html)  | Lists versions of a solution | List |  |  |  | 
|   [ ListSolutions ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_ListSolutions.html)  | Lists solutions | List |  |  |  | 
|   [ PutEvents ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_UBS_PutEvents.html)  | Records real time event data | Write |   [ eventTracker\* ](#amazonpersonalize-eventTracker)   |  |  | 
|   [ UpdateCampaign ](https://docs.aws.amazon.com/personalize/latest/dg/API_Operations.htmlAPI_UpdateCampaign.html)  | Updates a campaign | Write |   [ campaign\* ](#amazonpersonalize-campaign)   |  |  | 

## Resource types defined by Amazon Personalize<a name="amazonpersonalize-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonpersonalize-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   schema  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:schema/$\{ResourceId\}  |  | 
|   featureTransformation  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:feature\-transformation/$\{ResourceId\}  |  | 
|   dataset  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:dataset/$\{ResourceId\}  |  | 
|   datasetGroup  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:dataset\-group/$\{ResourceId\}  |  | 
|   datasetImportJob  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:dataset\-import\-job/$\{ResourceId\}  |  | 
|   solution  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:solution/$\{ResourceId\}  |  | 
|   campaign  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:campaign/$\{ResourceId\}  |  | 
|   eventTracker  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:event\-tracker/$\{ResourceId\}  |  | 
|   recipe  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:recipe/$\{ResourceId\}  |  | 
|   algorithm  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:algorithm/$\{ResourceId\}  |  | 
|   batchInferenceJob  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:batch\-inference\-job/$\{ResourceId\}  |  | 
|   filter  |  arn:$\{Partition\}:personalize:$\{Region\}:$\{Account\}:filter/$\{ResourceId\}  |  | 

## Condition keys for Amazon Personalize<a name="amazonpersonalize-policy-keys"></a>

Personalize has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.