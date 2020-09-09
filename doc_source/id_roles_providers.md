# Identity providers and federation<a name="id_roles_providers"></a>

If you already manage user identities outside of AWS, you can use IAM *identity providers* instead of creating IAM users in your AWS account\. With an identity provider \(IdP\), you can manage your user identities outside of AWS and give these external user identities permissions to use AWS resources in your account\. This is useful if your organization already has its own identity system, such as a corporate user directory\. It is also useful if you are creating a mobile app or web application that requires access to AWS resources\.

When you use an IAM identity provider, you don't have to create custom sign\-in code or manage your own user identities\. The IdP provides that for you\. Your external users sign in through a well\-known IdP, such as Login with Amazon, Facebook, or Google\. You can give those external identities permissions to use AWS resources in your account\. IAM identity providers help keep your AWS account secure because you don't have to distribute or embed long\-term security credentials, such as access keys, in your application\.

To use an IdP, you create an IAM identity provider entity to establish a trust relationship between your AWS account and the IdP\. IAM supports IdPs that are compatible with [OpenID Connect \(OIDC\)](http://openid.net/connect/) or [SAML 2\.0 \(Security Assertion Markup Language 2\.0\)](https://wiki.oasis-open.org/security)\. For more information about using one of these IdPs with AWS, see the following sections: 
+ [About web identity federation](id_roles_providers_oidc.md)
+ [About SAML 2\.0\-based federation](id_roles_providers_saml.md)

For details about creating the IAM identity provider entity to establish a trust relationship between a compatible IdP and AWS, see [Creating IAM identity providers](id_roles_providers_create.md)