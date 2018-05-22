# Actions, Resources, and Condition Keys for AWS Cloud9<a name="list_awscloud9"></a>

AWS Cloud9 \(service prefix: `cloud9`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by AWS Cloud9](#awscloud9-actions-as-permissions)
+ [Resources Defined by Cloud9](#awscloud9-resources-for-iam-policies)
+ [Condition Keys for AWS Cloud9](#awscloud9-policy-keys)

## Actions Defined by AWS Cloud9<a name="awscloud9-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_CreateEnvironmentEC2.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_CreateEnvironmentEC2.html) | Creates an AWS Cloud9 development environment, launches an Amazon Elastic Compute Cloud \(Amazon EC2\) instance, and then hosts the environment on the instance\. | Write |  | [cloud9:EnvironmentName](#awscloud9-cloud9_EnvironmentName) [cloud9:InstanceType](#awscloud9-cloud9_InstanceType) [cloud9:SubnetId](#awscloud9-cloud9_SubnetId) [cloud9:UserArn](#awscloud9-cloud9_UserArn)  |  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_CreateEnvironmentMembership.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_CreateEnvironmentMembership.html) | Adds an environment member to an AWS Cloud9 development environment\. | Write |  | [cloud9:UserArn](#awscloud9-cloud9_UserArn) [cloud9:EnvironmentId](#awscloud9-cloud9_EnvironmentId) [cloud9:Permissions](#awscloud9-cloud9_Permissions)  |  | 
| CreateEnvironmentSSH | Creates an AWS Cloud9 development environment, which is connected to a remote SSH server\. | Write |  | [cloud9:EnvironmentName](#awscloud9-cloud9_EnvironmentName)  |  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DeleteEnvironment.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DeleteEnvironment.html) | Deletes an AWS Cloud9 development environment\. If the environment is hosted on an Amazon Elastic Compute Cloud \(Amazon EC2\) instance, also terminates the instance\. | Write | [environment\*](#awscloud9-environment)  |  | iam:CreateServiceLinkedRole  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DeleteEnvironmentMembership.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DeleteEnvironmentMembership.html) | Deletes an environment member from an AWS Cloud9 development environment\. | Write |  |  |  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DescribeEnvironmentMemberships.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DescribeEnvironmentMemberships.html) | Gets information about environment members for an AWS Cloud9 development environment\. | Read |  | [cloud9:UserArn](#awscloud9-cloud9_UserArn) [cloud9:EnvironmentId](#awscloud9-cloud9_EnvironmentId)  |  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DescribeEnvironmentStatus.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DescribeEnvironmentStatus.html) | Gets status information for an AWS Cloud9 development environment\. | Read |  |  |  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DescribeEnvironments.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_DescribeEnvironments.html) | Gets information about AWS Cloud9 development environments\. | Read | [environment\*](#awscloud9-environment)  |  |  | 
| GetUserPublicKey | Gets the public key of the logged in user\. Only used in the AWS Cloud9 console\. | Read |  |  |  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_ListEnvironments.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_ListEnvironments.html) | Gets a list of AWS Cloud9 development environment identifiers\. | Read |  |  |  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_UpdateEnvironment.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_UpdateEnvironment.html) | Changes the settings of an existing AWS Cloud9 development environment\. | Write | [environment\*](#awscloud9-environment)  |  |  | 
| [http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_UpdateEnvironmentMembership.html](http://docs.aws.amazon.com///cloud9/latest/APIReferenceAPI_UpdateEnvironmentMembership.html) | Changes the settings of an existing environment member for an AWS Cloud9 development environment\. | Write |  | [cloud9:UserArn](#awscloud9-cloud9_UserArn) [cloud9:EnvironmentId](#awscloud9-cloud9_EnvironmentId) [cloud9:Permissions](#awscloud9-cloud9_Permissions)  |  | 
| ValidateEnvironmentName | Checks checks whether the passed in environment is valid\. Only used in the AWS Cloud9 console\. | Write |  |  |  | 

## Resources Defined by Cloud9<a name="awscloud9-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscloud9-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| environment | arn:$\{Partition\}:cloud9:$\{Region\}:$\{Account\}:environment:$\{ResourceId\} |  | 

## Condition Keys for AWS Cloud9<a name="awscloud9-policy-keys"></a>

AWS Cloud9 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| cloud9:InstanceType |  | String | 
| cloud9:SubnetId |  | String | 
| cloud9:UserArn |  | ARN | 
| cloud9:EnvironmentId |  | String | 
| cloud9:EnvironmentName |  | String | 
| cloud9:Permissions |  | String | 