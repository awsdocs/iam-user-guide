# Actions and Condition Context Keys for AWS Security Token Service<a name="list_sts"></a>

AWS Security Token Service \(service prefix: sts\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS Security Token Service**

For information about using the following AWS STS API actions in an IAM policy, see [Granting Permissions to Create Temporary Security Credentials](http://docs.aws.amazon.com/STS/latest/UsingSTS/STSPermission.html) in the *Using Temporary Security Credentials*\.
+ `[sts:AssumeRole](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html)`
+ `[sts:AssumeRoleWithSAML](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html)`
+ `[sts:AssumeRoleWithWebIdentity](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithWebIdentity.html)`
+ `[sts:DecodeAuthorizationMessage](http://docs.aws.amazon.com/STS/latest/APIReference/API_DecodeAuthorizationMessage.html)`
+ `[sts:GetCallerIdentity](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetCallerIdentity.html)`
+ `[sts:GetFederationToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)`
+ `[sts:GetSessionToken](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html)`

**Condition context keys for AWS Security Token Service**

AWS Security Token Service has the following service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.
+ `<web-identity-provider>:aud`
+ `<web-identity-provider>:oaud`
+ `<web-identity-provider>:sub`
+ `aws:FederatedProvider`
+ `saml:aud`
+ `saml:doc`
+ `saml:iss`
+ `saml:namequalifier`
+ `saml:sub`
+ `saml:sub_type`