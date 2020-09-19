# Actions, resources, and condition keys for Amazon EC2 Image Builder<a name="list_amazonec2imagebuilder"></a>

Amazon EC2 Image Builder \(service prefix: `imagebuilder`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/imagebuilder/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/imagebuilder/latest/userguide/security-iam.html) permission policies\.

**Topics**
+ [Actions defined by Amazon EC2 Image Builder](#amazonec2imagebuilder-actions-as-permissions)
+ [Resource types defined by Amazon EC2 Image Builder](#amazonec2imagebuilder-resources-for-iam-policies)
+ [Condition keys for Amazon EC2 Image Builder](#amazonec2imagebuilder-policy-keys)

## Actions defined by Amazon EC2 Image Builder<a name="amazonec2imagebuilder-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2imagebuilder.html)

## Resource types defined by Amazon EC2 Image Builder<a name="amazonec2imagebuilder-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonec2imagebuilder-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ component ](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_Component.html)  |  arn:$\{Partition\}:imagebuilder:$\{Region\}:$\{Account\}:component/$\{ComponentName\}/$\{ComponentVersion\}/$\{ComponentBuildVersion\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2imagebuilder-aws_ResourceTag___TagKey_)   | 
|   [ componentVersion ](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_ComponentVersion)  |  arn:$\{Partition\}:imagebuilder:$\{Region\}:$\{Account\}:component/$\{ComponentName\}/$\{ComponentVersion\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2imagebuilder-aws_ResourceTag___TagKey_)   | 
|   [ distributionConfiguration ](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_DistributionConfiguration.html)  |  arn:$\{Partition\}:imagebuilder:$\{Region\}:$\{Account\}:distribution\-configuration/$\{DistributionConfigurationName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2imagebuilder-aws_ResourceTag___TagKey_)   | 
|   [ image ](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_Image.html)  |  arn:$\{Partition\}:imagebuilder:$\{Region\}:$\{Account\}:image/$\{ImageName\}/$\{ImageVersion\}/$\{ImageBuildVersion\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2imagebuilder-aws_ResourceTag___TagKey_)   | 
|   [ imageVersion ](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_ImageVersion.html)  |  arn:$\{Partition\}:imagebuilder:$\{Region\}:$\{Account\}:image/$\{ImageName\}/$\{ImageVersion\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2imagebuilder-aws_ResourceTag___TagKey_)   | 
|   [ imageRecipe ](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_ImageRecipe.html)  |  arn:$\{Partition\}:imagebuilder:$\{Region\}:$\{Account\}:image\-recipe/$\{ImageRecipeName\}/$\{ImageRecipeVersion\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2imagebuilder-aws_ResourceTag___TagKey_)   | 
|   [ imagePipeline ](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_ImagePipeline.html)  |  arn:$\{Partition\}:imagebuilder:$\{Region\}:$\{Account\}:image\-pipeline/$\{ImagePipelineName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2imagebuilder-aws_ResourceTag___TagKey_)   | 
|   [ infrastructureConfiguration ](https://docs.aws.amazon.com/imagebuilder/latest/APIReference/API_InfrastructureConfiguration.html)  |  arn:$\{Partition\}:imagebuilder:$\{Region\}:$\{Account\}:infrastructure\-configuration/$\{ResourceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2imagebuilder-aws_ResourceTag___TagKey_)   | 
|   [ kmsKey ](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#master_keys)  |  arn:$\{Partition\}:kms:$\{Region\}:$\{Account\}:key/$\{KeyId\}  |  | 

## Condition keys for Amazon EC2 Image Builder<a name="amazonec2imagebuilder-policy-keys"></a>

Amazon EC2 Image Builder defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions by the presence of tag key\-value pairs in the request | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions by tag key\-value pairs attached to the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions by the presence of tag keys in the request | String | 
|   [ imagebuilder:CreatedResourceTag/<key> ](https://docs.aws.amazon.com/imagebuilder/latest/userguide/security_iam_service-with-iam.html#image-builder-security-createdresourcetag)  | Filters access by the tag key\-value pairs attached to the resource created by Image Builder | String | 
|   [ imagebuilder:CreatedResourceTagKeys ](https://docs.aws.amazon.com/imagebuilder/latest/userguide/security_iam_service-with-iam.html#image-builder-security-createdresourcetagkeys)  | Filters access by the presence of tag keys in the request | String | 