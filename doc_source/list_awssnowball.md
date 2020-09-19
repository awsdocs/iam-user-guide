# Actions, resources, and condition keys for AWS Snowball<a name="list_awssnowball"></a>

AWS Snowball \(service prefix: `snowball`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/snowball/latest/ug/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/snowball/latest/api-reference/)\.

**Topics**
+ [Actions defined by AWS Snowball](#awssnowball-actions-as-permissions)
+ [Resource types defined by AWS Snowball](#awssnowball-resources-for-iam-policies)
+ [Condition keys for AWS Snowball](#awssnowball-policy-keys)

## Actions defined by AWS Snowball<a name="awssnowball-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CancelCluster ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_CancelCluster.html)  | Cancels a cluster job\. | Write |  |  |  | 
|   [ CancelJob ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_CancelJob.html)  | Cancels the specified job\. | Write |  |  |  | 
|   [ CreateAddress ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_CreateAddress.html)  | Creates an address for a Snowball to be shipped to\. | Write |  |  |  | 
|   [ CreateCluster ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_CreateCluster.html)  | Creates an empty cluster\. | Write |  |  |  | 
|   [ CreateJob ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_CreateJob.html)  | Creates a job to import or export data between Amazon S3 and your on\-premises data center\. | Write |  |  |  | 
|   [ DescribeAddress ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_DescribeAddress.html)  | Takes an AddressId and returns specific details about that address in the form of an Address object\. | Read |  |  |  | 
|   [ DescribeAddresses ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_DescribeAddresses.html)  | Returns a specified number of ADDRESS objects\. | List |  |  |  | 
|   [ DescribeCluster ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_DescribeCluster.html)  | Returns information about a specific cluster including shipping information, cluster status, and other important metadata\. | Read |  |  |  | 
|   [ DescribeJob ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_DescribeJob.html)  | Returns information about a specific job including shipping information, job status, and other important metadata\. | Read |  |  |  | 
|   [ GetJobManifest ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_GetJobManifest.html)  | Returns a link to an Amazon S3 presigned URL for the manifest file associated with the specified JobId value\. | Read |  |  |  | 
|   [ GetJobUnlockCode ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_GetJobUnlockCode.html)  | Returns the UnlockCode code value for the specified job\. | Read |  |  |  | 
|   [ GetSnowballUsage ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_GetSnowballUsage.html)  | Returns information about the Snowball service limit for your account, and also the number of Snowballs your account has in use\. | Read |  |  |  | 
|   [ ListClusterJobs ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_ListClusterJobs.html)  | Returns an array of JobListEntry objects of the specified length\. | List |  |  |  | 
|   [ ListClusters ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_ListClusters.html)  | Returns an array of ClusterListEntry objects of the specified length\. | List |  |  |  | 
|   [ ListJobs ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_ListJobs.html)  | Returns an array of JobListEntry objects of the specified length\. | List |  |  |  | 
|   [ UpdateCluster ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_UpdateCluster.html)  | While a cluster's ClusterState value is in the AwaitingQuorum state, you can update some of the information associated with a cluster\. | Write |  |  |  | 
|   [ UpdateJob ](https://docs.aws.amazon.com/snowball/latest/api-reference/API_UpdateJob.html)  | While a job's JobState value is New, you can update some of the information associated with a job\. | Write |  |  |  | 

## Resource types defined by AWS Snowball<a name="awssnowball-resources-for-iam-policies"></a>

AWS Snowball does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Snowball, specify `“Resource”: “*”` in your policy\.

## Condition keys for AWS Snowball<a name="awssnowball-policy-keys"></a>

Snowball has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.