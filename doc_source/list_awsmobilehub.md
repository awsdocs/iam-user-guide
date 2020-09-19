# Actions, resources, and condition keys for AWS Mobile Hub<a name="list_awsmobilehub"></a>

AWS Mobile Hub \(service prefix: `mobilehub`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/reference-mobile-hub-iam-auth-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS Mobile Hub](#awsmobilehub-actions-as-permissions)
+ [Resource types defined by AWS Mobile Hub](#awsmobilehub-resources-for-iam-policies)
+ [Condition keys for AWS Mobile Hub](#awsmobilehub-policy-keys)

## Actions defined by AWS Mobile Hub<a name="awsmobilehub-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateProject ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Create a project | Write |  |  |  | 
|   [ CreateServiceRole ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Enable AWS Mobile Hub in the account by creating the required service role | Write |  |  |  | 
|   [ DeleteProject ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Delete the specified project | Write |   [ project\* ](#awsmobilehub-project)   |  |  | 
|   [ DeleteProjectSnapshot ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Delete a saved snapshot of project configuration | Write |  |  |  | 
|   [ DeployToStage ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Deploy changes to the specified stage | Write |  |  |  | 
|   [ DescribeBundle ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Describe the download bundle | Read |  |  |  | 
|   [ ExportBundle ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Export the download bundle | Read |  |  |  | 
|   [ ExportProject ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Export the project configuration | Read |   [ project\* ](#awsmobilehub-project)   |  |  | 
|   [ GenerateProjectParameters ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Generate project parameters required for code generation | Write |   [ project\* ](#awsmobilehub-project)   |  |  | 
|   [ GetProject ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Get project configuration and resources | Read |   [ project\* ](#awsmobilehub-project)   |  |  | 
|   [ GetProjectSnapshot ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Fetch the previously exported project configuration snapshot | Read |  |  |  | 
|   [ ImportProject ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Create a new project from the previously exported project configuration | Write |  |  |  | 
|   [ InstallBundle ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Install a bundle in the project deployments S3 bucket | Write |  |  |  | 
|   [ ListAvailableConnectors ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | List the available SaaS \(Software as a Service\) connectors | List |  |  |  | 
|   [ ListAvailableFeatures ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | List available features | List |  |  |  | 
|   [ ListAvailableRegions ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | List available regions for projects | List |  |  |  | 
|   [ ListBundles ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | List the available download bundles | List |  |  |  | 
|   [ ListProjectSnapshots ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | List saved snapshots of project configuration | List |  |  |  | 
|   [ ListProjects ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | List projects | List |  |  |  | 
|   [ SynchronizeProject ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Synchronize state of resources into project | Write |   [ project\* ](#awsmobilehub-project)   |  |  | 
|   [ UpdateProject ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Update project | Write |   [ project\* ](#awsmobilehub-project)   |  |  | 
|   [ ValidateProject ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Validate a mobile hub project\. | Read |  |  |  | 
|   [ VerifyServiceRole ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html)  | Verify AWS Mobile Hub is enabled in the account | Read |  |  |  | 

## Resource types defined by AWS Mobile Hub<a name="awsmobilehub-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsmobilehub-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ project ](https://docs.aws.amazon.com/mobile-hub/latest/developerguide/reference-mobile-hub-iam-managed-policies.html)  |  arn:$\{Partition\}:mobilehub:$\{Region\}:$\{Account\}:project/$\{ProjectId\}  |  | 

## Condition keys for AWS Mobile Hub<a name="awsmobilehub-policy-keys"></a>

Mobile Hub has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.