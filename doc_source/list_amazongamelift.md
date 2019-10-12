# Actions, Resources, and Condition Keys for Amazon GameLift<a name="list_amazongamelift"></a>

Amazon GameLift \(service prefix: `gamelift`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/gamelift/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/gamelift/latest/apireference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/gamelift/latest/developerguide/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon GameLift](#amazongamelift-actions-as-permissions)
+ [Resources Defined by Amazon GameLift](#amazongamelift-resources-for-iam-policies)
+ [Condition Keys for Amazon GameLift](#amazongamelift-policy-keys)

## Actions Defined by Amazon GameLift<a name="amazongamelift-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AcceptMatch ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_AcceptMatch.html)  | Registers player acceptance or rejection of a proposed FlexMatch match\. | Write |  |  |  | 
|   [ CreateAlias ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateAlias.html)  | Defines a new alias for a fleet\. | Write |  |  |  | 
|   [ CreateBuild ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateBuild.html)  | Creates a new game build using files stored in an Amazon S3 bucket\. | Write |  |  |  | 
|   [ CreateFleet ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateFleet.html)  | Creates a new fleet of computing resources to run your game servers\. | Write |  |  |  | 
|   [ CreateGameSession ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateGameSession.html)  | Starts a new game session on a specified fleet\. | Write |  |  |  | 
|   [ CreateGameSessionQueue ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateGameSessionQueue.html)  | Sets up a new queue for processing new game session placement requests\. | Write |  |  |  | 
|   [ CreateMatchmakingConfiguration ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateMatchmakingConfiguration.html)  | Creates a new FlexMatch matchmaker\. | Write |  |  |  | 
|   [ CreateMatchmakingRuleSet ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateMatchmakingRuleSet.html)  | Creates a new matchmaking rule set for FlexMatch\. | Write |  |  |  | 
|   [ CreatePlayerSession ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreatePlayerSession.html)  | Reserves an available game session slot for a player\. | Write |  |  |  | 
|   [ CreatePlayerSessions ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreatePlayerSessions.html)  | Reserves available game session slots for multiple players\. | Write |  |  |  | 
|   [ CreateScript ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateScript.html)  | Creates a new Realtime Servers script\. | Write |  |  |  | 
|   [ CreateVpcPeeringAuthorization ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateVpcPeeringAuthorization.html)  | Allows GameLift to create or delete a peering connection between a GameLift fleet VPC and a VPC on another AWS account\. | Write |  |  |  | 
|   [ CreateVpcPeeringConnection ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_CreateVpcPeeringConnection.html)  | Establishes a peering connection between your GameLift fleet VPC and a VPC on another account\. | Write |  |  |  | 
|   [ DeleteAlias ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteAlias.html)  | Deletes an alias\. | Write |  |  |  | 
|   [ DeleteBuild ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteBuild.html)  | Deletes a game build\. | Write |  |  |  | 
|   [ DeleteFleet ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteFleet.html)  | Deletes an empty fleet\. | Write |  |  |  | 
|   [ DeleteGameSessionQueue ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteGameSessionQueue.html)  | Deletes an existing game session queue\. | Write |  |  |  | 
|   [ DeleteMatchmakingConfiguration ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteMatchmakingConfiguration.html)  | Deletes an existing FlexMatch matchmaker\. | Write |  |  |  | 
|   [ DeleteMatchmakingRuleSet ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteMatchmakingRuleSet.html)  | Deletes an existing FlexMatch matchmaking rule set\. | Write |  |  |  | 
|   [ DeleteScalingPolicy ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteScalingPolicy.html)  | Deletes a set of auto\-scaling rules\. | Write |  |  |  | 
|   [ DeleteScript ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteScript.html)  | Deletes a Realtime Servers script\. | Write |  |  |  | 
|   [ DeleteVpcPeeringAuthorization ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteVpcPeeringAuthorization.html)  | Cancels a VPC peering authorization\. | Write |  |  |  | 
|   [ DeleteVpcPeeringConnection ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DeleteVpcPeeringConnection.html)  | Removes a peering connection between VPCs\. | Write |  |  |  | 
|   [ DescribeAlias ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeAlias.html)  | Retrieves properties for an alias\. | Read |  |  |  | 
|   [ DescribeBuild ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeBuild.html)  | Retrieves properties for a game build\. | Read |  |  |  | 
|   [ DescribeEC2InstanceLimits ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeEC2InstanceLimits.html)  | Retrieves the maximum allowed and current usage for EC2 instance types\. | Read |  |  |  | 
|   [ DescribeFleetAttributes ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetAttributes.html)  | Retrieves general properties, including status, for fleets\. | Read |  |  |  | 
|   [ DescribeFleetCapacity ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetCapacity.html)  | Retrieves the current capacity setting for fleets\. | Read |  |  |  | 
|   [ DescribeFleetEvents ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetEvents.html)  | Retrieves entries from a fleet's event log\. | Read |  |  |  | 
|   [ DescribeFleetPortSettings ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetPortSettings.html)  | Retrieves the inbound connection permissions for a fleet\. | Read |  |  |  | 
|   [ DescribeFleetUtilization ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeFleetUtilization.html)  | Retrieves utilization statistics for fleets\. | Read |  |  |  | 
|   [ DescribeGameSessionDetails ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeGameSessionDetails.html)  | Retrieves properties for game sessions in a fleet, including the protection policy\. | Read |  |  |  | 
|   [ DescribeGameSessionPlacement ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeGameSessionPlacement.html)  | Retrieves details of a game session placement request\. | Read |  |  |  | 
|   [ DescribeGameSessionQueues ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeGameSessionQueues.html)  | Retrieves properties for game session queues\. | Read |  |  |  | 
|   [ DescribeGameSessions ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeGameSessions.html)  | Retrieves properties for game sessions in a fleet\. | Read |  |  |  | 
|   [ DescribeInstances ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeInstances.html)  | Retrieves information about instances in a fleet\. | Read |  |  |  | 
|   [ DescribeMatchmaking ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeMatchmaking.html)  | Retrieves details of matchmaking tickets\. | Read |  |  |  | 
|   [ DescribeMatchmakingConfigurations ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeMatchmakingConfigurations.html)  | Retrieves properties for FlexMatch matchmakers\. | Read |  |  |  | 
|   [ DescribeMatchmakingRuleSets ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeMatchmakingRuleSets.html)  | Retrieves properties for FlexMatch matchmaking rule sets\. | Read |  |  |  | 
|   [ DescribePlayerSessions ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribePlayerSessions.html)  | Retrieves properties for player sessions in a game session\. | Read |  |  |  | 
|   [ DescribeRuntimeConfiguration ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeRuntimeConfiguration.html)  | Retrieves the current runtime configuration for a fleet\. | Read |  |  |  | 
|   [ DescribeScalingPolicies ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeScalingPolicies.html)  | Retrieves all scaling policies that are applied to a fleet\. | Read |  |  |  | 
|   [ DescribeScript ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeScript.html)  | Retrieves properties for a Realtime Servers script\. | Read |  |  |  | 
|   [ DescribeVpcPeeringAuthorizations ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeVpcPeeringAuthorizations.html)  | Retrieves valid VPC peering authorizations\. | Read |  |  |  | 
|   [ DescribeVpcPeeringConnections ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_DescribeVpcPeeringConnections.html)  | Retrieves details on active or pending VPC peering connections\. | Read |  |  |  | 
|   [ GetGameSessionLogUrl ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_GetGameSessionLogUrl.html)  | Retrieves the location of stored logs for a game session\. | Read |  |  |  | 
|   [ GetInstanceAccess ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_GetInstanceAccess.html)  | Requests remote access to a specified fleet instance\. | Read |  |  |  | 
|   [ ListAliases ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_ListAliases.html)  | Retrieves all aliases that are defined in the current region\. | List |  |  |  | 
|   [ ListBuilds ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_ListBuilds.html)  | Retrieves all game build in the current region\. | List |  |  |  | 
|   [ ListFleets ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_ListFleets.html)  | Retrieves a list of fleet IDs for all fleets in the current region\. | List |  |  |  | 
|   [ ListScripts ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_ListScripts.html)  | Retrieves properties for all Realtime Servers scripts in the current region\. | List |  |  |  | 
|   [ PutScalingPolicy ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_PutScalingPolicy.html)  | Creates or updates a fleet auto\-scaling policy\. | Write |  |  |  | 
|   [ RequestUploadCredentials ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_RequestUploadCredentials.html)  | Retrieves fresh upload credentials to use when uploading a new game build\. | Read |  |  |  | 
|   [ ResolveAlias ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_ResolveAlias.html)  | Retrieves the fleet ID associated with an alias\. | Read |  |  |  | 
|   [ SearchGameSessions ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_SearchGameSessions.html)  | Retrieves game sessions that match a set of search criteria\. | Read |  |  |  | 
|   [ StartFleetActions ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_StartFleetActions.html)  | Resumes auto\-scaling activity on a fleet after it was suspended with StopFleetActions\(\)\. | Write |  |  |  | 
|   [ StartGameSessionPlacement ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_StartGameSessionPlacement.html)  | Sends a game session placement request to a game session queue\. | Write |  |  |  | 
|   [ StartMatchBackfill ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_StartMatchBackfill.html)  | Requests FlexMatch matchmaking to fill available player slots in an existing game session\. | Write |  |  |  | 
|   [ StartMatchmaking ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_StartMatchmaking.html)  | Requests FlexMatch matchmaking for one or a group of players and game session placement for a resulting match\. | Write |  |  |  | 
|   [ StopFleetActions ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_StopFleetActions.html)  | Suspends auto\-scaling activity on a fleet\. | Write |  |  |  | 
|   [ StopGameSessionPlacement ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_StopGameSessionPlacement.html)  | Cancels a game session placement request that is in progress\. | Write |  |  |  | 
|   [ StopMatchmaking ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_StopMatchmaking.html)  | Cancels a matchmaking or match backfill request that is in progress\. | Write |  |  |  | 
|   [ UpdateAlias ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateAlias.html)  | Updates the properties of an existing alias\. | Write |  |  |  | 
|   [ UpdateBuild ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateBuild.html)  | Updates an existing build's metadata\. | Write |  |  |  | 
|   [ UpdateFleetAttributes ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetAttributes.html)  | Updates the general properties of an existing fleet\. | Write |  |  |  | 
|   [ UpdateFleetCapacity ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetCapacity.html)  | Adjusts a fleet's capacity settings\. | Write |  |  |  | 
|   [ UpdateFleetPortSettings ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateFleetPortSettings.html)  | Adjusts a fleet's port settings\. | Write |  |  |  | 
|   [ UpdateGameSession ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateGameSession.html)  | Updates the properties of an existing game session\. | Write |  |  |  | 
|   [ UpdateGameSessionQueue ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateGameSessionQueue.html)  | Updates properties of an existing game session queue\. | Write |  |  |  | 
|   [ UpdateMatchmakingConfiguration ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateMatchmakingConfiguration.html)  | Updates properties of an existing FlexMatch matchmaking configuration\. | Write |  |  |  | 
|   [ UpdateRuntimeConfiguration ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateRuntimeConfiguration.html)  | Updates how server processes are configured on instances in an existing fleet\. | Write |  |  |  | 
|   [ UpdateScript ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_UpdateScript.html)  | Updates the metadata and content of an existing Realtime Servers script\. | Write |  |  |  | 
|   [ ValidateMatchmakingRuleSet ](https://docs.aws.amazon.com/gamelift/latest/apireference/API_ValidateMatchmakingRuleSet.html)  | Validates the syntax of a FlexMatch matchmaking rule set\. | Read |  |  |  | 

## Resources Defined by Amazon GameLift<a name="amazongamelift-resources-for-iam-policies"></a>

Amazon GameLift does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon GameLift, specify `“Resource”: “*”` in your policy\.

## Condition Keys for Amazon GameLift<a name="amazongamelift-policy-keys"></a>

GameLift has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.