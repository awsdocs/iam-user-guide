# Actions, Resources, and Condition Keys for Amazon Cognito Sync<a name="list_amazoncognitosync"></a>

Amazon Cognito Sync \(service prefix: `cognito-sync`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/cognito/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/cognitosync/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/cognito/latest/developerguide/resource-permissions.html#amazon-cognito-amazon-resource-names) permission policies\.

**Topics**
+ [Actions Defined by Amazon Cognito Sync](#amazoncognitosync-actions-as-permissions)
+ [Resources Defined by Cognito Sync](#amazoncognitosync-resources-for-iam-policies)
+ [Condition Keys for Amazon Cognito Sync](#amazoncognitosync-policy-keys)

## Actions Defined by Amazon Cognito Sync<a name="amazoncognitosync-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BulkPublish ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_BulkPublish.html)  | Initiates a bulk publish of all existing datasets for an Identity Pool to the configured stream\. | Write |   [ identitypool\* ](#amazoncognitosync-identitypool)   |  |  | 
|   [ DeleteDataset ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_DeleteDataset.html)  | Deletes the specific dataset\. | Write |   [ dataset\* ](#amazoncognitosync-dataset)   |  |  | 
|   [ DescribeDataset ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_DescribeDataset.html)  | Gets meta data about a dataset by identity and dataset name\. | Read |   [ dataset\* ](#amazoncognitosync-dataset)   |  |  | 
|   [ DescribeIdentityPoolUsage ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_DescribeIdentityPoolUsage.html)  | Gets usage details \(for example, data storage\) about a particular identity pool\. | Read |   [ identitypool\* ](#amazoncognitosync-identitypool)   |  |  | 
|   [ DescribeIdentityUsage ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_DescribeIdentityUsage.html)  | Gets usage information for an identity, including number of datasets and data usage\. | Read |   [ identity\* ](#amazoncognitosync-identity)   |  |  | 
|   [ GetBulkPublishDetails ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_GetBulkPublishDetails.html)  | Get the status of the last BulkPublish operation for an identity pool\. | Read |   [ identitypool\* ](#amazoncognitosync-identitypool)   |  |  | 
|   [ GetCognitoEvents ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_GetCognitoEvents.html)  | Gets the events and the corresponding Lambda functions associated with an identity pool\. | Read |   [ identitypool\* ](#amazoncognitosync-identitypool)   |  |  | 
|   [ GetIdentityPoolConfiguration ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_GetIdentityPoolConfiguration.html)  | Gets the configuration settings of an identity pool\. | Read |   [ identitypool\* ](#amazoncognitosync-identitypool)   |  |  | 
|   [ ListDatasets ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_ListDatasets.html)  | Lists datasets for an identity\. | List |   [ dataset\* ](#amazoncognitosync-dataset)   |  |  | 
|   [ ListIdentityPoolUsage ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_ListIdentityPoolUsage.html)  | Gets a list of identity pools registered with Cognito\. | Read |   [ identitypool\* ](#amazoncognitosync-identitypool)   |  |  | 
|   [ ListRecords ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_ListRecords.html)  | Gets paginated records, optionally changed after a particular sync count for a dataset and identity\. | Read |   [ dataset\* ](#amazoncognitosync-dataset)   |  |  | 
|   QueryRecords \[permission only\] | A permission that grants the ability to query records\. | Read |  |  |  | 
|   [ RegisterDevice ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_RegisterDevice.html)  | Registers a device to receive push sync notifications\. | Write |   [ identity\* ](#amazoncognitosync-identity)   |  |  | 
|   [ SetCognitoEvents ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_SetCognitoEvents.html)  | Sets the AWS Lambda function for a given event type for an identity pool\. | Write |   [ identitypool\* ](#amazoncognitosync-identitypool)   |  |  | 
|   SetDatasetConfiguration \[permission only\] | A permission that grants ability to configure datasets\. | Write |   [ dataset\* ](#amazoncognitosync-dataset)   |  |  | 
|   [ SetIdentityPoolConfiguration ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_SetIdentityPoolConfiguration.html)  | Sets the necessary configuration for push sync\. | Write |   [ identitypool\* ](#amazoncognitosync-identitypool)   |  |  | 
|   [ SubscribeToDataset ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_SubscribeToDataset.html)  | Subscribes to receive notifications when a dataset is modified by another device\. | Write |   [ dataset\* ](#amazoncognitosync-dataset)   |  |  | 
|   [ UnsubscribeFromDataset ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_UnsubscribeFromDataset.html)  | Unsubscribes from receiving notifications when a dataset is modified by another device\. | Write |   [ dataset\* ](#amazoncognitosync-dataset)   |  |  | 
|   [ UpdateRecords ](http://docs.aws.amazon.com/cognitosync/latest/APIReference/API_UpdateRecords.html)  | Posts updates to records and adds and deletes records for a dataset and user\. | Write |   [ dataset\* ](#amazoncognitosync-dataset)   |  |  | 

## Resources Defined by Cognito Sync<a name="amazoncognitosync-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncognitosync-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ dataset ](http://docs.aws.amazon.com/cognito/latest/developerguide/synchronizing-data.html#understanding-datasets)  |  arn:$\{Partition\}:cognito\-sync:$\{Region\}:$\{Account\}:identitypool/$\{IdentityPoolId\}/identity/$\{IdentityId\}/dataset/$\{DatasetName\}  |  | 
|   [ identity ](http://docs.aws.amazon.com/cognito/latest/developerguide/identity-pools.html#authenticated-and-unauthenticated-identities)  |  arn:$\{Partition\}:cognito\-sync:$\{Region\}:$\{Account\}:identitypool/$\{IdentityPoolId\}/identity/$\{IdentityId\}  |  | 
|   [ identitypool ](http://docs.aws.amazon.com/cognito/latest/developerguide/identity-pools.html)  |  arn:$\{Partition\}:cognito\-sync:$\{Region\}:$\{Account\}:identitypool/$\{IdentityPoolId\}  |  | 

## Condition Keys for Amazon Cognito Sync<a name="amazoncognitosync-policy-keys"></a>

Cognito Sync has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.