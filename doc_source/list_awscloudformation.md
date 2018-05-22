# Actions, Resources, and Condition Keys for AWS CloudFormation<a name="list_awscloudformation"></a>

AWS CloudFormation \(service prefix: `cloudformation`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/cloudformation/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/cloudformation/latest/UserGuide/using-iam-template.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CloudFormation](#awscloudformation-actions-as-permissions)
+ [Resources Defined by CloudFormation](#awscloudformation-resources-for-iam-policies)
+ [Condition Keys for AWS CloudFormation](#awscloudformation-policy-keys)

## Actions Defined by AWS CloudFormation<a name="awscloudformation-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloudformation.html)

## Resources Defined by CloudFormation<a name="awscloudformation-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloudformation-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/cloudformation/latest/UserGuide/cfn-whatis-concepts.html#w1ab2b5c17c11](http://docs.aws.amazon.com/cloudformation/latest/UserGuide/cfn-whatis-concepts.html#w1ab2b5c17c11) | arn:$\{Partition\}:cloudformation:$\{Region\}:$\{Account\}:stack/$\{StackName\}/$\{Id\} |  | 

## Condition Keys for AWS CloudFormation<a name="awscloudformation-policy-keys"></a>

AWS CloudFormation defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [${DocumenationLink}using-iam-template.html#using-iam-template-conditions](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | An AWS CloudFormation change set name\. Use to control which change sets IAM users can execute or delete\. | String | 
| [${DocumenationLink}using-iam-template.html#using-iam-template-conditions](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | The template resource types, such as <code>AWS::EC2::Instance</code>\. Use to control which resource types IAM users can work with when they create or update a stack | String | 
| [${DocumenationLink}using-iam-template.html#using-iam-template-conditions](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | The ARN of an IAM service role\. Use to control which service role IAM users can use to work with stacks or change sets\. | ARN | 
| [${DocumenationLink}using-iam-template.html#using-iam-template-conditions](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | An Amazon S3 stack policy URL\. Use to control which stack policies IAM users can associate with a stack during a create or update stack action\. | String | 
| [${DocumenationLink}using-iam-template.html#using-iam-template-conditions](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | An Amazon S3 template URL\. Use to control which templates IAM users can use when they create or update stacks\. | String | 