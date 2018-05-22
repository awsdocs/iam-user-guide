# Creating a Role for a Third\-Party Identity Provider \(Federation\)<a name="id_roles_create_for-idp"></a>

Identity federation provides access to AWS resources to users by means of a third\-party identity provider \(IdP\)\. To set up identity federation, you configure the provider and then create an IAM role that determines what permissions a federated user will have\. For more information about federation and identity providers, see [Identity Providers and Federation](id_roles_providers.md)\.

## Creating a Role for Federated Users \(AWS Management Console\)<a name="w3ab1c19c23c20c14b5"></a>

The steps for creating a role for federated users depends on your choice of third\-party providers:
+ To create a role for users federated with a Web Identity or OpenID Connect \(OIDC\) IdP, see [Creating a Role for Web Identity or OpenID Connect Federation \(Console\)](id_roles_create_for-idp_oidc.md)\.
+ To create a role for users federated with a SAML 2\.0 IdP, see [Creating a Role for SAML 2\.0 Federation \(Console\)](id_roles_create_for-idp_saml.md)\.

## Creating a Role for Federated Access \(AWS Command Line Interface\)<a name="roles-creatingrole-identityprovider-cli"></a>

The steps to create a role for the supported identity providers \(OIDC or SAML\) from the AWS CLI are identical; —the difference is in the contents of the trust policy that you create in the prerequisite steps\. Begin by following the steps in the **Prerequisites** section for the type of provider you are using:
+ For an OIDC provider, follow the steps in [Prerequisites for an OIDC provider](id_roles_create_for-idp_oidc.md#oidc-prereqs)\.
+ For a SAML provider, follow the steps in [Prerequisites for a SAML provider](id_roles_create_for-idp_saml.md#saml-prereqs)\.

Creating a role from the AWS CLI involves multiple steps\. When you use the console to create a role, many of the steps are done for you, but with the CLI you must explicitly perform each step yourself\. You must create the trust policy first, create the role, and then assign an permission policy to the role\.
<a name="createrolecli"></a>
**To create a role using the AWS CLI**  
Use the following commands:
+ To create a role: [http://docs.aws.amazon.com/cli/latest/reference/iam/create-role.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-role.html)
+ To attach a permission policy to the role:

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

## Creating a Role for Federated Access \(Tools for Windows PowerShell\)<a name="roles-creatingrole-identityprovider-twp"></a>

The steps to create a role for the supported identity providers \(OIDC or SAML\) is identical; the difference is in the contents of the trust policy you create in the prerequisite steps\. Follow the steps in the **Prerequisites** section for the type of provider you are using:
+ For an OIDC provider, follow the steps in [Prerequisites for an OIDC provider](id_roles_create_for-idp_oidc.md#oidc-prereqs)\.
+ For a SAML provider, follow the steps in [Prerequisites for a SAML provider](id_roles_create_for-idp_saml.md#saml-prereqs)\.

Creating a role using the Tools for Windows PowerShell involves multiple steps\. When you use the console to create a role, many of the steps are done for you, but with the Tools for Windows PowerShell you must explicitly perform each step yourself\. You must create the trust policy first, create the role, and then assign a permission policy to the role\.

**To create a role using the Tools for Windows PowerShell**  
Use the following commands:
+ To create a role: [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMRole.html&tocid=New-IAMRole](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMRole.html&tocid=New-IAMRole)
+ To attach a permission policy to the role:

  [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Register-IAMRolePolicy.html&tocid=Register-IAMRolePolicy](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Register-IAMRolePolicy.html&tocid=Register-IAMRolePolicy) to attach an existing managed policy

   \-or\-

  [http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Write-IAMRolePolicy.html&tocid=Write-IAMRolePolicy](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Write-IAMRolePolicy.html&tocid=Write-IAMRolePolicy) to create an inline policy

The following example shows all of the steps in a simple environment\. The example assumes that you have already configured the Tools for Windows PowerShell with your credentials\. For more information, see [Using AWS Credentials](http://docs.aws.amazon.com/powershell/latest/userguide/specifying-your-aws-credentials.html)\.

The commands to run are the following:

```
# Create the role and attach the trust policy that enables users in an account to assume the role.
PS C:\> New-IAMRole -RoleName Test-Federation-Role -AssumeRolePolicyDocument (Get-Content -Raw C:\policies\trustpolicyforfederation.json)

# Attach a managed permissions policy to the role to specify what it is allowed to do.
PS C:\> Register-IAMRolePolicy -RoleName Test-Federation-Role -PolicyArn arn:aws:iam::aws:policy/PolicyForFederation
```

## Creating a Role for Federated Access \(IAM API\)<a name="roles-creatingrole-identityprovider-api"></a>

Before you create the role, you must follow the steps in the Prerequisites section for the type of provider you are using:
+ For an OIDC provider, follow the steps in [Prerequisites for an OIDC provider](id_roles_create_for-idp_oidc.md#oidc-prereqs)\.
+ For a SAML provider, follow the steps in [Prerequisites for a SAML provider](id_roles_create_for-idp_saml.md#saml-prereqs)\.

**To create a role for identity federation using the IAM API**  
Use the following commands:
+ To create a role: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateRole.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateRole.html)
+ To attach a permission policy to the role:

  [http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html) to attach an existing managed policy

   or

  [http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html) to create an inline policy