# Actions, Resources, and Condition Keys for Amazon Fraud Detector<a name="list_amazonfrauddetector"></a>

Amazon Fraud Detector \(service prefix: `frauddetector`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/frauddetector/latest/ug/what-is-frauddetector.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/frauddetector/latest/api/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/IAM/xxx/UserGuide/assets.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Fraud Detector](#amazonfrauddetector-actions-as-permissions)
+ [Resource Types Defined by Amazon Fraud Detector](#amazonfrauddetector-resources-for-iam-policies)
+ [Condition Keys for Amazon Fraud Detector](#amazonfrauddetector-policy-keys)

## Actions Defined by Amazon Fraud Detector<a name="amazonfrauddetector-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchCreateVariable ](https://docs.aws.amazon.com/frauddetector/latest/api/API_BatchCreateVariable)  | Creates a batch of variables\. | Write |  |  |  | 
|   [ BatchGetVariable ](https://docs.aws.amazon.com/frauddetector/latest/api/API_BatchGetVariable)  | Gets a batch of variables\. | List |  |  |  | 
|   [ CreateDetectorVersion ](https://docs.aws.amazon.com/frauddetector/latest/api/API_CreateDetectorVersion)  | Creates a detector version\. The detector version starts in a DRAFT status\. | Write |  |  |  | 
|   [ CreateModelVersion ](https://docs.aws.amazon.com/frauddetector/latest/api/API_CreateModelVersion)  | Creates a version of the model using the specified model type\. | Write |  |  |  | 
|   [ CreateRule ](https://docs.aws.amazon.com/frauddetector/latest/api/API_CreateRule.html)  | Creates a rule for use with the specified detector\. | Write |  |  |  | 
|   [ CreateVariable ](https://docs.aws.amazon.com/frauddetector/latest/api/API_CreateVariable.html)  | Creates a variable\. | Write |  |  |  | 
|   [ DeleteDetectorVersion ](https://docs.aws.amazon.com/frauddetector/latest/api/API_DeleteDetectorVersion)  | Deletes the detector version\. | Write |  |  |  | 
|   [ DeleteEvent ](https://docs.aws.amazon.com/frauddetector/latest/api/API_DeleteEvent)  | Deletes the specified event\. | Write |  |  |  | 
|   [ DescribeDetector ](https://docs.aws.amazon.com/frauddetector/latest/api/API_DescribeDetector)  | Gets all versions for a specified detector\. | Read |  |  |  | 
|   [ DescribeModelVersions ](https://docs.aws.amazon.com/frauddetector/latest/api/API_DescribeModelVersions)  | Gets all of the model versions for the specified model type or for the specified model type and model ID\. You can also get details for a single, specified model version\. | Read |  |  |  | 
|   [ GetDetectorVersion ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetDetectorVersion)  | Gets a particular detector version\. | List |  |  |  | 
|   [ GetDetectors ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetDetectors)  | Gets all of detectors\. This is a paginated API\. If you provide a null maxSizePerPage, this actions retrieves a maximum of 10 records per page\. If you provide a maxSizePerPage, the value must be between 5 and 10\. To get the next page results, provide the pagination token from the GetEventTypesResponse as part of your request\. A null pagination token fetches the records from the beginning\. | List |  |  |  | 
|   [ GetExternalModels ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetExternalModels)  | Gets the details for one or more Amazon SageMaker models that have been imported into the service\. This is a paginated API\. If you provide a null maxSizePerPage, this actions retrieves a maximum of 10 records per page\. If you provide a maxSizePerPage, the value must be between 5 and 10\. To get the next page results, provide the pagination token from the GetExternalModelsResult as part of your request\. A null pagination token fetches the records from the beginning\. | List |  |  |  | 
|   [ GetModelVersion ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetModelVersion)  | Gets a model version\. | List |  |  |  | 
|   [ GetModels ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetModels)  | Gets all of the models for the AWS account, or the specified model type, or gets a single model for the specified model type, model ID combination\. | List |  |  |  | 
|   [ GetOutcomes ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetOutcomes)  | Gets one or more outcomes\. This is a paginated API\. If you provide a null maxSizePerPage, this actions retrieves a maximum of 10 records per page\. If you provide a maxSizePerPage, the value must be between 50 and 100\. To get the next page results, provide the pagination token from the GetOutcomesResult as part of your request\. A null pagination token fetches the records from the beginning\. | List |  |  |  | 
|   [ GetPrediction ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetPrediction)  | Evaluates an event against a detector version\. If a version ID is not provided, the detector’s \(ACTIVE\) version is used\. | Read |  |  |  | 
|   [ GetRules ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetRules.html)  | Gets all rules available for the specified detector\. | List |  |  |  | 
|   [ GetVariables ](https://docs.aws.amazon.com/frauddetector/latest/api/API_GetVariables)  | Gets all of the variables or the specific variable\. This is a paginated API\. Providing null maxSizePerPage results in retrieving maximum of 100 records per page\. If you provide maxSizePerPage the value must be between 50 and 100\. To get the next page result, a provide a pagination token from GetVariablesResult as part of your request\. Null pagination token fetches the records from the beginning\. | List |  |  |  | 
|   [ PutDetector ](https://docs.aws.amazon.com/frauddetector/latest/api/API_PutDetector.html)  | Creates or updates a detector\. | Write |  |  |  | 
|   [ PutExternalModel ](https://docs.aws.amazon.com/frauddetector/latest/api/API_PutExternalModel.html)  | Creates or updates an Amazon SageMaker model endpoint\. You can also use this action to update the configuration of the model endpoint, including the IAM role and/or the mapped variables\. | Write |  |  |  | 
|   [ PutModel ](https://docs.aws.amazon.com/frauddetector/latest/api/API_PutModel)  | Creates or updates a model\. | Write |  |  |   iam:PassRole   | 
|   [ PutOutcome ](https://docs.aws.amazon.com/frauddetector/latest/api/API_PutOutcome.html)  | Creates or updates an outcome\. | Write |  |  |  | 
|   [ UpdateDetectorVersion ](https://docs.aws.amazon.com/frauddetector/latest/api/API_UpdateDetectorVersion)  | Updates a detector version\. The detector version attributes that you can update include models, external model endpoints, rules, and description\. You can only update a DRAFT detector version\. | Write |  |  |  | 
|   [ UpdateDetectorVersionMetadata ](https://docs.aws.amazon.com/frauddetector/latest/api/API_UpdateDetectorVersionMetadata)  | Updates the detector version's description\. You can update the metadata for any detector version \(DRAFT, ACTIVE, or INACTIVE\)\. | Write |  |  |  | 
|   [ UpdateDetectorVersionStatus ](https://docs.aws.amazon.com/frauddetector/latest/api/API_UpdateDetectorVersionStatus)  | Updates the detector version’s status\. You can perform the following promotions or demotions using UpdateDetectorVersionStatus: DRAFT to ACTIVE, ACTIVE to INACTIVE, and INACTIVE to ACTIVE\. | Write |  |  |  | 
|   [ UpdateModelVersion ](https://docs.aws.amazon.com/frauddetector/latest/api/API_UpdateModelVersion)  | Updates a model version\. You can update the description and status attributes using this action\. | Write |  |  |  | 
|   [ UpdateRuleMetadata ](https://docs.aws.amazon.com/frauddetector/latest/api/API_UpdateRuleMetadata.html)  | Updates a rule's metadata\. | Write |  |  |  | 
|   [ UpdateRuleVersion ](https://docs.aws.amazon.com/frauddetector/latest/api/API_UpdateRuleVersion.html)  | Updates a rule version resulting in a new rule version\. | Write |  |  |  | 
|   [ UpdateVariable ](https://docs.aws.amazon.com/frauddetector/latest/api/API_UpdateVariable.html)  | Updates a variable\. | Write |  |  |  | 

## Resource Types Defined by Amazon Fraud Detector<a name="amazonfrauddetector-resources-for-iam-policies"></a>

Amazon Fraud Detector does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Fraud Detector, specify `“Resource”: “*”` in your policy\.

## Condition Keys for Amazon Fraud Detector<a name="amazonfrauddetector-policy-keys"></a>

Fraud Detector has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.