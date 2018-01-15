# Actions and Condition Context Keys for AWS CloudFormation<a name="list_cloudformation"></a>

AWS CloudFormation \(service prefix: cloudformation\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS CloudFormation**

For information about using the following AWS CloudFormation API actions in an IAM policy, see [AWS CloudFormation Actions and Resources](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html#d0e4248) in the *AWS CloudFormation User Guide*\.

+ `[cloudformation:ListImports](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListImports.html)`

+ `[cloudformation:ListStacks](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStacks.html)`

+ `[cloudformation:DescribeChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeChangeSet.html)`

+ `[cloudformation:ValidateTemplate](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ValidateTemplate.html)`

+ `[cloudformation:UpdateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateStack.html)`

+ `[cloudformation:GetTemplateSummary](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetTemplateSummary.html)`

+ `[cloudformation:DescribeAccountLimits](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeAccountLimits.html)`

+ `[cloudformation:CreateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateStack.html)`

+ `[cloudformation:DescribeStackResource](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackResource.html)`

+ `[cloudformation:DescribeStackEvents](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackEvents.html)`

+ `[cloudformation:ListExports](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListExports.html)`

+ `[cloudformation:PreviewStackUpdate](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_PreviewStackUpdate.html)`

+ `[cloudformation:DeleteStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteStack.html)`

+ `[cloudformation:CreateUploadBucket](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateUploadBucket.html)`

+ `[cloudformation:DeleteChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteChangeSet.html)`

+ `[cloudformation:SignalResource](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SignalResource.html)`

+ `[cloudformation:ExecuteChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ExecuteChangeSet.html)`

+ `[cloudformation:DescribeStacks](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStacks.html)`

+ `[cloudformation:CreateChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateChangeSet.html)`

+ `[cloudformation:SetStackPolicy](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SetStackPolicy.html)`

+ `[cloudformation:GetTemplate](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetTemplate.html)`

+ `[cloudformation:DescribeStackResources](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackResources.html)`

+ `[cloudformation:GetStackPolicy](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetStackPolicy.html)`

+ `[cloudformation:UpdateTerminationProtection](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateTerminationProtection.html)`

+ `[cloudformation:EstimateTemplateCost](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_EstimateTemplateCost.html)`

+ `[cloudformation:CancelUpdateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CancelUpdateStack.html)`

+ `[cloudformation:ContinueUpdateRollback](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ContinueUpdateRollback.html)`

+ `[cloudformation:ListStackResources](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStackResources.html)`

+ `[cloudformation:ListChangeSets](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListChangeSets.html)`

**Condition context keys for AWS CloudFormation**

For information about using conditions in an IAM policy, see [AWS CloudFormation Conditions](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html#d0e4297) in the *AWS CloudFormation User Guide*\.

AWS CloudFormation has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.

+ `cloudformation:ChangeSetName`

+ `cloudformation:ResourceTypes`

+ `cloudformation:RoleArn`

+ `cloudformation:StackPolicyUrl`

+ `cloudformation:TemplateUrl`