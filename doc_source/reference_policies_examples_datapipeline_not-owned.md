# AWS Data Pipeline: Denies Access to DataPipeline Pipelines That a User Did Not Create<a name="reference_policies_examples_datapipeline_not-owned"></a>

This example shows how you might create a policy that denies access to pipelines that a user did not create\. If the value of the `PipelineCreator` field matches the IAM user name, then the specified actions are not denied\. This policy provides the permissions necessary to complete this action using the AWS API or AWS CLI only\.

**Important**  
This policy does not allow any actions\. Use this policy in combination with other policies that allow specific actions\. 

```
 {
   "Version": "2012-10-17",
   "Statement": [
       {
           "Sid": "ExplicitDenyIfNotTheOwner",
           "Effect": "Deny",
           "Action": [
               "datapipeline:ActivatePipeline",
               "datapipeline:AddTags",
               "datapipeline:DeactivatePipeline",
               "datapipeline:DeletePipeline",
               "datapipeline:DescribeObjects",
               "datapipeline:EvaluateExpression",
               "datapipeline:GetPipelineDefinition",
               "datapipeline:PollForTask",
               "datapipeline:PutPipelineDefinition",
               "datapipeline:QueryObjects",
               "datapipeline:RemoveTags",
               "datapipeline:ReportTaskProgress",
               "datapipeline:ReportTaskRunnerHeartbeat",
               "datapipeline:SetStatus",
               "datapipeline:SetTaskStatus",
               "datapipeline:ValidatePipelineDefinition"
           ],
           "Resource": [
               "*"
           ],
           "Condition": {
               "StringNotEquals": {
                   "datapipeline:PipelineCreator": "${aws:userid}"
               }
           }
       }
   ]
 }
```