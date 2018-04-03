# Actions and Condition Context Keys for AWS CloudFormation<a name="list_cloudformation"></a>

AWS CloudFormation \(service prefix: cloudformation\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS CloudFormation**

For information about using the following AWS CloudFormation API actions in an IAM policy, see [AWS CloudFormation Actions and Resources](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html#d0e4248) in the *AWS CloudFormation User Guide*\.
+ `[cloudformation:CancelUpdateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CancelUpdateStack.html)`
+ `[cloudformation:ContinueUpdateRollback](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ContinueUpdateRollback.html)`
+ `[cloudformation:CreateChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateChangeSet.html)`
+ `[cloudformation:CreateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateStack.html)`
+ `[cloudformation:CreateStackInstances](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateStackInstances.html)`
+ `[cloudformation:CreateStackSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateStackSet.html)`
+ `[cloudformation:CreateUploadBucket](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateUploadBucket.html)`
+ `[cloudformation:DeleteChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteChangeSet.html)`
+ `[cloudformation:DeleteStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteStack.html)`
+ `[cloudformation:DeleteStackInstances](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteStackInstances.html)`
+ `[cloudformation:DeleteStackSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DeleteStackSet.html)`
+ `[cloudformation:DescribeAccountLimits](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeAccountLimits.html)`
+ `[cloudformation:DescribeChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeChangeSet.html)`
+ `[cloudformation:DescribeStackEvents](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackEvents.html)`
+ `[cloudformation:DescribeStackInstance](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackInstance.html)`
+ `[cloudformation:DescribeStackResource](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackResource.html)`
+ `[cloudformation:DescribeStackResources](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackResources.html)`
+ `[cloudformation:DescribeStacks](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStacks.html)`
+ `[cloudformation:DescribeStackSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackSet.html)`
+ `[cloudformation:DescribeStackSetOperation](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_DescribeStackSetOperation.html)`
+ `[cloudformation:EstimateTemplateCost](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_EstimateTemplateCost.html)`
+ `[cloudformation:ExecuteChangeSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ExecuteChangeSet.html)`
+ `[cloudformation:GetStackPolicy](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetStackPolicy.html)`
+ `[cloudformation:GetTemplate](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetTemplate.html)`
+ `[cloudformation:GetTemplateSummary](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_GetTemplateSummary.html)`
+ `[cloudformation:ListChangeSets](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListChangeSets.html)`
+ `[cloudformation:ListExports](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListExports.html)`
+ `[cloudformation:ListImports](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListImports.html)`
+ `[cloudformation:ListStackInstances](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStackInstances.html)`
+ `[cloudformation:ListStackResources](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStackResources.html)`
+ `[cloudformation:ListStacks](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStacks.html)`
+ `[cloudformation:ListStackSetOperationResults](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStackSetOperationResults.html)`
+ `[cloudformation:ListStackSetOperations](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStackSetOperations.html)`
+ `[cloudformation:ListStackSets](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ListStackSets.html)`
+ `[cloudformation:PreviewStackUpdate](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_PreviewStackUpdate.html)`
+ `[cloudformation:SetStackPolicy](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SetStackPolicy.html)`
+ `[cloudformation:SignalResource](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_SignalResource.html)`
+ `[cloudformation:StopStackSetOperation](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_StopStackSetOperation.html)`
+ `[cloudformation:UpdateStack](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateStack.html)`
+ `[cloudformation:UpdateStackInstances](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateStackInstances.html)`
+ `[cloudformation:UpdateStackSet](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateStackSet.html)`
+ `[cloudformation:UpdateTerminationProtection](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_UpdateTerminationProtection.html)`
+ `[cloudformation:ValidateTemplate](http://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_ValidateTemplate.html)`

**Condition context keys for AWS CloudFormation**

For information about using conditions in an IAM policy, see [AWS CloudFormation Conditions](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-template.html#d0e4297) in the *AWS CloudFormation User Guide*\.

AWS CloudFormation has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ `cloudformation:ChangeSetName`
+ `cloudformation:ResourceTypes`
+ `cloudformation:RoleArn`
+ `cloudformation:StackPolicyUrl`
+ `cloudformation:TemplateUrl`
