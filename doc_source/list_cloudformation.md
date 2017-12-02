# Actions and Condition Context Keys for AWS CloudFormation<a name="list_cloudformation"></a>

AWS CloudFormation \(service prefix: cloudformation\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS CloudFormation**

For information about using the following AWS CloudFormation API actions in an IAM policy, see [AWS CloudFormation Actions and Resources](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html#d0e4248) in the *AWS CloudFormation User Guide*\.

+ `[cloudformation:ListStacks](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStacks.html)`

+ `[cloudformation:DescribeChangeSet](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeChangeSet.html)`

+ `[cloudformation:ValidateTemplate](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ValidateTemplate.html)`

+ `[cloudformation:GetTemplateSummary](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetTemplateSummary.html)`

+ `[cloudformation:UpdateStack](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateStack.html)`

+ `[cloudformation:DescribeAccountLimits](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeAccountLimits.html)`

+ `[cloudformation:CreateStack](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateStack.html)`

+ `[cloudformation:DescribeStackResource](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackResource.html)`

+ `[cloudformation:DescribeStackEvents](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackEvents.html)`

+ `[cloudformation:PreviewStackUpdate](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_PreviewStackUpdate.html)`

+ `[cloudformation:DeleteStack](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteStack.html)`

+ `[cloudformation:CreateUploadBucket](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateUploadBucket.html)`

+ `[cloudformation:DeleteChangeSet](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteChangeSet.html)`

+ `[cloudformation:SignalResource](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SignalResource.html)`

+ `[cloudformation:ExecuteChangeSet](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ExecuteChangeSet.html)`

+ `[cloudformation:DescribeStacks](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStacks.html)`

+ `[cloudformation:SetStackPolicy](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SetStackPolicy.html)`

+ `[cloudformation:CreateChangeSet](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateChangeSet.html)`

+ `[cloudformation:GetTemplate](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetTemplate.html)`

+ `[cloudformation:DescribeStackResources](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackResources.html)`

+ `[cloudformation:GetStackPolicy](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetStackPolicy.html)`

+ `[cloudformation:CancelUpdateStack](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CancelUpdateStack.html)`

+ `[cloudformation:EstimateTemplateCost](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_EstimateTemplateCost.html)`

+ `[cloudformation:ContinueUpdateRollback](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ContinueUpdateRollback.html)`

+ `[cloudformation:ListStackResources](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStackResources.html)`

+ `[cloudformation:ListChangeSets](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListChangeSets.html)`

**Condition context keys for AWS CloudFormation**

For information about using conditions in an IAM policy, see [AWS CloudFormation Conditions](http://alpha-docs-aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html#d0e4297) in the *AWS CloudFormation User Guide*\.

AWS CloudFormation has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `cloudformation:ChangeSetName`

+ `cloudformation:ResourceTypes`

+ `cloudformation:RoleArn`

+ `cloudformation:StackPolicyUrl`

+ `cloudformation:TemplateUrl`