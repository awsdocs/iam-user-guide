# Actions, Resources, and Condition Keys for AWS Elemental MediaConvert<a name="list_awselementalmediaconvert"></a>

AWS Elemental MediaConvert \(service prefix: `mediaconvert`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com//mediaconvert/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com//mediaconvert/latest/userguide/IAM_policies.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Elemental MediaConvert](#awselementalmediaconvert-actions-as-permissions)
+ [Resources Defined by MediaConvert](#awselementalmediaconvert-resources-for-iam-policies)
+ [Condition Keys for AWS Elemental MediaConvert](#awselementalmediaconvert-policy-keys)

## Actions Defined by AWS Elemental MediaConvert<a name="awselementalmediaconvert-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CancelJob.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CancelJob.html) | Cancel a mediaconvert job that is waiting in queue | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CreateJob.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CreateJob.html) | Create and submit a mediaconvert job | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CreateJob.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CreateJob.html) | Create a mediaconvert custom job template | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CreateJob.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CreateJob.html) | Create a mediaconvert custom output preset | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CreateQueue.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_CreateQueue.html) | Create a mediaconvert job queue | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_DeleteJobTemplate.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_DeleteJobTemplate.html) | Delete a mediaconvert custom job template | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_DeletePreset.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_DeletePreset.html) | Delete a mediaconvert custom output preset | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_DeleteQueue.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_DeleteQueue.html) | Delete a mediaconvert job queue | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_DescribeEndpoints.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_DescribeEndpoints.html) | Subscribe to mediaconvert service, returns one \(or more\) custom endpoints | List |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_GetJob.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_GetJob.html) | Get a mediaconvert job | Read |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_GetJobTemplate.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_GetJobTemplate.html) | Get a mediaconvert job template | Read |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_GetPreset.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_GetPreset.html) | Get a mediaconvert output preset | Read |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_GetQueue.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_GetQueue.html) | Get a mediaconvert job queue | Read |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_ListJobTemplates.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_ListJobTemplates.html) | List mediaconvert job templates | List |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_ListJobs.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_ListJobs.html) | List mediaconvert jobs | List |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_ListPresets.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_ListPresets.html) | List mediaconvert output presets | List |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_ListQueues.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_ListQueues.html) | List mediaconvert job queues | List |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_UpdateJobTemplate.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_UpdateJobTemplate.html) | Update a mediaconvert custom job template | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_UpdatePreset.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_UpdatePreset.html) | Update a mediaconvert custom output preset | Write |  |  |  | 
| [http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_UpdateQueue.html](http://docs.aws.amazon.com//mediaconvert/latest/APIReference/API_UpdateQueue.html) | Update a mediaconvert job queue | Write |  |  |  | 

## Resources Defined by MediaConvert<a name="awselementalmediaconvert-resources-for-iam-policies"></a>

MediaConvert has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Elemental MediaConvert<a name="awselementalmediaconvert-policy-keys"></a>

MediaConvert has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.