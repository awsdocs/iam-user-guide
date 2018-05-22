# Actions, Resources, and Condition Keys for Amazon EC2 Container Registry<a name="list_amazonec2containerregistry"></a>

Amazon EC2 Container Registry \(service prefix: `ecr`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AmazonECR/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AmazonECR/latest/userguide/ECR_IAM_policies.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon EC2 Container Registry](#amazonec2containerregistry-actions-as-permissions)
+ [Resources Defined by EC2 Container Registry](#amazonec2containerregistry-resources-for-iam-policies)
+ [Condition Keys for Amazon EC2 Container Registry](#amazonec2containerregistry-policy-keys)

## Actions Defined by Amazon EC2 Container Registry<a name="amazonec2containerregistry-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_BatchCheckLayerAvailability.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_BatchCheckLayerAvailability.html) | Check the availability of multiple image layers in a specified registry and repository\. | Read | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_BatchDeleteImage.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_BatchDeleteImage.html) | Deletes a list of specified images within a specified repository\.  | Write | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_BatchGetImage.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_BatchGetImage.html) | Gets detailed information for specified images within a specified repository\. | Read | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_CompleteLayerUpload.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_CompleteLayerUpload.html) | Inform Amazon ECR that the image layer upload for a specified registry, repository name, and upload ID, has completed\. | Write | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_CreateRepository.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_CreateRepository.html) | Creates an image repository\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_DeleteRepository.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_DeleteRepository.html) | Deletes an existing image repository\.  | Write | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_DeleteRepositoryPolicy.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_DeleteRepositoryPolicy.html) | Deletes the repository policy from a specified repository\. | Write | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_DescribeImages.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_DescribeImages.html) | Returns metadata about the images in a repository, including image size, image tags, and creation date\. | Read | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_DescribeRepositories.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_DescribeRepositories.html) | Describes image repositories in a registry | List | [repository](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_GetAuthorizationToken.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_GetAuthorizationToken.html) | Retrieves a token that is valid for a specified registry for 12 hours\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_GetDownloadUrlForLayer.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_GetDownloadUrlForLayer.html) | Retrieves the pre\-signed Amazon S3 download URL corresponding to an image layer\.  | Read | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_GetRepositoryPolicy.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_GetRepositoryPolicy.html) | Retrieves the repository policy for a specified repository\. | Read | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_InitiateLayerUpload.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_InitiateLayerUpload.html) | Notify Amazon ECR that you intend to upload an image layer\. | Write | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_ListImages.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_ListImages.html) | Lists all the image IDs for a given repository\. | List | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_PutImage.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_PutImage.html) | Creates or updates the image manifest associated with an image\. | Write | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_SetRepositoryPolicy.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_SetRepositoryPolicy.html) | Applies a repository policy on a specified repository to control access permissions\. | Write | [repository\*](#amazonec2containerregistry-repository)  |  |  | 
| [http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_UploadLayerPart.html](http://docs.aws.amazon.com/AmazonECR/latest/APIReference/API_UploadLayerPart.html) | Uploads an image layer part to Amazon ECR\. | Write | [repository\*](#amazonec2containerregistry-repository)  |  |  | 

## Resources Defined by EC2 Container Registry<a name="amazonec2containerregistry-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonec2containerregistry-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/AmazonECR/latest/userguide/iam-policy-structure.html#ECR_ARN_Format](http://docs.aws.amazon.com/AmazonECR/latest/userguide/iam-policy-structure.html#ECR_ARN_Format) | arn:$\{Partition\}:ecr:$\{Region\}:$\{Account\}:repository/$\{RepositoryName\} |  | 

## Condition Keys for Amazon EC2 Container Registry<a name="amazonec2containerregistry-policy-keys"></a>

EC2 Container Registry has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.