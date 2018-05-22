# Actions, Resources, and Condition Keys for AWS Serverless Application Repository<a name="list_awsserverlessapplicationrepository"></a>

AWS Serverless Application Repository \(service prefix: `serverlessrepo`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by AWS Serverless Application Repository](#awsserverlessapplicationrepository-actions-as-permissions)
+ [Resources Defined by Serverless Application Repository](#awsserverlessapplicationrepository-resources-for-iam-policies)
+ [Condition Keys for AWS Serverless Application Repository](#awsserverlessapplicationrepository-policy-keys)

## Actions Defined by AWS Serverless Application Repository<a name="awsserverlessapplicationrepository-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| CreateApplication | Creates an application, optionally including an AWS SAM file to create the first application version in the same call\. | Write |  |  |  | 
| CreateApplicationVersion | Creates an application version\. | Write |  |  |  | 
| CreateCloudFormationChangeSet | Creates an AWS CloudFormation ChangeSet for the given application\. | Write |  |  |  | 
| DeleteApplication | Delete the specified Application | Write |  |  |  | 
| GetApplication | Gets the specified application\. | Read |  |  |  | 
| GetApplicationPolicy | Gets the policy for the specified application\. | Read |  |  |  | 
| ListApplicationVersions | Lists versions for the specified application owned by the requester\. | List |  |  |  | 
| ListApplications | Lists applications owned by the requester\. | List |  |  |  | 
| PutApplicationPolicy | Puts the policy for the specified application\. | Write |  |  |  | 
| SearchApplications | Gets all applications authorized for this user | Read |  |  |  | 
| UpdateApplication | Updates meta\-data of the application | Write |  |  |  | 

## Resources Defined by Serverless Application Repository<a name="awsserverlessapplicationrepository-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsserverlessapplicationrepository-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| applications | arn:$\{Partition\}:serverlessrepo:$\{Region\}:$\{Account\}:applications/$\{ResourceId\} |  | 

## Condition Keys for AWS Serverless Application Repository<a name="awsserverlessapplicationrepository-policy-keys"></a>

Serverless Application Repository has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.