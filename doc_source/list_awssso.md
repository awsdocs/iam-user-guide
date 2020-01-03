# Actions, Resources, and Condition Keys for AWS SSO<a name="list_awssso"></a>

AWS SSO \(service prefix: `sso`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/singlesignon/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/singlesignon/latest/userguide/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access.html) permission policies\.

**Topics**
+ [Actions Defined by AWS SSO](#awssso-actions-as-permissions)
+ [Resource Types Defined by AWS SSO](#awssso-resources-for-iam-policies)
+ [Condition Keys for AWS SSO](#awssso-policy-keys)

## Actions Defined by AWS SSO<a name="awssso-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Connect a directory to be used by AWS Single Sign\-On | Write |  |  |  | 
|   [ AssociateProfile ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create an association between a directory user or group and a profile | Write |  |  |  | 
|   [ CreateApplicationInstance ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Add an application instance to AWS Single Sign\-On | Write |  |  |  | 
|   [ CreateApplicationInstanceCertificate ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Add a new certificate for an application instance | Write |  |  |  | 
|   [ CreateManagedApplicationInstance ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Add a managed application instance to AWS Single Sign\-On | Write |  |  |  | 
|   [ CreatePermissionSet ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create a permission set | Write |  |  |  | 
|   [ CreateProfile ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create a profile for an application instance | Write |  |  |  | 
|   [ CreateTrust ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create a federation trust in a target account | Write |  |  |  | 
|   [ DeleteApplicationInstance ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete the application instance | Write |  |  |  | 
|   [ DeleteApplicationInstanceCertificate ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete an inactive or expired certificate from the application instance | Write |  |  |  | 
|   [ DeleteManagedApplicationInstance ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete the managed application instance | Write |  |  |  | 
|   [ DeletePermissionSet ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete a permission set | Write |  |  |  | 
|   [ DeletePermissionsPolicy ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete the permission policy associated with a permission set | Write |  |  |  | 
|   [ DeleteProfile ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete the profile for an application instance | Write |  |  |  | 
|   [ DescribePermissionsPolicies ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all the permissions policies associated with a permission set | Read |  |  |  | 
|   [ DisassociateDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Disassociate a directory to be used by AWS Single Sign\-On | Write |  |  |  | 
|   [ DisassociateProfile ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Disassociate a directory user or group from a profile | Write |  |  |  | 
|   [ GetApplicationInstance ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve details for an application instance | Read |  |  |  | 
|   [ GetApplicationTemplate ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve application template details | Read |  |  |  | 
|   [ GetManagedApplicationInstance ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve details for an application instance | Read |  |  |  | 
|   [ GetMfaDeviceManagementForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve Mfa Device Management settings for the directory | Read |  |  |  | 
|   [ GetPermissionSet ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve details of a permission set | Read |  |  |  | 
|   [ GetPermissionsPolicy ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all permission policies associated with a permission set | Read |  |  |   sso:DescribePermissionsPolicies   | 
|   [ GetProfile ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve a profile for an application instance | Read |  |  |  | 
|   [ GetSSOStatus ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Check if AWS Single Sign\-On is enabled | Read |  |  |  | 
|   [ GetSharedSsoConfiguration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve shared configuration for the current SSO instance | Read |  |  |  | 
|   [ GetSsoConfiguration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve configuration for the current SSO instance | Read |  |  |  | 
|   [ GetTrust ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve the federation trust in a target account | Read |  |  |  | 
|   [ ImportApplicationInstanceServiceProviderMetadata ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the application instance by uploading an application SAML metadata file provided by the service provider | Write |  |  |  | 
|   [ ListApplicationInstanceCertificates ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all of the certificates for a given application instance | Read |  |  |  | 
|   [ ListApplicationInstances ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all application instances | List |  |  |   sso:GetApplicationInstance   | 
|   [ ListApplicationTemplates ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all supported application templates | Read |  |  |   sso:GetApplicationTemplate   | 
|   [ ListApplications ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all supported applications | Read |  |  |  | 
|   [ ListDirectoryAssociations ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve details about the directory connected to AWS Single Sign\-On | Read |  |  |  | 
|   [ ListPermissionSets ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all permission sets | Read |  |  |  | 
|   [ ListProfileAssociations ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve the directory user or group associated with the profile | Read |  |  |  | 
|   [ ListProfiles ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all profiles for an application instance | Read |  |  |   sso:GetProfile   | 
|   [ PutMfaDeviceManagementForDirectory ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Put Mfa Device Management settings for the directory | Write |  |  |  | 
|   [ PutPermissionsPolicy ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Add a policy to a permission set | Write |  |  |  | 
|   [ StartSSO ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Initialize AWS Single Sign\-On | Write |  |  |  | 
|   [ UpdateApplicationInstanceActiveCertificate ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Set a certificate as the active one for this application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceDisplayData ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update display data of an application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceResponseConfiguration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update federation response configuration for the application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceResponseSchemaConfiguration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update federation response schema configuration for the application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceSecurityConfiguration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update security details for the application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceServiceProviderConfiguration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update service provider related configuration for the application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceStatus ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the status of an application instance | Write |  |  |  | 
|   [ UpdateDirectoryAssociation ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the user attribute mappings for your connected directory | Write |  |  |  | 
|   [ UpdateManagedApplicationInstanceStatus ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the status of a managed application instance | Write |  |  |  | 
|   [ UpdatePermissionSet ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the permission set\. | Write |  |  |  | 
|   [ UpdateProfile ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the profile for an application instance | Write |  |  |  | 
|   [ UpdateSSOConfiguration ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the configuration for the current SSO instance | Write |  |  |  | 
|   [ UpdateTrust ](https://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the federation trust in a target account | Write |  |  |  | 

## Resource Types Defined by AWS SSO<a name="awssso-resources-for-iam-policies"></a>

AWS SSO does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS SSO, specify `“Resource”: “*”` in your policy\.

## Condition Keys for AWS SSO<a name="awssso-policy-keys"></a>

SSO has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.