# Actions, resources, and condition keys for AWS CloudFormation<a name="list_awscloudformation"></a>

AWS CloudFormation \(service prefix: `cloudformation`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html) permission policies\.

**Topics**
+ [Actions defined by AWS CloudFormation](#awscloudformation-actions-as-permissions)
+ [Resource types defined by AWS CloudFormation](#awscloudformation-resources-for-iam-policies)
+ [Condition keys for AWS CloudFormation](#awscloudformation-policy-keys)

## Actions defined by AWS CloudFormation<a name="awscloudformation-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloudformation.html)

## Resource types defined by AWS CloudFormation<a name="awscloudformation-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloudformation-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ stack ](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html#w2ab1b5c15b9)  |  arn:$\{Partition\}:cloudformation:$\{Region\}:$\{Account\}:stack/$\{StackName\}/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awscloudformation-aws_ResourceTag___TagKey_)   | 
|   [ stackset ](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-concepts.html#stacksets-concepts-stackset)  |  arn:$\{Partition\}:cloudformation:$\{Region\}:$\{Account\}:stackset/$\{StackSetName\}:$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awscloudformation-aws_ResourceTag___TagKey_)   | 
|   [ changeset ](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html#w2ab1b5c15c11)  |  arn:$\{Partition\}:cloudformation:$\{Region\}:$\{Account\}:changeSet/$\{ChangeSetName\}:$\{Id\}  |  | 

## Condition keys for AWS CloudFormation<a name="awscloudformation-policy-keys"></a>

AWS CloudFormation defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  |  | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  |  | String | 
|   [ aws:TagKeys ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  |  | String | 
|   [ cloudformation:ChangeSetName ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  | An AWS CloudFormation change set name\. Use to control which change sets IAM users can execute or delete\. | String | 
|   [ cloudformation:ImportResourceTypes ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  | The template resource types, such as <code>AWS::EC2::Instance</code>\. Use to control which resource types IAM users can work with when they want to import a resource into a stack\. | String | 
|   [ cloudformation:ResourceTypes ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  | The template resource types, such as <code>AWS::EC2::Instance</code>\. Use to control which resource types IAM users can work with when they create or update a stack\. | String | 
|   [ cloudformation:RoleArn ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  | The ARN of an IAM service role\. Use to control which service role IAM users can use to work with stacks or change sets\. | ARN | 
|   [ cloudformation:StackPolicyUrl ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  | An Amazon S3 stack policy URL\. Use to control which stack policies IAM users can associate with a stack during a create or update stack action\. | String | 
|   [ cloudformation:TemplateUrl ](${DocumenationLink}using-iam-template.html#using-iam-template-conditions)  | An Amazon S3 template URL\. Use to control which templates IAM users can use when they create or update stacks\. | String | 