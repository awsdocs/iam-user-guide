# Actions, Resources, and Condition Keys for Single Sign\-On<a name="list_singlesign-on"></a>

Single Sign\-On \(service prefix: `sso`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/singlesignon/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/singlesignon/latest/userguide/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access.html) permission policies\.

**Topics**
+ [Actions Defined by Single Sign\-On](#singlesign-on-actions-as-permissions)
+ [Resources Defined by SSO](#singlesign-on-resources-for-iam-policies)
+ [Condition Keys for Single Sign\-On](#singlesign-on-policy-keys)

## Actions Defined by Single Sign\-On<a name="singlesign-on-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateDirectory ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Connect a directory to be used by AWS Single Sign\-On | Write |  |  |  | 
|   [ AssociateProfile ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create an association between a directory user or group and a profile | Write |  |  |  | 
|   [ CreateApplicationInstance ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Add an application instance to AWS Single Sign\-On | Write |  |  |  | 
|   [ CreateApplicationInstanceCertificate ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Add a new certificate for an application instance | Write |  |  |  | 
|   [ CreatePermissionSet ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create a permission set | Write |  |  |  | 
|   [ CreateProfile ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create a profile for an application instance | Write |  |  |  | 
|   [ CreateTrust ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Create a federation trust in a target account | Write |  |  |  | 
|   [ DeleteApplicationInstance ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete the application instance | Write |  |  |  | 
|   [ DeleteApplicationInstanceCertificate ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete an inactive or expired certificate from the application instance | Write |  |  |  | 
|   [ DeletePermissionSet ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete a permission set | Write |  |  |  | 
|   [ DeletePermissionsPolicy ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete the permission policy associated with a permission set | Write |  |  |  | 
|   [ DeleteProfile ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Delete the profile for an application instance | Write |  |  |  | 
|   [ DescribePermissionsPolicies ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all the permissions policies associated with a permission set | Read |  |  |  | 
|   [ DisassociateDirectory ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Disassociate a directory to be used by AWS Single Sign\-On | Write |  |  |  | 
|   [ DisassociateProfile ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Disassociate a directory user or group from a profile | Write |  |  |  | 
|   [ GetApplicationInstance ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve details for an application instance | Read |  |  |  | 
|   [ GetApplicationTemplate ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve application template details | Read |  |  |  | 
|   [ GetPermissionSet ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve details of a permission set | Read |  |  |  | 
|   [ GetPermissionsPolicy ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all permission policies associated with a permission set | Read |  |  |   sso:DescribePermissionsPolicies   | 
|   [ GetProfile ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve a profile for an application instance | Read |  |  |  | 
|   [ GetSSOStatus ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Check if AWS Single Sign\-On is enabled | Read |  |  |  | 
|   [ GetTrust ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve the federation trust in a target account | Read |  |  |  | 
|   [ ImportApplicationInstanceServiceProviderMetadata ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the application instance by uploading an application SAML metadata file provided by the service provider | Write |  |  |  | 
|   [ ListApplicationInstanceCertificates ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all of the certificates for a given application instance | Read |  |  |  | 
|   [ ListApplicationInstances ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all application instances | List |  |  |   sso:GetApplicationInstance   | 
|   [ ListApplicationTemplates ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all supported application templates | Read |  |  |   sso:GetApplicationTemplate   | 
|   [ ListApplications ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all supported applications | Read |  |  |  | 
|   [ ListDirectoryAssociations ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve details about the directory connected to AWS Single Sign\-On | Read |  |  |  | 
|   [ ListPermissionSets ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all permission sets | Read |  |  |  | 
|   [ ListProfileAssociations ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve the directory user or group associated with the profile | Read |  |  |  | 
|   [ ListProfiles ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Retrieve all profiles for an application instance | Read |  |  |   sso:GetProfile   | 
|   [ PutPermissionsPolicy ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Add a policy to a permission set | Write |  |  |  | 
|   [ SearchGroups ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Search for groups within the associated directory | Read |  |  |  | 
|   [ SearchUsers ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Search for users within the associated directory | Read |  |  |  | 
|   [ StartSSO ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Initialize AWS Single Sign\-On | Write |  |  |  | 
|   [ UpdateApplicationInstanceActiveCertificate ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Set a certificate as the active one for this application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceDisplayData ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update display data of an application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceResponseConfiguration ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update federation response configuration for the application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceResponseSchemaConfiguration ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update federation response schema configuration for the application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceSecurityConfiguration ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update security details for the application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceServiceProviderConfiguration ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update service provider related configuration for the application instance | Write |  |  |  | 
|   [ UpdateApplicationInstanceStatus ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the status of an application instance | Write |  |  |  | 
|   [ UpdateDirectoryAssociation ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the user attribute mappings for your connected directory | Write |  |  |  | 
|   [ UpdateProfile ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the profile for an application instance | Write |  |  |  | 
|   [ UpdateTrust ](http://docs.aws.amazon.com/singlesignon/latest/userguide/iam-auth-access-using-id-policies.html#policyexample)  | Update the federation trust in a target account | Write |  |  |  | 

## Resources Defined by SSO<a name="singlesign-on-resources-for-iam-policies"></a>

Single Sign\-On has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Single Sign\-On<a name="singlesign-on-policy-keys"></a>

SSO has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.