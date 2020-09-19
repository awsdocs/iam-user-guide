# Actions, resources, and condition keys for AWS Key Management Service<a name="list_awskeymanagementservice"></a>

AWS Key Management Service \(service prefix: `kms`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/kms/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/kms/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/kms/latest/developerguide/control-access.html) permission policies\.

**Topics**
+ [Actions defined by AWS Key Management Service](#awskeymanagementservice-actions-as-permissions)
+ [Resource types defined by AWS Key Management Service](#awskeymanagementservice-resources-for-iam-policies)
+ [Condition keys for AWS Key Management Service](#awskeymanagementservice-policy-keys)

## Actions defined by AWS Key Management Service<a name="awskeymanagementservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awskeymanagementservice.html)

## Resource types defined by AWS Key Management Service<a name="awskeymanagementservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awskeymanagementservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ alias ](https://docs.aws.amazon.com/kms/latest/developerguide/programming-aliases.html)  |  arn:$\{Partition\}:kms:$\{Region\}:$\{Account\}:alias/$\{Alias\}  |  | 
|   [ key ](https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#master_keys)  |  arn:$\{Partition\}:kms:$\{Region\}:$\{Account\}:key/$\{KeyId\}  |  | 

## Condition keys for AWS Key Management Service<a name="awskeymanagementservice-policy-keys"></a>

AWS Key Management Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ kms:BypassPolicyLockoutSafetyCheck ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-bypass-policy-lockout-safety-check)  | Controls access to the CreateKey and PutKeyPolicy operations based on the value of the BypassPolicyLockoutSafetyCheck parameter in the request\. | Bool | 
|   [ kms:CallerAccount ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-caller-account)  | Controls access to specified AWS KMS operations based on the AWS account ID of the caller\. You can use this condition key to allow or deny access to all IAM users and roles in an AWS account in a single policy statement\. | String | 
|   [ kms:CustomerMasterKeySpec ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-customer-master-key-spec)  | Controls access to an API operation based on the CustomerMasterKeySpec property of the CMK that is created by or used in the operation\. Use it to qualify authorization of the CreateKey operation or any operation that is authorized for a CMK resource\. | String | 
|   [ kms:CustomerMasterKeyUsage ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-customer-master-key-usage)  | Controls access to an API operation based on the KeyUsage property of the CMK created by or used in the operation\. Use it to qualify authorization of the CreateKey operation or any operation that is authorized for a CMK resource\. | String | 
|   [ kms:DataKeyPairSpec ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-data-key-pair-spec)  | Controls access to GenerateDataKeyPair and GenerateDataKeyPairWithoutPlaintext operations based on the value of the DataKeyPairSpec parameter in the request\. | String | 
|   [ kms:EncryptionAlgorithm ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-algorithm)  | Controls access to encryption operations based on the value of the encryption algorithm in the request\. | String | 
|   [ kms:EncryptionContextKeys ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context-keys)  | Controls access based on the presence of specified keys in the encryption context\. The encryption context is an optional element in a cryptographic operation\. | String | 
|   [ kms:ExpirationModel ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-expiration-model)  | Controls access to the ImportKeyMaterial operation based on the value of the ExpirationModel parameter in the request\. | String | 
|   [ kms:GrantConstraintType ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-grant-constraint-type)  | Controls access to the CreateGrant operation based on the grant constraint in the request\. | String | 
|   [ kms:GrantIsForAWSResource ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-grant-is-for-aws-resource)  | Controls access to the CreateGrant operation when the request comes from a specified AWS service\. | Bool | 
|   [ kms:GrantOperations ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-grant-operations)  | Controls access to the CreateGrant operation based on the operations in the grant\. | String | 
|   [ kms:GranteePrincipal ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-grantee-principal)  | Controls access to the CreateGrant operation based on the grantee principal in the grant\. | String | 
|   [ kms:KeyOrigin ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-key-origin)  | Controls access to an API operation based on the Origin property of the CMK created by or used in the operation\. Use it to qualify authorization of the CreateKey operation or any operation that is authorized for a CMK resource\. | String | 
|   [ kms:MessageType ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-message-type)  | Controls access to the Sign and Verify operations based on the value of the MessageType parameter in the request\. | String | 
|   [ kms:ReEncryptOnSameKey ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-reencrypt-on-same-key)  | Controls access to the ReEncrypt operation when it uses the same customer master key that was used for the Encrypt operation\. | Bool | 
|   [ kms:RetiringPrincipal ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-retiring-principal)  | Controls access to the CreateGrant operation based on the retiring principal in the grant\. | String | 
|   [ kms:SigningAlgorithm ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-signing-algorithm)  | Controls access to the Sign and Verify operations based on the signing algorithm in the request\. | String | 
|   [ kms:ValidTo ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-valid-to)  | Controls access to the ImportKeyMaterial operation based on the value of the ValidTo parameter in the request\. You can use this condition key to allow users to import key material only when it expires by the specified date\. | Numeric | 
|   [ kms:ViaService ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-via-service)  | Controls access when a request made on the principal's behalf comes from a specified AWS service\. | String | 
|   [ kms:WrappingAlgorithm ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-wrapping-algorithm)  | Controls access to the GetParametersForImport operation based on the value of the WrappingAlgorithm parameter in the request\. | String | 
|   [ kms:WrappingKeySpec ](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-wrapping-key-spec)  | Controls access to the GetParametersForImport operation based on the value of the WrappingKeySpec parameter in the request\. | String | 