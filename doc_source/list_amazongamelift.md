# Actions, Resources, and Condition Keys for Amazon GameLift<a name="list_amazongamelift"></a>

Amazon GameLift \(service prefix: `gamelift`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/gamelift/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/gamelift/latest/apireference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/gamelift/latest/developerguide/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon GameLift](#amazongamelift-actions-as-permissions)
+ [Resources Defined by GameLift](#amazongamelift-resources-for-iam-policies)
+ [Condition Keys for Amazon GameLift](#amazongamelift-policy-keys)

## Actions Defined by Amazon GameLift<a name="amazongamelift-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateAlias.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateAlias.html) | Creates an alias for a fleet | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateBuild.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateBuild.html) | Initializes a new build record and generates information required to upload a game build to Amazon GameLift | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateFleet.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateFleet.html) | Creates a new fleet of computing resources to run your game servers | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateGameSession.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateGameSession.html) | Creates a game session for players to join | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreatePlayerSession.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreatePlayerSession.html) | Adds a player to a game session | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreatePlayerSessions.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_CreatePlayerSessions.html) | Adds a group of players to a game session | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteAlias.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteAlias.html) | Deletes an alias | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteBuild.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteBuild.html) | Deletes a build | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteFleet.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteFleet.html) | Deletes an empty fleet | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteScalingPolicy.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteScalingPolicy.html) | Deletes a set of scaling rules | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeAlias.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeAlias.html) | Retrieves properties for an alias | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeBuild.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeBuild.html) | Retrieves properties for a build | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeEC2InstanceLimits.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeEC2InstanceLimits.html) | Retrieves maximum allowed usage and current usage for all EC2 instance types or a specified type | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetAttributes.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetAttributes.html) | Retrieves general fleet properties for a fleet | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetCapacity.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetCapacity.html) | Retrieves the current capacity status for a fleet | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetEvents.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetEvents.html) | Retrieves entries from a fleet's event log | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetPortSettings.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetPortSettings.html) | Retrieves the inbound connection permissions set for a fleet | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetUtilization.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetUtilization.html) | Retrieves utilization statistics for a fleet | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeGameSessionDetails.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeGameSessionDetails.html) | Retrieves game session properties plus game session protection policy | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeGameSessions.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeGameSessions.html) | Retrieves game session properties for a fleet | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeInstances.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeInstances.html) | Retrieves information about a fleet's instances, including instance IDs\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribePlayerSessions.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribePlayerSessions.html) | Retrieves player session properties for a game session | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeRuntimeConfiguration.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeRuntimeConfiguration.html) | Retrieves the runtime configuration for a fleet | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeScalingPolicies.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeScalingPolicies.html) | Retrieves all scaling policies applied to a fleet | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_GetGameSessionLogUrl.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_GetGameSessionLogUrl.html) | Retrieves the location of stored logs for a game session | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_GetInstanceAccess.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_GetInstanceAccess.html) | Requests remote access to a fleet instance\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_ListAliases.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_ListAliases.html) | Retrieves the fleet aliases used with this AWS account | List |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_ListBuilds.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_ListBuilds.html) | Retrieves the builds for this AWS account | List |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_ListFleets.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_ListFleets.html) | Retrieves the fleet for this AWS account | List |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_PutScalingPolicy.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_PutScalingPolicy.html) | Creates or updates a fleet scaling policy | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_RequestUploadCredentials.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_RequestUploadCredentials.html) | Retrieves a fresh set of upload credentials and the Amazon S3 storage location for a specific build | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_ResolveAlias.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_ResolveAlias.html) | Retrieves the fleet ID associated with an alias | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_SearchGameSessions.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_SearchGameSessions.html) | Retrieves game sessions that match the search criteria and sorts them as specified | Read |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateAlias.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateAlias.html) | Updates properties for an alias | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateBuild.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateBuild.html) | Updates a build's name and version | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetAttributes.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetAttributes.html) | Sets a fleet's general properties | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetCapacity.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetCapacity.html) | Sets a fleet's capacity settings | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetPortSettings.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetPortSettings.html) | Sets a fleet's port settings | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateGameSession.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateGameSession.html) | Sets game session properties | Write |  |  |  | 
| [http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateRuntimeConfiguration.html](http://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateRuntimeConfiguration.html) | Sets a fleet's runtime configuration, which specifies how to launch server processes on the fleet | Write |  |  |  | 

## Resources Defined by GameLift<a name="amazongamelift-resources-for-iam-policies"></a>

GameLift has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon GameLift<a name="amazongamelift-policy-keys"></a>

GameLift has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.