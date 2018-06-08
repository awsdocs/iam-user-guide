# Creating a Role for a Third\-Party Identity Provider \(Federation\)<a name="id_roles_create_for-idp"></a>

Identity federation provides access to AWS resources to users by means of a third\-party identity provider \(IdP\)\. To set up identity federation, you configure the provider and then create an IAM role that determines what permissions a federated user will have\. For more information about federation and identity providers, see [Identity Providers and Federation](id_roles_providers.md)\.

## Creating a Role for Federated Users \(Console\)<a name="roles-creatingrole-federated-users-console"></a>

The steps for creating a role for federated users depend on your choice of third\-party providers:
+ To create a role for users federated with a Web Identity or OpenID Connect \(OIDC\) IdP, see [Creating a Role for Web Identity or OpenID Connect Federation \(Console\)](id_roles_create_for-idp_oidc.md)\.
+ To create a role for users federated with a SAML 2\.0 IdP, see [Creating a Role for SAML 2\.0 Federation \(Console\)](id_roles_create_for-idp_saml.md)\.

## Creating a Role for Federated Access \(AWS CLI\)<a name="roles-creatingrole-identityprovider-cli"></a>

The steps to create a role for the supported identity providers \(OIDC or SAML\) from the AWS CLI are identical\. The difference is in the contents of the trust policy that you create in the prerequisite steps\. Begin by following the steps in the **Prerequisites** section for the type of provider you are using:
+ For an OIDC provider, follow the steps in [Prerequisites for an OIDC provider](id_roles_create_for-idp_oidc.md#oidc-prereqs)\.
+ For a SAML provider, follow the steps in [Prerequisites for a SAML provider](id_roles_create_for-idp_saml.md#saml-prereqs)\.

Creating a role from the AWS CLI involves multiple steps\. When you use the console to create a role, many of the steps are done for you, but with the AWS CLI you must explicitly perform each step yourself\. You must create the trust policy first, create the role, and then assign a permission policy to the role\.

**To create a role \(AWS CLI\)**

1. To create a role: [http://docs.aws.amazon.com/cli/latest/reference/iam/create-role.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-role.html)

1. To attach a permission policy to the role:

   [http://docs.aws.amazon.com/cli/latest/reference/iam/attach-role-policy.html](http://docs.aws.amazon.com/cli/latest/reference/iam/attach-role-policy.html) to attach an existing managed policy

    or

   [http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html) to create an inline policy

The following example shows all the steps in a simple environment\. The example assumes that you are running the AWS CLI on a computer running Windows, and have already configured the AWS CLI with your credentials\. For more information, see [Configuring the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)\.

The commands to run are the following:

```
# Create the role and attach the trust policy that enables users in an account to assume the role.
$ aws iam create-role --role-name Test-CrossAcct-Role --assume-role-policy-document file://trustpolicyforcognitofederation.json

# Attach the permissions policy to the role to specify what it is allowed to do.
aws iam put-role-policy --role-name Test-CrossAcct-Role --policy-name Perms-Policy-For-CognitoFederation --policy-document file://permspolicyforcognitofederation.json
```

## Creating a Role for Federated Access \(AWS API\)<a name="roles-creatingrole-identityprovider-api"></a>

Before you create the role, you must follow the steps in the prerequisites section for the type of provider you are using:
+ For an OIDC provider, follow the steps in [Prerequisites for an OIDC provider](id_roles_create_for-idp_oidc.md#oidc-prereqs)\.
+ For a SAML provider, follow the steps in [Prerequisites for a SAML provider](id_roles_create_for-idp_saml.md#saml-prereqs)\.

**To create a role for identity federation \(AWS API\)**

1. To create a role: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateRole.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateRole.html)

1. To attach a permission policy to the role:

   [http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html) to attach an existing managed policy

    or

   [http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html) to create an inline policy