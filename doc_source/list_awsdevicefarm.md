# Actions, Resources, and Condition Keys for AWS Device Farm<a name="list_awsdevicefarm"></a>

AWS Device Farm \(service prefix: `devicefarm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/devicefarm/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/devicefarm/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/devicefarm/latest/developerguide/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Device Farm](#awsdevicefarm-actions-as-permissions)
+ [Resources Defined by Device Farm](#awsdevicefarm-resources-for-iam-policies)
+ [Condition Keys for AWS Device Farm](#awsdevicefarm-policy-keys)

## Actions Defined by AWS Device Farm<a name="awsdevicefarm-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateDevicePool.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateDevicePool.html) | Creates a device pool | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateProject.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateProject.html) | Creates a new project | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateProject.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateProject.html) | Specifies and starts a remote access session | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateUpload.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateUpload.html) | Creates a new project | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateUpload.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_CreateUpload.html) | Deletes a device pool given the pool ARN\. Does not allow deletion of curated pools owned by the system | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeleteProject.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeleteProject.html) | Deletes an AWS Device Farm project, given the project ARN | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeleteRemoteAccessSession.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeleteRemoteAccessSession.html) | Deletes a completed remote access session and its results | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeleteRun.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeleteRun.html) | Deletes the run, given the run ARN | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeleteUpload.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_DeleteUpload.html) | Deletes an upload given the upload ARN | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetAccountSettings.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetAccountSettings.html) | Returns the number of unmetered iOS and/or unmetered Android devices that have been purchased by the account | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetDevice.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetDevice.html) | Gets information about a unique device type | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetDevicePool.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetDevicePool.html) | Gets information about a device pool | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetDevicePoolCompatibility.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetDevicePoolCompatibility.html) | Gets information about compatibility with a device pool | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetJob.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetJob.html) | Gets information about a job | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetOfferingStatus.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetOfferingStatus.html) | Gets the current status and future status of all offerings purchased by an AWS account | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetProject.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetProject.html) | Gets information about a project | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetRemoteAccessSession.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetRemoteAccessSession.html) | Returns a link to a currently running remote access session | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetRun.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetRun.html) | Gets information about a run | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetSuite.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetSuite.html) | Gets information about a suite | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetTest.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetTest.html) | Gets information about a test | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetUpload.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_GetUpload.html) | Gets information about an upload | Read |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_InstallToRemoteAccessSession.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_InstallToRemoteAccessSession.html) | Installs an application to the device in a remote access session | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListArtifacts.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListArtifacts.html) | Gets information about artifacts | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListDevicePools.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListDevicePools.html) | Gets information about device pools | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListDevices.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListDevices.html) | Gets information about unique device types | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListJobs.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListJobs.html) | Gets information about jobs | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListOfferingTransactions.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListOfferingTransactions.html) | Returns a list of all historical purchases, renewals, and system renewal transactions for an AWS account | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListOfferings.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListOfferings.html) | Returns a list of products or offerings that the user can manage through the API | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListProjects.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListProjects.html) | Gets information about projects | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListRemoteAccessSessions.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListRemoteAccessSessions.html) | Returns a list of all currently running remote access sessions | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListRuns.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListRuns.html) | Gets information about runs | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListSamples.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListSamples.html) | Gets information about samples | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListSuites.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListSuites.html) | Gets information about suites | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListTests.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListTests.html) | Gets information about tests | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListUniqueProblems.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListUniqueProblems.html) | Gets information about unique problems | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListUploads.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ListUploads.html) | Gets information about uploads | List |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_PurchaseOffering.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_PurchaseOffering.html) | Immediately purchases offerings for an AWS account | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_RenewOffering.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_RenewOffering.html) | Explicitly sets the quantity of devices to renew for an offering, starting from the effectiveDate of the next period | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ScheduleRun.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_ScheduleRun.html) | Schedules a run | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_StopRemoteAccessSession.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_StopRemoteAccessSession.html) | Ends a specified remote access session | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_StopRun.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_StopRun.html) | Initiates a stop request for the current test run | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_UpdateDevicePool.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_UpdateDevicePool.html) | Modifies the name, description, and rules in a device pool given the attributes and the pool ARN | Write |  |  |  | 
| [http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_UpdateProject.html](http://docs.aws.amazon.com/devicefarm/latest/APIReference/API_UpdateProject.html) | Modifies the specified project name, given the project ARN and a new name | Write |  |  |  | 

## Resources Defined by Device Farm<a name="awsdevicefarm-resources-for-iam-policies"></a>

Device Farm has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Device Farm<a name="awsdevicefarm-policy-keys"></a>

Device Farm has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.