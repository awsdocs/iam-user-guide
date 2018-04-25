# Actions, Resources, and Condition Keys for AWS Secrets Manager<a name="list_awssecretsmanager"></a>

AWS Secrets Manager \(service prefix: `secretsmanager`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/secretsmanager/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/secretsmanager/latest/userguide/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/secretsmanager/latest/userguide/auth-and-access.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Secrets Manager](#awssecretsmanager-actions-as-permissions)
+ [Resources Defined by Secrets Manager](#awssecretsmanager-resources-for-iam-policies)
+ [Condition Keys for AWS Secrets Manager](#awssecretsmanager-policy-keys)

## Actions Defined by AWS Secrets Manager<a name="awssecretsmanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [CancelRotateSecret](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to cancel an in\-progress secret rotation\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [CreateSecret](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to create a secret that stores encrypted data that can be queried and rotated\. |   |  |  |  | 
| [DeleteSecret](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to delete a secret\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [DescribeSecret](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to retrieve the metadata about a secret, but not the encrypted data\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [GetRandomPassword](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to generate a random string for use in passowrd creation\. |   |  |  |  | 
| [GetSecretValue](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to retrieve and decrypt the encrypted data\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [ListSecretVersionIds](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to list the available versions of a secret\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [ListSecrets](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to list the available secrets\. |   |  |  |  | 
| [PutSecretValue](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to create a new version of the secret with new encrypted data\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [RestoreSecret](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to cancel deletion of a secret\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [RotateSecret](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to start rotation of a secret\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [TagResource](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to add tags to a secret\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [UntagResource](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to remove tags from a secret\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [UpdateSecret](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to update a secret with new metadata or with a new version of the encrypted data\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 
| [UpdateSecretVersionStage](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-actions) | Enables the user to move a stage from one secret to another\. |   | [Secret\*](#awssecretsmanager-Secret)  |  |  | 

## Resources Defined by Secrets Manager<a name="awssecretsmanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awssecretsmanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [Secret](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-resources) | arn:$\{Partition\}:secretsmanager:$\{Region\}:$\{Account\}:secret:$\{SecretId\} |  | 

## Condition Keys for AWS Secrets Manager<a name="awssecretsmanager-policy-keys"></a>

AWS Secrets Manager defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [secretsmanager:SecretId](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-contextkeys) | Filters access by the SecretID value in the request\. | ARN | 
| [secretsmanager:Name](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-contextkeys) | Filters access by the friendly name of the secret in the request\. | String | 
| [secretsmanager:Description](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-contextkeys) | Filters access by the description text in the request\. | String | 
| [secretsmanager:KmsKeyId](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-contextkeys) | Filters access by the ARN of the KMS key in the request\. | String | 
| [secretsmanager:VersionId](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-contextkeys) | Filters access by the unique identifier of the version of the secret in the request\. | String | 
| [secretsmanager:VersionStage](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-contextkeys) | Filters access by the list of version stages in the request\. | String | 
| [secretsmanager:RotationLambdaARN](http://docs.aws.amazon.com/secretsmanager/latest/userguide/reference_iam-permissions.html#iam-contextkeys) | Filters access by the ARN of the rotation Lambda function in the request\. | ARN | 