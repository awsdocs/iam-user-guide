# Actions, Resources, and Condition Keys for Amazon CodeGuru Profiler<a name="list_amazoncodeguruprofiler"></a>

Amazon CodeGuru Profiler \(service prefix: `codeguru-profiler`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/codeguru/latest/profiler-ug/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/codeguru/latest/profiler-api/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/codeguru/latest/profiler-ug/security-iam.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon CodeGuru Profiler](#amazoncodeguruprofiler-actions-as-permissions)
+ [Resource Types Defined by Amazon CodeGuru Profiler](#amazoncodeguruprofiler-resources-for-iam-policies)
+ [Condition Keys for Amazon CodeGuru Profiler](#amazoncodeguruprofiler-policy-keys)

## Actions Defined by Amazon CodeGuru Profiler<a name="amazoncodeguruprofiler-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ ConfigureAgent ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_ConfigureAgent.html) \[permission only\] | Grants permission for an agent to register with the orchestration service and retrieve profiling configuration information | Write |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ CreateProfilingGroup ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_CreateProfilingGroup.html)  | Grants permission to create a profiling group | Write |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ DeleteProfilingGroup ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_DeleteProfilingGroup.html)  | Grants permission to delete a profiling group | Write |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ DescribeProfilingGroup ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_DescribeProfilingGroup.html)  | Grants permission to describe a profiling group | Read |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ GetFindingsReport ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_GetFindingsReport.html)  | Grants permission to get a recommendations report | Read |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ GetFindingsReportAccountSummary ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_GetFindingsReportAccountSummary.html)  | Grants permission to get a summary of recent recommendations for each profiling group in the account | Read |  |  |  | 
|   [ GetPolicy ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_GetPolicy.html)  | Grants permission to get the resource policy associated with the specified Profiling Group\. | Read |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ GetProfile ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_GetProfile.html)  | Grants permission to get aggregated profiles for a specific profiling group | Read |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ ListFindingsReports ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_ListFindingsReports.html)  | Grants permissions to list the available recommendations reports for a specific profiling group | List |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ ListProfileTimes ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_ListProfileTimes.html)  | Grants permissions to list the start times of the available aggregated profiles for a specific profiling group | List |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ ListProfilingGroups ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_ListProfilingGroups.html)  | Grants permissions to list profiling groups in the account | List |  |  |  | 
|   [ PostAgentProfile ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_PostAgentProfile.html) \[permission only\] | Grants permissions to submit a profile collected by an agent belonging to a specific profiling group for aggregation | Write |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ PutPermission ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_PutPermission.html)  | Grants permissions to update the list of principals allowed for an action group in the resource policy associated with the specified Profiling Group\. | Permissions management |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ RemovePermission ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_RemovePermission.html)  | Grants permission to remove the permission of specified Action Group from the resource policy associated with the specified Profiling Group\. | Permissions management |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 
|   [ UpdateProfilingGroup ](https://docs.aws.amazon.com/codeguru/latest/profiler-api/API_UpdateProfilingGroup.html)  | Grants permissions to update a specific profiling group | Write |   [ ProfilingGroup\* ](#amazoncodeguruprofiler-ProfilingGroup)   |  |  | 

## Resource Types Defined by Amazon CodeGuru Profiler<a name="amazoncodeguruprofiler-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncodeguruprofiler-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ ProfilingGroup ](https://docs.aws.amazon.com/codeguru/latest/profiler-ug/working-with-profiling-groups.html)  |  arn:$\{Partition\}:codeguru\-profiler:$\{Region\}:$\{Account\}:profilingGroup/$\{profilingGroupName\}  |  | 

## Condition Keys for Amazon CodeGuru Profiler<a name="amazoncodeguruprofiler-policy-keys"></a>

CodeGuru Profiler has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.