# Actions, Resources, and Condition Keys for AWS RoboMaker<a name="list_awsrobomaker"></a>

AWS RoboMaker \(service prefix: `robomaker`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/robomaker/latest/what-is-robomaker.html)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/robomaker/latest/API_Operations.html)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/robomaker/latest/what-is-robomaker.html) permission policies\.

**Topics**
+ [Actions Defined by AWS RoboMaker](#awsrobomaker-actions-as-permissions)
+ [Resources Defined by RoboMaker](#awsrobomaker-resources-for-iam-policies)
+ [Condition Keys for AWS RoboMaker](#awsrobomaker-policy-keys)

## Actions Defined by AWS RoboMaker<a name="awsrobomaker-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchDescribeSimulationJob ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_BatchDescribeSimulationJob.html)  | Describe multiple simulation jobs | Read |  |  |  | 
|   [ CancelSimulationJob ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CancelSimulationJob.html)  | End a simulation job | Write |  |  |  | 
|   [ CreateDeploymentJob ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CreateDeploymentJob.html)  | Create a deployment job | Write |  |  |   iam:CreateServiceLinkedRole   | 
|   [ CreateFleet ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CreateFleet.html)  | Create a fleet that represents a logical group of robots running the same robot application | Write |  |  |  | 
|   [ CreateRobot ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CreateRobot.html)  | Create a robot that can be registered to a fleet | Write |  |  |  | 
|   [ CreateRobotApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CreateRobotApplication.html)  | Create a robot application | Write |  |  |  | 
|   [ CreateRobotApplicationVersion ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CreateRobotApplicationVersion.html)  | Create a snapshot of a robot application | Write |  |  |   s3:GetObject   | 
|   [ CreateSimulationApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CreateSimulationApplication.html)  | Create a robot application | Write |  |  |  | 
|   [ CreateSimulationApplicationVersion ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CreateSimulationApplicationVersion.html)  | Create a snapshot of a robot application | Write |  |  |  | 
|   [ CreateSimulationJob ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_CreateSimulationJob.html)  | Create a simulation job | Write |  |  |   iam:CreateServiceLinkedRole   | 
|   [ DeleteRobot ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DeleteRobot.html)  | Delete a robot | Write |  |  |  | 
|   [ DeleteRobotApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DeleteRobotApplication.html)  | Delete a robot application | Write |  |  |  | 
|   [ DeleteSimulationApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DeleteSimulationApplication.html)  | Delete a robot application | Write |  |  |  | 
|   [ DeregisterRobot ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DeregisterRobot.html)  | Deregister a robot from a fleet | Write |  |  |  | 
|   [ DescribeDeploymentJob ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DescribeDeploymentJob.html)  | Describe a deployment job | Read |  |  |  | 
|   [ DescribeFleet ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DescribeFleet.html)  | Describe a fleet | Read |  |  |  | 
|   [ DescribeRobot ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DescribeRobot.html)  | Describe a robot | Read |  |  |  | 
|   [ DescribeRobotApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DescribeRobotApplication.html)  | Describe a robot application | Read |  |  |  | 
|   [ DescribeSimulationApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DescribeSimulationApplication.html)  | Describe a robot application | Read |  |  |  | 
|   [ DescribeSimulationJob ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_DescribeSimulationJob.html)  | Describe a simulation job | Read |  |  |  | 
|   [ ListDeploymentJobs ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_ListDeploymentJobs.html)  | List deployment jobs | List |  |  |  | 
|   [ ListFleets ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_ListFleets.html)  | List fleets | List |  |  |  | 
|   [ ListRobotApplications ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_ListRobotApplications.html)  | List robot applications | List |  |  |  | 
|   [ ListRobots ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_ListRobots.html)  | List robots | List |  |  |  | 
|   [ ListSimulationApplications ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_ListSimulationApplications.html)  | List robot applications | List |  |  |  | 
|   [ ListSimulationJobs ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_ListSimulationJobs.html)  | List simulation jobs | List |  |  |  | 
|   [ RegisterRobot ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_RegisterRobot.html)  | Register a robot to a fleet | Write |  |  |  | 
|   [ RestartSimulationJob ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_RestartSimulationJob.html)  | Restart a running simulation job | Write |  |  |  | 
|   [ SyncDeploymentJob ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_SyncDeploymentJob.html)  | Ensures the most recently deployed robot application is deployed to all robots in the fleet | Write |  |  |   iam:CreateServiceLinkedRole   | 
|   [ UpdateRobotApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_UpdateRobotApplication.html)  | Update a robot application | Write |  |  |  | 
|   [ UpdateSimulationApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Operations.htmlAPI_UpdateSimulationApplication.html)  | Update a robot application | Write |  |  |   s3:GetObject   | 

## Resources Defined by RoboMaker<a name="awsrobomaker-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsrobomaker-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ robotApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Types.htmlmanaging-robot-applications.html)  |  arn:$\{Partition\}:robomaker:<region>:<account>:robot\-application/<applicationName>/<createdOnEpoch>  |  | 
|   [ simulationApplication ](https://docs.aws.amazon.com/robomaker/latest/API_Types.htmlmanaging-simulation-applications.html)  |  arn:$\{Partition\}:robomaker:<region>:<account>:simulation\-application/<applicationName>/<createdOnEpoch>  |  | 
|   [ simulationJob ](https://docs.aws.amazon.com/robomaker/latest/API_Types.htmlsimulation.html)  |  arn:$\{Partition\}:robomaker:<region>:<account>:simulation\-job/<simulationJobId>  |  | 
|   [ deploymentJob ](https://docs.aws.amazon.com/robomaker/latest/API_Types.htmldeployment.html)  |  arn:$\{Partition\}:robomaker:<region>:<account>:deployment\-job/<deploymentJobId>  |  | 
|   [ robot ](https://docs.aws.amazon.com/robomaker/latest/API_Types.htmlmanaging-robots.html)  |  arn:$\{Partition\}:robomaker:<region>:<account>:robot/<robotName>/<createdOnEpoch>  |  | 

## Condition Keys for AWS RoboMaker<a name="awsrobomaker-policy-keys"></a>

RoboMaker has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.