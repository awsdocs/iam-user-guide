# Actions, Resources, and Condition Keys for AWS CloudHSM<a name="list_awscloudhsm"></a>

AWS CloudHSM \(service prefix: `cloudhsm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/cloudhsm/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/cloudhsm/latest/userguide/iam-policy.html) permission policies\.

**Topics**
+ [Actions Defined by AWS CloudHSM](#awscloudhsm-actions-as-permissions)
+ [Resources Defined by CloudHSM](#awscloudhsm-resources-for-iam-policies)
+ [Condition Keys for AWS CloudHSM](#awscloudhsm-policy-keys)

## Actions Defined by AWS CloudHSM<a name="awscloudhsm-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_AddTagsToResource.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_AddTagsToResource.html) | Adds or overwrites one or more tags for the specified AWS CloudHSM resource | Tagging |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_CreateHapg.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_CreateHapg.html) | Creates a high\-availability partition group | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_CreateHsm.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_CreateHsm.html) | Creates an uninitialized HSM instance | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_CreateLunaClient.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_CreateLunaClient.html) | Creates an HSM client | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DeleteHapg.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DeleteHapg.html) | Deletes a high\-availability partition group | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DeleteHsm.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DeleteHsm.html) | Deletes an HSM\. After completion, this operation cannot be undone and your key material cannot be recovered | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DeleteLunaClient.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DeleteLunaClient.html) | Deletes a client | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DescribeHapg.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DescribeHapg.html) | Retrieves information about a high\-availability partition group | Read |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DescribeHsm.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DescribeHsm.html) | Retrieves information about an HSM\. You can identify the HSM by its ARN or its serial number | Read |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DescribeLunaClient.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_DescribeLunaClient.html) | Retrieves information about an HSM client | Read |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_GetConfig.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_GetConfig.html) | Gets the configuration files necessary to connect to all high availability partition groups the client is associated with | Read |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListAvailableZones.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListAvailableZones.html) | Lists the Availability Zones that have available AWS CloudHSM capacity | List |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListHapgs.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListHapgs.html) | Lists the high\-availability partition groups for the account | List |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListHsms.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListHsms.html) | Retrieves the identifiers of all of the HSMs provisioned for the current customer | List |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListLunaClients.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListLunaClients.html) | Lists all of the clients | List |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListTagsForResource.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ListTagsForResource.html) | Returns a list of all tags for the specified AWS CloudHSM resource | Read |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ModifyHapg.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ModifyHapg.html) | Modifies an existing high\-availability partition group | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ModifyHsm.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ModifyHsm.html) | Modifies an HSM | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ModifyLunaClient.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_ModifyLunaClient.html) | Modifies the certificate used by the client | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_RemoveTagsFromResource.html](http://docs.aws.amazon.com/cloudhsm/classic/APIReference/API_RemoveTagsFromResource.html) | Removes one or more tags from the specified AWS CloudHSM resource | Tagging |  |  |  | 

## Resources Defined by CloudHSM<a name="awscloudhsm-resources-for-iam-policies"></a>

CloudHSM has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS CloudHSM<a name="awscloudhsm-policy-keys"></a>

CloudHSM has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.