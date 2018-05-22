# Actions, Resources, and Condition Keys for Amazon Cognito Identity<a name="list_amazoncognitoidentity"></a>

Amazon Cognito Identity \(service prefix: `cognito-identity`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/cognito/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/cognito/latest/developerguide/cognito-identity.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Cognito Identity](#amazoncognitoidentity-actions-as-permissions)
+ [Resources Defined by Cognito Identity](#amazoncognitoidentity-resources-for-iam-policies)
+ [Condition Keys for Amazon Cognito Identity](#amazoncognitoidentity-policy-keys)

## Actions Defined by Amazon Cognito Identity<a name="amazoncognitoidentity-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_CreateIdentityPool.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_CreateIdentityPool.html) | Creates a new identity pool\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_DeleteIdentities.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_DeleteIdentities.html) | Deletes identities from an identity pool\. You can specify a list of 1\-60 identities that you want to delete\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_DeleteIdentityPool.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_DeleteIdentityPool.html) | Deletes a user pool\. Once a pool is deleted, users will not be able to authenticate with the pool\. | Write | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_DescribeIdentity.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_DescribeIdentity.html) | Returns metadata related to the given identity, including when the identity was created and any associated linked logins\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_DescribeIdentityPool.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_DescribeIdentityPool.html) | Gets details about a particular identity pool, including the pool name, ID description, creation date, and current number of users\. | Read | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetCredentialsForIdentity.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetCredentialsForIdentity.html) | Returns credentials for the provided identity ID\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetId.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetId.html) | Generates \(or retrieves\) a Cognito ID\. Supplying multiple logins will create an implicit linked account\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetIdentityPoolRoles.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetIdentityPoolRoles.html) | Gets the roles for an identity pool\. | Read | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetOpenIdToken.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetOpenIdToken.html) | Gets an OpenID token, using a known Cognito ID\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetOpenIdTokenForDeveloperIdentity.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_GetOpenIdTokenForDeveloperIdentity.html) | Registers \(or retrieves\) a Cognito IdentityId and an OpenID Connect token for a user authenticated by your backend authentication process\. | Read | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_ListIdentities.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_ListIdentities.html) | Lists the identities in a pool\. | List | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_ListIdentityPools.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_ListIdentityPools.html) | Lists all of the Cognito identity pools registered for your account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_LookupDeveloperIdentity.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_LookupDeveloperIdentity.html) | Retrieves the IdentityID associated with a DeveloperUserIdentifier or the list of DeveloperUserIdentifiers associated with an IdentityId for an existing identity\. | Read | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_MergeDeveloperIdentities.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_MergeDeveloperIdentities.html) | Merges two users having different IdentityIds, existing in the same identity pool, and identified by the same developer provider\. | Write | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_SetIdentityPoolRoles.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_SetIdentityPoolRoles.html) | Sets the roles for an identity pool\. These roles are used when making calls to GetCredentialsForIdentity action\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_UnlinkDeveloperIdentity.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_UnlinkDeveloperIdentity.html) | Unlinks a DeveloperUserIdentifier from an existing identity\. | Write | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_UnlinkIdentity.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_UnlinkIdentity.html) | Unlinks a federated identity from an existing account\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_UpdateIdentityPool.html](http://docs.aws.amazon.com/cognitoidentity/latest/APIReference/API_UpdateIdentityPool.html) | Updates a user pool\. | Write | [identitypool\*](#amazoncognitoidentity-identitypool)  |  |  | 

## Resources Defined by Cognito Identity<a name="amazoncognitoidentity-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncognitoidentity-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/cognito/latest/developerguide/identity-pools.html](http://docs.aws.amazon.com/cognito/latest/developerguide/identity-pools.html) | arn:$\{Partition\}:cognito\-identity:$\{Region\}:$\{Account\}:identitypool/$\{IdentityPoolId\} |  | 

## Condition Keys for Amazon Cognito Identity<a name="amazoncognitoidentity-policy-keys"></a>

Cognito Identity has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.