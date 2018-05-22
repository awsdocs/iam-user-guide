# Actions, Resources, and Condition Keys for Amazon Elastic MapReduce<a name="list_amazonelasticmapreduce"></a>

Amazon Elastic MapReduce \(service prefix: `elasticmapreduce`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/emr/latest/ManagementGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-access.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Elastic MapReduce](#amazonelasticmapreduce-actions-as-permissions)
+ [Resources Defined by EMR](#amazonelasticmapreduce-resources-for-iam-policies)
+ [Condition Keys for Amazon Elastic MapReduce](#amazonelasticmapreduce-policy-keys)

## Actions Defined by Amazon Elastic MapReduce<a name="amazonelasticmapreduce-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_AddInstanceGroups.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_AddInstanceGroups.html) | Adds instance groups to a running cluster | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_AddJobFlowSteps.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_AddJobFlowSteps.html) | Adds new steps to a running job flow | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_AddTags.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_AddTags.html) | Adds tags to an Amazon EMR resource | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_CancelSteps.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_CancelSteps.html) | Cancels a pending step or steps in a running cluster | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_CreateSecurityConfiguration.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_CreateSecurityConfiguration.html) | Creates a security configuration which is stored in the service | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ DeleteSecurityConfiguration.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ DeleteSecurityConfiguration.html) | Deletes a security configuration | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_DescribeCluster.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_DescribeCluster.html) | Provides cluster\-level details including status, hardware and software configuration, VPC settings, and so on | Read |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_DescribeSecurityConfiguration.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_DescribeSecurityConfiguration.html) | Provides the details of a security configuration by returning the configuration JSON | Read |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_DescribeStep.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_DescribeStep.html) | Provides more detail about the cluster step | Read |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListBootstrapActions.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListBootstrapActions.html) | Provides information about the bootstrap actions associated with a cluster | List |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListClusters.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListClusters.html) | Provides the status of all clusters visible to this AWS account | List |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListInstanceGroups.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListInstanceGroups.html) | Provides all available details about the instance groups in a cluster | List |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListInstances.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListInstances.html) | Provides information about the cluster instances that Amazon EMR provisions on behalf of a user when it creates the cluster | List |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ ListSecurityConfigurations ](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ ListSecurityConfigurations ) |  Lists all the security configurations visible to this account, providing their creation dates and times, and their names | List |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListSteps.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ListSteps.html) | Provides a list of steps for the cluster | List |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ModifyInstanceGroups.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_ModifyInstanceGroups.html) | Modifies the number of nodes and configuration settings of an instance group | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_PutAutoScalingPolicy.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_PutAutoScalingPolicy.html) | Modifies the number of nodes and configuration settings of an instance group | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_RemoveAutoScalingPolicy.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_RemoveAutoScalingPolicy.html) | Removes an automatic scaling policy from a specified instance group within an EMR cluster | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_RemoveTags.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_RemoveTags.html) | Removes tags from an Amazon EMR resource | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_RunJobFlow.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_RunJobFlow.html) | Creates and starts running a new job flow | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_SetTerminationProtection.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_SetTerminationProtection.html) | Locks a job flow so the Amazon EC2 instances in the cluster cannot be terminated by user intervention, an API call, or in the event of a job\-flow error | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_SetVisibleToAllUsers.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_SetVisibleToAllUsers.html) | Sets whether all AWS Identity and Access Management \(IAM\) users under your account can access the specified job flows | Write |  |  |  | 
| [http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_TerminateJobFlows.html](http://docs.aws.amazon.com/ElasticMapReduce/latest/API/API_TerminateJobFlows.html) | Shuts a list of job flows down | Write |  |  |  | 
| ViewEventsFromAllClustersInConsole \[permission only\] | Use the console to view events from all clusters in a region | List |  |  |  | 

## Resources Defined by EMR<a name="amazonelasticmapreduce-resources-for-iam-policies"></a>

EMR has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Elastic MapReduce<a name="amazonelasticmapreduce-policy-keys"></a>

EMR has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.