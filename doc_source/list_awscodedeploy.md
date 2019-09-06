# Actions, Resources, and Condition Keys for AWS CodeDeploy<a name="list_awscodedeploy"></a>

AWS CodeDeploy \(service prefix: `codedeploy`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/codedeploy/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/codedeploy/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/codedeploy/latest/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CodeDeploy](#awscodedeploy-actions-as-permissions)
+ [Resources Defined by AWS CodeDeploy](#awscodedeploy-resources-for-iam-policies)
+ [Condition Keys for AWS CodeDeploy](#awscodedeploy-policy-keys)

## Actions Defined by AWS CodeDeploy<a name="awscodedeploy-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddTagsToOnPremisesInstances ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_AddTagsToOnPremisesInstances.html)  | Add tags to one or more on\-premises instances\. | Tagging |   [ instance\* ](#awscodedeploy-instance)   |  |  | 
|   [ BatchGetApplicationRevisions ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetApplicationRevisions.html)  | Gets information about one or more application revisions\. | Read |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ BatchGetApplications ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetApplications.html)  | Get information about multiple applications associated with the IAM user\. | Read |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ BatchGetDeploymentGroups ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetDeploymentGroups.html)  | Get information about one or more deployment groups\. | Read |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ BatchGetDeploymentInstances ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetDeploymentInstances.html)  | Gets information about one or more instance that are part of a deployment group\. | Read |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ BatchGetDeployments ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetDeployments.html)  | Get information about multiple deployments associated with the IAM user\. | Read |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ BatchGetOnPremisesInstances ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_BatchGetOnPremisesInstances.html)  | Get information about one or more on\-premises instances\. | Read |   [ instance\* ](#awscodedeploy-instance)   |  |  | 
|   [ ContinueDeployment ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ContinueDeployment.html)  | Starts the process of rerouting traffic from instances in the original environment to instances in thereplacement environment without waiting for a specified wait time to elapse\. | Write |  |  |  | 
|   [ CreateApplication ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_CreateApplication.html)  | Create an application associated with the IAM user\. | Write |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ CreateDeployment ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_CreateDeployment.html)  | Create a deployment for an application associated with the IAM user\. | Write |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ CreateDeploymentConfig ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_CreateDeploymentConfig.html)  | Create a custom deployment configuration associated with the IAM user\. | Write |   [ deploymentconfig\* ](#awscodedeploy-deploymentconfig)   |  |  | 
|   [ CreateDeploymentGroup ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_CreateDeploymentGroup.html)  | Create a deployment group for an application associated with the IAM user\. | Write |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ DeleteApplication ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_DeleteApplication.html)  | Delete an application associated with the IAM user\. | Write |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ DeleteDeploymentConfig ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_DeleteDeploymentConfig.html)  | Delete a custom deployment configuration associated with the IAM user\. | Write |   [ deploymentconfig\* ](#awscodedeploy-deploymentconfig)   |  |  | 
|   [ DeleteDeploymentGroup ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_DeleteDeploymentGroup.html)  | Delete a deployment group for an application associated with the IAM user\. | Write |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ DeregisterOnPremisesInstance ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_DeregisterOnPremisesInstance.html)  | Deregister an on\-premises instance\. | Write |   [ instance\* ](#awscodedeploy-instance)   |  |  | 
|   [ GetApplication ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetApplication.html)  | Get information about a single application associated with the IAM user\. | List |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ GetApplicationRevision ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetApplicationRevision.html)  | Get information about a single application revision for an application associated with the IAM user\. | List |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ GetDeployment ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetDeployment.html)  | Get information about a single deployment to a deployment group for an application associated with the IAM user\. | List |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ GetDeploymentConfig ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetDeploymentConfig.html)  | Get information about a single deployment configuration associated with the IAM user\. | List |   [ deploymentconfig\* ](#awscodedeploy-deploymentconfig)   |  |  | 
|   [ GetDeploymentGroup ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetDeploymentGroup.html)  | Get information about a single deployment group for an application associated with the IAM user\. | List |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ GetDeploymentInstance ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetDeploymentInstance.html)  | Get information about a single instance in a deployment associated with the IAM user\. | List |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ GetOnPremisesInstance ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_GetOnPremisesInstance.html)  | Get information about a single on\-premises instance\. | List |   [ instance\* ](#awscodedeploy-instance)   |  |  | 
|   [ ListApplicationRevisions ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListApplicationRevisions.html)  | Get information about all application revisions for an application associated with the IAM user\. | List |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ ListApplications ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListApplications.html)  | Get information about all applications associated with the IAM user\. | List |  |  |  | 
|   [ ListDeploymentConfigs ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListDeploymentConfigs.html)  | Get information about all deployment configurations associated with the IAM user\. | List |  |  |  | 
|   [ ListDeploymentGroups ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListDeploymentGroups.html)  | Get information about all deployment groups for an application associated with the IAM user\. | List |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ ListDeploymentInstances ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListDeploymentInstances.html)  | Get information about all instances in a deployment associated with the IAM user\. | List |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ ListDeployments ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListDeployments.html)  | Get information about all deployments to a deployment group associated with the IAM user, or to get all deployments associated with the IAM user\. | List |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 
|   [ ListOnPremisesInstances ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_ListOnPremisesInstances.html)  | Get a list of one or more on\-premises instance names\. | List |  |  |  | 
|   [ PutLifecycleEventHookExecutionStatus ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_PutLifecycleEventHookExecutionStatus.html)  | Notify a lifecycle event hook execution status for associated deployment with the IAM user\. | Write |  |  |  | 
|   [ RegisterApplicationRevision ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_RegisterApplicationRevision.html)  | Register information about an application revision for an application associated with the IAM user\. | Write |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ RegisterOnPremisesInstance ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_RegisterOnPremisesInstance.html)  | Register an on\-premises instance\. | Write |   [ instance\* ](#awscodedeploy-instance)   |  |  | 
|   [ RemoveTagsFromOnPremisesInstances ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_RemoveTagsFromOnPremisesInstances.html)  | Remove tags from one or more on\-premises instances\. | Tagging |   [ instance\* ](#awscodedeploy-instance)   |  |  | 
|   [ StopDeployment ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_StopDeployment.html)  | Description for StopDeployment | Write |  |  |  | 
|   [ UpdateApplication ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_UpdateApplication.html)  | Description for UpdateApplication | Write |   [ application\* ](#awscodedeploy-application)   |  |  | 
|   [ UpdateDeploymentGroup ](https://docs.aws.amazon.com/codedeploy/latest/APIReference/API_UpdateDeploymentGroup.html)  | Change information about a single deployment group for an application associated with the IAM user\. | Write |   [ deploymentgroup\* ](#awscodedeploy-deploymentgroup)   |  |  | 

## Resources Defined by AWS CodeDeploy<a name="awscodedeploy-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodedeploy-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ application ](https://docs.aws.amazon.com/codedeploy/latest/userguide/auth-and-access-control-permissions-reference.html)  |  arn:$\{Partition\}:codedeploy:$\{Region\}:$\{Account\}:application:$\{ApplicationName\}  |  | 
|   [ deploymentconfig ](https://docs.aws.amazon.com/codedeploy/latest/userguide/auth-and-access-control-permissions-reference.html)  |  arn:$\{Partition\}:codedeploy:$\{Region\}:$\{Account\}:deploymentconfig:$\{DeploymentConfigurationName\}  |  | 
|   [ deploymentgroup ](https://docs.aws.amazon.com/codedeploy/latest/userguide/auth-and-access-control-permissions-reference.html)  |  arn:$\{Partition\}:codedeploy:$\{Region\}:$\{Account\}:deploymentgroup:$\{ApplicationName\}/$\{DeploymentGroupName\}  |  | 
|   [ instance ](https://docs.aws.amazon.com/codedeploy/latest/userguide/auth-and-access-control-permissions-reference.html)  |  arn:$\{Partition\}:codedeploy:$\{Region\}:$\{Account\}:instance:$\{InstanceName\}  |  | 

## Condition Keys for AWS CodeDeploy<a name="awscodedeploy-policy-keys"></a>

CodeDeploy has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.