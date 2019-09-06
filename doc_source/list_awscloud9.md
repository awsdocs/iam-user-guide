# Actions, Resources, and Condition Keys for AWS Cloud9<a name="list_awscloud9"></a>

AWS Cloud9 \(service prefix: `cloud9`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/cloud9/latest/user-guide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/cloud9/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/cloud9/latest/user-guide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Cloud9](#awscloud9-actions-as-permissions)
+ [Resources Defined by AWS Cloud9](#awscloud9-resources-for-iam-policies)
+ [Condition Keys for AWS Cloud9](#awscloud9-policy-keys)

## Actions Defined by AWS Cloud9<a name="awscloud9-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateEnvironmentEC2 ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_CreateEnvironmentEC2.html)  | Grants permission to create an AWS Cloud9 development environment, launches an Amazon Elastic Compute Cloud \(Amazon EC2\) instance, and then hosts the environment on the instance\. | Write |  |   [ cloud9:EnvironmentName ](#awscloud9-cloud9_EnvironmentName)   [ cloud9:InstanceType ](#awscloud9-cloud9_InstanceType)   [ cloud9:SubnetId ](#awscloud9-cloud9_SubnetId)   [ cloud9:UserArn ](#awscloud9-cloud9_UserArn)   |   ec2:DescribeSubnets   ec2:DescribeVpcs   iam:CreateServiceLinkedRole   | 
|   [ CreateEnvironmentMembership ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_CreateEnvironmentMembership.html)  | Grants permission to add an environment member to an AWS Cloud9 development environment\. | Write |  |   [ cloud9:UserArn ](#awscloud9-cloud9_UserArn)   [ cloud9:EnvironmentId ](#awscloud9-cloud9_EnvironmentId)   [ cloud9:Permissions ](#awscloud9-cloud9_Permissions)   |  | 
|   [ DeleteEnvironment ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_DeleteEnvironment.html)  | Grants permission to delete an AWS Cloud9 development environment\. If the environment is hosted on an Amazon Elastic Compute Cloud \(Amazon EC2\) instance, also terminates the instance\. | Write |   [ environment\* ](#awscloud9-environment)   |  |   iam:CreateServiceLinkedRole   | 
|   [ DeleteEnvironmentMembership ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_DeleteEnvironmentMembership.html)  | Grants permission to delete an environment member from an AWS Cloud9 development environment\. | Write |  |  |  | 
|   [ DescribeEnvironmentMemberships ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_DescribeEnvironmentMemberships.html)  | Grants permission to get information about environment members for an AWS Cloud9 development environment\. | Read |  |   [ cloud9:UserArn ](#awscloud9-cloud9_UserArn)   [ cloud9:EnvironmentId ](#awscloud9-cloud9_EnvironmentId)   |  | 
|   [ DescribeEnvironmentStatus ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_DescribeEnvironmentStatus.html)  | Grants permission to get status information for an AWS Cloud9 development environment\. | Read |  |  |  | 
|   [ DescribeEnvironments ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_DescribeEnvironments.html)  | Grants permission to get information about AWS Cloud9 development environments\. | Read |   [ environment\* ](#awscloud9-environment)   |  |  | 
|   [ ListEnvironments ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_ListEnvironments.html)  | Grants permission to get a list of AWS Cloud9 development environment identifiers\. | Read |  |  |  | 
|   [ UpdateEnvironment ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_UpdateEnvironment.html)  | Grants permission to change the settings of an existing AWS Cloud9 development environment\. | Write |   [ environment\* ](#awscloud9-environment)   |  |  | 
|   [ UpdateEnvironmentMembership ](https://docs.aws.amazon.com/cloud9/latest/APIReference/API_UpdateEnvironmentMembership.html)  | Grants permission to change the settings of an existing environment member for an AWS Cloud9 development environment\. | Write |  |   [ cloud9:UserArn ](#awscloud9-cloud9_UserArn)   [ cloud9:EnvironmentId ](#awscloud9-cloud9_EnvironmentId)   [ cloud9:Permissions ](#awscloud9-cloud9_Permissions)   |  | 

## Resources Defined by AWS Cloud9<a name="awscloud9-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloud9-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ environment ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloud9.html#awscloud9-environment)  |  arn:$\{Partition\}:cloud9:$\{Region\}:$\{Account\}:environment:$\{ResourceId\}  |  | 

## Condition Keys for AWS Cloud9<a name="awscloud9-policy-keys"></a>

AWS Cloud9 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ cloud9:EnvironmentId ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloud9.html#awscloud9-cloud9_EnvironmentId)  | Filters access by the AWS Cloud9 environment ID | String | 
|   [ cloud9:EnvironmentName ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloud9.html#awscloud9-cloud9_EnvironmentName)  | Filters access by the AWS Cloud9 environment name | String | 
|   [ cloud9:InstanceType ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloud9.html#awscloud9-cloud9_InstanceType)  | Filters access by the instance type of the AWS Cloud9 environment's Amazon EC2 instance | String | 
|   [ cloud9:Permissions ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloud9.html#awscloud9-cloud9_Permissions)  | Filters access by the type of AWS Cloud9 permissions | String | 
|   [ cloud9:SubnetId ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloud9.html#awscloud9-cloud9_SubnetId)  | Filters access by the subnet ID that the AWS Cloud9 environment will be created in | String | 
|   [ cloud9:UserArn ](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awscloud9.html#awscloud9-cloud9_UserArn)  | Filters access by the user ARN specified | ARN | 