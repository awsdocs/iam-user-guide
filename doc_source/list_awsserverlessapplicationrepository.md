# Actions, Resources, and Condition Keys for AWS Serverless Application Repository<a name="list_awsserverlessapplicationrepository"></a>

AWS Serverless Application Repository \(service prefix: `serverlessrepo`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by AWS Serverless Application Repository](#awsserverlessapplicationrepository-actions-as-permissions)
+ [Resources Defined by AWS Serverless Application Repository](#awsserverlessapplicationrepository-resources-for-iam-policies)
+ [Condition Keys for AWS Serverless Application Repository](#awsserverlessapplicationrepository-policy-keys)

## Actions Defined by AWS Serverless Application Repository<a name="awsserverlessapplicationrepository-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   CreateApplication  | Creates an application, optionally including an AWS SAM file to create the first application version in the same call\. | Write |  |  |  | 
|   CreateApplicationVersion  | Creates an application version\. | Write |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   CreateCloudFormationChangeSet  | Creates an AWS CloudFormation ChangeSet for the given application\. | Write |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   CreateCloudFormationTemplate  | Creates an AWS CloudFormation template | Write |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   DeleteApplication  | Delete the specified Application | Write |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   GetApplication  | Gets the specified application\. | Read |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   GetApplicationPolicy  | Gets the policy for the specified application\. | Read |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   GetCloudFormationTemplate  | Gets the specified AWS CloudFormation template | Read |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   ListApplicationDependencies  | Retrieves the list of applications nested in the containing application | List |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   ListApplicationVersions  | Lists versions for the specified application owned by the requester\. | List |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   ListApplications  | Lists applications owned by the requester\. | List |  |  |  | 
|   PutApplicationPolicy  | Puts the policy for the specified application\. | Write |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 
|   SearchApplications  | Gets all applications authorized for this user | Read |  |  |  | 
|   UpdateApplication  | Updates meta\-data of the application | Write |   [ applications\* ](#awsserverlessapplicationrepository-applications)   |  |  | 

## Resources Defined by AWS Serverless Application Repository<a name="awsserverlessapplicationrepository-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsserverlessapplicationrepository-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   applications  |  arn:$\{Partition\}:serverlessrepo:$\{Region\}:$\{Account\}:applications/$\{ResourceId\}  |  | 

## Condition Keys for AWS Serverless Application Repository<a name="awsserverlessapplicationrepository-policy-keys"></a>

Serverless Application Repository has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.