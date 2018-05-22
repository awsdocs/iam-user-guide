# Actions, Resources, and Condition Keys for AWS Batch<a name="list_awsbatch"></a>

AWS Batch \(service prefix: `batch`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/batch/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/batch/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/batch/latest/userguide/IAM_policies.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Batch](#awsbatch-actions-as-permissions)
+ [Resources Defined by Batch](#awsbatch-resources-for-iam-policies)
+ [Condition Keys for AWS Batch](#awsbatch-policy-keys)

## Actions Defined by AWS Batch<a name="awsbatch-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_CancelJob.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_CancelJob.html) | Cancels jobs in an AWS Batch job queue\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_CreateComputeEnvironment.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_CreateComputeEnvironment.html) | Creates an AWS Batch compute environment\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_CreateJobQueue.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_CreateJobQueue.html) | Creates an AWS Batch job queue\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_DeleteComputeEnvironment.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_DeleteComputeEnvironment.html) | Deletes an AWS Batch compute environment\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_DeleteJobQueue.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_DeleteJobQueue.html) | Deletes the specified job queue\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_DeregisterJobDefinition.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_DeregisterJobDefinition.html) | Deregisters an AWS Batch job definition\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_DescribeComputeEnvironments.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_DescribeComputeEnvironments.html) | Describes one or more of your compute environments\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_DescribeJobDefinitions.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_DescribeJobDefinitions.html) | Describes a list of job definitions\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_DescribeJobQueues.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_DescribeJobQueues.html) | Describes one or more of your job queues\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_DescribeJobs.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_DescribeJobs.html) | Describes a list of AWS Batch jobs\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_ListJobs.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_ListJobs.html) | Returns a list of task jobs for a specified job queue\. | List |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_RegisterJobDefinition.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_RegisterJobDefinition.html) | Registers an AWS Batch job definition\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_SubmitJob.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_SubmitJob.html) | Submits an AWS Batch job from a job definition\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_TerminateJob.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_TerminateJob.html) | Terminates jobs in a job queue\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_UpdateComputeEnvironment.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_UpdateComputeEnvironment.html) | Updates an AWS Batch compute environment\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/batch/latest/APIReference/API_UpdateJobQueue.html](http://docs.aws.amazon.com/batch/latest/APIReference/API_UpdateJobQueue.html) | Updates a job queue\. | Write |  |  |  | 

## Resources Defined by Batch<a name="awsbatch-resources-for-iam-policies"></a>

Batch has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Batch<a name="awsbatch-policy-keys"></a>

Batch has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.