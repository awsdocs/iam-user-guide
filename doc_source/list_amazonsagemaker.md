# Actions, resources, and condition keys for Amazon SageMaker<a name="list_amazonsagemaker"></a>

Amazon SageMaker \(service prefix: `sagemaker`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/sagemaker/latest/dg/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/sagemaker/latest/dg/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/sagemaker/latest/dg/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon SageMaker](#amazonsagemaker-actions-as-permissions)
+ [Resource types defined by Amazon SageMaker](#amazonsagemaker-resources-for-iam-policies)
+ [Condition keys for Amazon SageMaker](#amazonsagemaker-policy-keys)

## Actions defined by Amazon SageMaker<a name="amazonsagemaker-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html)

## Resource types defined by Amazon SageMaker<a name="amazonsagemaker-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonsagemaker-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   human\-loop  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:human\-loop/$\{HumanLoopName\}  |  | 
|   flow\-definition  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:flow\-definition/$\{FlowDefinitionName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   human\-task\-ui  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:human\-task\-ui/$\{HumanTaskUiName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   labeling\-job  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:labeling\-job/$\{LabelingJobName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   workteam  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:workteam/$\{WorkteamName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   workforce  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:workforce/$\{WorkforceName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   domain  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:domain/$\{DomainId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   user\-profile  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:user\-profile/$\{DomainId\}/$\{UserProfileName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   app  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:app/$\{DomainId\}/$\{UserProfileName\}/$\{AppType\}/$\{AppName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   notebook\-instance  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:notebook\-instance/$\{NotebookInstanceName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   notebook\-instance\-lifecycle\-config  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:notebook\-instance\-lifecycle\-config/$\{NotebookInstanceLifecycleConfigName\}  |  | 
|   code\-repository  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:code\-repository/$\{CodeRepositoryName\}  |  | 
|   algorithm  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:algorithm/$\{AlgorithmName\}  |  | 
|   training\-job  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:training\-job/$\{TrainingJobName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   processing\-job  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:processing\-job/$\{ProcessingJobName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   hyper\-parameter\-tuning\-job  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:hyper\-parameter\-tuning\-job/$\{HyperParameterTuningJobName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   model\-package  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:model\-package/$\{ModelPackageName\}  |  | 
|   model  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:model/$\{ModelName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   endpoint\-config  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:endpoint\-config/$\{EndpointConfigName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   endpoint  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:endpoint/$\{EndpointName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   transform\-job  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:transform\-job/$\{TransformJobName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   compilation\-job  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:compilation\-job/$\{CompilationJobName\}  |  | 
|   automl\-job  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:automl\-job/$\{AutoMLJobJobName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   monitoring\-schedule  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:monitoring\-schedule/$\{MonitoringScheduleName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   experiment  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:experiment/$\{ExperimentName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   experiment\-trial  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:experiment\-trial/$\{TrialName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 
|   experiment\-trial\-component  |  arn:$\{Partition\}:sagemaker:$\{Region\}:$\{Account\}:experiment\-trial\-component/$\{TrialComponentName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonsagemaker-aws_ResourceTag___TagKey_)   [ sagemaker:ResourceTag/$\{TagKey\} ](#amazonsagemaker-sagemaker_ResourceTag___TagKey_)   | 

## Condition keys for Amazon SageMaker<a name="amazonsagemaker-policy-keys"></a>

Amazon SageMaker defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | A key that is present in the request the user makes to the SageMaker service\. | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | A tag key and value pair\. | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The list of all the tag key names associated with the resource in the request\. | String | 
|   [ sagemaker:AcceleratorTypes ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The list of all accelerator types associated with the resource in the request\. | ArrayOfString | 
|   [ sagemaker:AppNetworkAccess ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | App network access associated with the resource in the request\. | String | 
|   [ sagemaker:DirectInternetAccess ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The direct internet access associated with the resource in the request\. | String | 
|   [ sagemaker:DomainSharingOutputKmsKey ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The Domain sharing output KMS key associated with the resource in the request\. | ARN | 
|   [ sagemaker:FileSystemAccessMode ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | File system access mode associated with the resource in the request\. | String | 
|   [ sagemaker:FileSystemDirectoryPath ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | File system directory path associated with the resource in the request\. | String | 
|   [ sagemaker:FileSystemId ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | A file system ID associated with the resource in the request\. | String | 
|   [ sagemaker:FileSystemType ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | File system type associated with the resource in the request\. | String | 
|   [ sagemaker:HomeEfsFileSystemKmsKey ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The KMS Key Id of the EFS File System used for UserProfile home directories, which is associated with the resource in the request\. | ARN | 
|   [ sagemaker:InstanceTypes ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The list of all instance types associated with the resource in the request\. | ArrayOfString | 
|   [ sagemaker:InterContainerTrafficEncryption ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The inter container traffic encryption associated with the resource in the request\. | Bool | 
|   [ sagemaker:MaxRuntimeInSeconds ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The max runtime in seconds associated with the resource in the request\. | Numeric | 
|   [ sagemaker:ModelArn ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The model arn associated with the resource in the request\. | ARN | 
|   [ sagemaker:NetworkIsolation ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The network isolation associated with the resource in the request\. | Bool | 
|   [ sagemaker:OutputKmsKey ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The output kms key associated with the resource in the request\. | ARN | 
|   [ sagemaker:ResourceTag/ ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The preface string for a tag key and value pair attached to a resource\. | String | 
|   [ sagemaker:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | A tag key and value pair\. | String | 
|   [ sagemaker:RootAccess ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The root access associated with the resource in the request\. | String | 
|   [ sagemaker:TargetModel ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The target model associated with the Multi\-Model Endpoint in the request\. | String | 
|   [ sagemaker:VolumeKmsKey ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The volume kms key associated with the resource in the request\. | ARN | 
|   [ sagemaker:VpcSecurityGroupIds ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The list of all vpc security group ids associated with the resource in the request\. | ArrayOfString | 
|   [ sagemaker:VpcSubnets ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The list of all vpc subnets associated with the resource in the request\. | ArrayOfString | 
|   [ sagemaker:WorkteamArn ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The workteam arn associated to the request\. | ARN | 
|   [ sagemaker:WorkteamType ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonsagemaker.html#amazonsagemaker-policy-keys)  | The workteam type associated to the request\. This can be public\-crowd, private\-crowd or vendor\-crowd\. | String | 