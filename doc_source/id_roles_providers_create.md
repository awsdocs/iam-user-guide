# Creating IAM identity providers<a name="id_roles_providers_create"></a>

**Note**  
We recommend that you require your human users to use temporary credentials when accessing AWS\. Have you considered using AWS IAM Identity Center \(successor to AWS Single Sign\-On\)? You can use IAM Identity Center to centrally manage access to multiple AWS accounts and provide users with MFA\-protected, single sign\-on access to all their assigned accounts from one place\. With IAM Identity Center, you can create and manage user identities in IAM Identity Center or easily connect to your existing SAML 2\.0 compatible identity provider\. For more information, see [What is IAM Identity Center?](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html) in the *AWS IAM Identity Center \(successor to AWS Single Sign\-On\) User Guide*\.

You can use an external identity provider \(IdP\) to manage user identities outside of AWS\. An external IdP can provide identity information to AWS using either OpenID Connect \(OIDC\) or Security Assertion Markup Language \(SAML\)\. Examples of well\-known OIDC identity providers are: Login with Amazon, Facebook, and Google\. Examples of well\-known SAML identity providers are: Shibboleth and Active Directory Federation Services\.

When you want to configure federation with an external IdP, you create an IAM *identity provider* to inform AWS about the external IdP and its configuration\. This establishes "trust" between your AWS account and the external IdP\. The following topics include details about how to create an IAM identity provider for each of the external IdP types\.

**Topics**
+ [Creating OpenID Connect \(OIDC\) identity providers](id_roles_providers_create_oidc.md)
+ [Creating IAM SAML identity providers](id_roles_providers_create_saml.md)