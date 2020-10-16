# Actions, resources, and condition keys for Amazon S3 on Outposts<a name="list_amazons3onoutposts"></a>

**Tip**  
This page is moving to a new location on November 16, 2020\. Please update your bookmark to use the new page at [https://docs\.aws\.amazon\.com/service\-authorization/latest/reference/list\_amazons3onoutposts\.html](https://docs.aws.amazon.com/service-authorization/latest/reference/list_amazons3onoutposts.html)\. 

Amazon S3 on Outposts \(service prefix: `s3-outposts`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AmazonS3/latest/API/Type_API_Reference.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-control-overview.html) permission policies\.

**Topics**
+ [Actions defined by Amazon S3 on Outposts](#amazons3onoutposts-actions-as-permissions)
+ [Resource types defined by Amazon S3 on Outposts](#amazons3onoutposts-resources-for-iam-policies)
+ [Condition keys for Amazon S3 on Outposts](#amazons3onoutposts-policy-keys)

## Actions defined by Amazon S3 on Outposts<a name="amazons3onoutposts-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazons3onoutposts.html)

## Resource types defined by Amazon S3 on Outposts<a name="amazons3onoutposts-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazons3onoutposts-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ accesspoint ](https://docs.aws.amazon.com/AmazonS3/latest/dev/access-points.html)  |  arn:$\{Partition\}:s3\-outposts:$\{Region\}:$\{Account\}:outpost/$\{OutpostId\}/accesspoint/$\{AccessPointName\}  |  | 
|   [ bucket ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html)  |  arn:$\{Partition\}:s3\-outposts:$\{Region\}:$\{Account\}:outpost/$\{OutpostId\}/bucket/$\{BucketName\}  |  | 
|   [ endpoint ](https://docs.aws.amazon.com/AmazonS3/latest/dev/outposts-endpoints.html)  |  arn:$\{Partition\}:s3\-outposts:$\{Region\}:$\{Account\}:outpost/$\{OutpostId\}/endpoint/$\{EndpointId\}  |  | 
|   [ object ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingObjects.html)  |  arn:$\{Partition\}:s3\-outposts:$\{Region\}:$\{Account\}:outpost/$\{OutpostId\}/bucket/$\{BucketName\}/object/$\{ObjectName\}  |  | 

## Condition keys for Amazon S3 on Outposts<a name="amazons3onoutposts-policy-keys"></a>

Amazon S3 on Outposts defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ s3\-outposts:AccessPointNetworkOrigin ](https://docs.aws.amazon.com/AmazonS3/latest/dev/creating-access-points.html#access-points-policies)  | Filters access by the network origin \(Internet or VPC\) | String | 
|   [ s3\-outposts:DataAccessPointAccount ](https://docs.aws.amazon.com/AmazonS3/latest/dev/creating-access-points.html#access-points-policies)  | Filters access by the AWS Account ID that owns the access point | String | 
|   s3\-outposts:DataAccessPointArn  | Filters access by an access point Amazon Resource Name \(ARN\) | String | 
|   [ s3\-outposts:ExistingObjectTag/<key> ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  | Filters access by requiring that an existing object tag has a specific tag key and value | String | 
|   [ s3\-outposts:RequestObjectTag/<key> ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  | Filters access by restricting the tag keys and values allowed on objects | String | 
|   [ s3\-outposts:RequestObjectTagKeys ](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-tagging.html#tagging-and-policies)  | Filters access by restricting the tag keys allowed on objects | String | 
|   [ s3\-outposts:authType ](https://docs.aws.amazon.com/AmazonS3/latest/API/bucket-policy-s3-sigv4-conditions.html)  | Filters access by restricting incoming requests to a specific authentication method | String | 
|   [ s3\-outposts:delimiter ](https://docs.aws.amazon.com/AmazonS3/latest/dev/walkthrough1.html)  | Filters access by requiring the delimiter parameter | String | 
|   [ s3\-outposts:max\-keys ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#example-numeric-condition-operators)  | Filters access by limiting the maximum number of keys returned in a ListBucket request | Numeric | 
|   [ s3\-outposts:prefix ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#condition-key-bucket-ops-2)  | Filters access by key name prefix | String | 
|   [ s3\-outposts:signatureAge ](https://docs.aws.amazon.com/AmazonS3/latest/API/bucket-policy-s3-sigv4-conditions.html)  | Filters access by identifying the length of time, in milliseconds, that a signature is valid in an authenticated request | Numeric | 
|   [ s3\-outposts:signatureversion ](https://docs.aws.amazon.com/AmazonS3/latest/API/bucket-policy-s3-sigv4-conditions.html)  | Filters access by identifying the version of AWS Signature that is supported for authenticated requests | String | 
|   [ s3\-outposts:x\-amz\-acl ](https://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#permissions)  | Filters access by requiring the x\-amz\-acl header with a specific canned ACL in a request | String | 
|   [ s3\-outposts:x\-amz\-content\-sha256 ](https://docs.aws.amazon.com/AmazonS3/latest/API/bucket-policy-s3-sigv4-conditions.html)  | Filters access by disallowing unsigned content in your bucket | String | 
|   [ s3\-outposts:x\-amz\-copy\-source ](https://docs.aws.amazon.com/AmazonS3/latest/dev/amazon-s3-policy-keys.html#putobject-limit-copy-source-3)  | Filters access by restricting the copy source to a specific bucket, prefix, or object | String | 
|   [ s3\-outposts:x\-amz\-metadata\-directive ](https://docs.aws.amazon.com/AmazonS3/latest/API/API_CopyObject.html)  | Filters access by enabling enforcement of object metadata behavior \(COPY or REPLACE\) when objects are copied | String | 
|   [ s3\-outposts:x\-amz\-server\-side\-encryption ](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingServerSideEncryption.html)  | Filters access by requiring server\-side encryption | String | 
|   [ s3\-outposts:x\-amz\-storage\-class ](https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html#sc-howtoset)  | Filters access by storage class | String | 