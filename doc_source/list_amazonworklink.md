# Actions, Resources, and Condition Keys for Amazon WorkLink<a name="list_amazonworklink"></a>

Amazon WorkLink \(service prefix: `worklink`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/worklink/latest/developerguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/worklink/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/worklink/latest/developerguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon WorkLink](#amazonworklink-actions-as-permissions)
+ [Resources Defined by WorkLink](#amazonworklink-resources-for-iam-policies)
+ [Condition Keys for Amazon WorkLink](#amazonworklink-policy-keys)

## Actions Defined by Amazon WorkLink<a name="amazonworklink-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateWebsiteCertificateAuthority ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_AssociateWebsiteCertificateAuthority.html)  | Associates cert with a specified fleet\. | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ CreateFleet ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_CreateFleet.html)  | Creates a worklink fleet\. | Write |  |  |  | 
|   [ DeleteFleet ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_DeleteFleet.html)  | Deletes the worklink fleet\. | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeCompanyNetworkConfiguration ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_DescribeCompanyNetworkConfiguration.html)  | Describes company network configuration for a specified fleet\. | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeDevice ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_DescribeDevice.html)  | Describes a specific device associated with the fleet\. | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeDevicePolicyConfiguration ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_DescribeDevicePolicyConfiguration.html)  | Describes device policy configuration for a specified fleet\. | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeFleetMetadata ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_DescribeFleetMetadata.html)  | Describes metadata of a specified fleet\. | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeIdentityProviderConfiguration ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_DescribeIdentityProviderConfiguration.html)  | Describes identity provider configuration for a specified fleet\. | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DescribeWebsiteCertificateAuthority ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_DescribeWebsiteCertificateAuthority.html)  | Describes the cert of a specified fleet\. | Read |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ DisassociateWebsiteCertificateAuthority ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_DisassociateWebsiteCertificateAuthority.html)  | Disassociates cert with a specified fleet\. | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ ListDevices ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_ListDevices.html)  | Lists all the devices associated with the fleet\. | List |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ ListFleets ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_ListFleets.html)  | Lists all the fleets associated with the account\. | List |  |  |  | 
|   [ ListWebsiteCertificateAuthorities ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_ListWebsiteCertificateAuthorities.html)  | Lists all the certs associated with the specified fleet\. | List |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ SignOutUser ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_SignOutUser.html)  | Signs out the specified user in a fleet\. | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateCompanyNetworkConfiguration ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_UpdateCompanyNetworkConfiguration.html)  | Updates company network configuration for a specified fleet\. | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateDevicePolicyConfiguration ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_UpdateDevicePolicyConfiguration.html)  | Updates device policy configuration for a specified fleet\. | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateFleetMetadata ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_UpdateFleetMetadata.html)  | Updates metadata of a specified fleet\. | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 
|   [ UpdateIdentityProviderConfiguration ](https://docs.aws.amazon.com/worklink/latest/APIReference/API_UpdateIdentityProviderConfiguration.html)  | Updates identity provider configuration for a specified fleet\. | Write |   [ fleet\* ](#amazonworklink-fleet)   |  |  | 

## Resources Defined by WorkLink<a name="amazonworklink-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonworklink-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ fleet ](https://docs.aws.amazon.com/worklink/latest/developerguide/worklink-resources.html#Fleet)  |  arn:$\{Partition\}:worklink::$\{Account\}:fleet/$\{fleetName\}  |  | 

## Condition Keys for Amazon WorkLink<a name="amazonworklink-policy-keys"></a>

WorkLink has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.