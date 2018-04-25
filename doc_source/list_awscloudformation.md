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

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [CancelUpdateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CancelUpdateStack.html) | Cancels an update on the specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [ContinueUpdateRollback](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ContinueUpdateRollback.html) | For a specified stack that is in the UPDATE\_ROLLBACK\_FAILED state, continues rolling it back to the UPDATE\_ROLLBACK\_COMPLETE state\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [CreateChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateChangeSet.html) | Creates a list of changes for a stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [CreateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateStack.html) | Creates a stack as specified in the template\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [DeleteChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteChangeSet.html) | Deletes the specified change set\. Deleting change sets ensures that no one executes the wrong change set\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [DeleteStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteStack.html) | Deletes a specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [DescribeAccountLimits](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeAccountLimits.html) | Retrieves your account's AWS CloudFormation limits\. |   |  |  |  | 
| [DescribeStackEvents](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackEvents.html) | Returns all stack related events for a specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [DescribeStackResource](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackResource.html) | Returns a description of the specified resource in the specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [DescribeStackResources](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackResources.html) | Returns AWS resource descriptions for running and deleted stacks\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [DescribeStacks](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStacks.html) | Returns the description for the specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [EstimateTemplateCost](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_EstimateTemplateCost.html) | Returns the estimated monthly cost of a template\. |   |  |  |  | 
| [ExecuteChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ExecuteChangeSet.html) | Updates a stack using the input information that was provided when the specified change set was created\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [GetStackPolicy](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetStackPolicy.html) | Returns the stack policy for a specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [GetTemplate](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetTemplate.html) | Returns the template body for a specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [GetTemplateSummary](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetTemplateSummary.html) | Returns information about a new or existing template\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [ListChangeSets](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListChangeSets.html) | Returns the ID and status of each active change set for a stack\. For example, AWS CloudFormation lists change sets that are in the CREATE\_IN\_PROGRESS or CREATE\_PENDING state\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [ListExports](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListExports.html) | Lists all exported output values in the account and region in which you call this action\. |   |  |  |  | 
| [ListImports](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListImports.html) | Lists all stacks that are importing an exported output value\. |   |  |  |  | 
| [ListStackResources](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStackResources.html) | Returns descriptions of all resources of the specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [ListStacks](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStacks.html) | Returns the summary information for stacks whose status matches the specified StackStatusFilter\. |   |  |  |  | 
| [SetStackPolicy](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SetStackPolicy.html) | Sets a stack policy for a specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [SignalResource](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SignalResource.html) | Sends a signal to the specified resource with a success or failure status\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [UpdateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateStack.html) | Updates a stack as specified in the template\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [UpdateTerminationProtection](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateTerminationProtection.html) | Updates termination protection for the specified stack\. |   | [stack\*](#awscloudformation-stack)  |  |  | 
| [ValidateTemplate](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SignalResource.html) | Validates a specified template\. |   |  |  |  | 

## Resources Defined by CloudFormation<a name="awscloudformation-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloudformation-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [stack](http://docs.aws.amazon.com/cloudformation/latest/UserGuide/cfn-whatis-concepts.html#w1ab2b5c17c11) | arn:$\{Partition\}:cloudformation:$\{Region\}:$\{Account\}:stack/$\{StackName\}/$\{Id\} |  | 

## Condition Keys for AWS CloudFormation<a name="awscloudformation-policy-keys"></a>

AWS CloudFormation defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [cloudformation:ChangeSetName](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | An AWS CloudFormation change set name\. Use to control which change sets IAM users can execute or delete\. | String | 
| [cloudformation:ResourceTypes](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | The template resource types, such as <code>AWS::EC2::Instance</code>\. Use to control which resource types IAM users can work with when they create or update a stack | String | 
| [cloudformation:RoleArn](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | The ARN of an IAM service role\. Use to control which service role IAM users can use to work with stacks or change sets\. | ARN | 
| [cloudformation:StackPolicyUrl](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | An Amazon S3 stack policy URL\. Use to control which stack policies IAM users can associate with a stack during a create or update stack action\. | String | 
| [cloudformation:TemplateUrl](${DocumenationLink}using-iam-template.html#using-iam-template-conditions) | An Amazon S3 template URL\. Use to control which templates IAM users can use when they create or update stacks\. | String | 