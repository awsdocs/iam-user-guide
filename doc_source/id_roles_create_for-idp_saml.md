# Creating a Role for SAML 2\.0 Federation \(Console\)<a name="id_roles_create_for-idp_saml"></a>

With identity federation, you can provide access to AWS resources for users who sign in from a third\-party identity provider \(IdP\)\. To configure identity federation, you configure the provider and then you create an IAM role that determines what permissions a federated user has\. For more information about federation and identity providers, see [Identity Providers and Federation](id_roles_providers.md)\.

Before you can create a role for SAML 2\.0 federation, you must first complete the following prerequisite steps:<a name="saml-prereqs"></a>

**To prepare to create a role for SAML 2\.0 federation**

1. <a name="idpsamlstep1"></a>Before you create a role for SAML\-based federation, you must create a SAML provider in IAM\. For more information, see [Creating SAML Identity Providers](id_roles_providers_create_saml.md)\.

1. Prepare the policies for the role that the SAML 2\.0–authenticated users will assume\. As with any role, a role for the SAML federation contains two policies\. One is the trust policy that specifies who can assume the role \(the trusted entity, or principal\)\. The other policy \(the permission policy\) specifies the actual AWS actions and resources that the federated user is allowed or denied access to \(similar to a user or resource policy\)\.

   For SAML 2\.0 providers, the policy must include a `Statement` element similar to the following:

   The trust policy must grant an `Allow` effect for the `sts:AssumeRoleWithSAML` action\. In this role, you use two values that ensure that the role can be assumed only by your application:
   + For the `Principal` element, use the string `{"Federated":ARNofIdentityProvider}`\. Replace `ARNofIdentityProvider` with the ARN of the [SAML identity provider](id_roles_providers_saml.md) that you created in [Step 1](#idpsamlstep1)\.
   + For the `Condition` element, use a `StringEquals` condition to test that the `saml:aud` attribute from the SAML response matches the SAML federation endpoint for AWS\. 
**Note**  
Because the policy for the trusted entity uses [policy variables](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html) that represent values in the SAML response, you must set the policy's `Version` element to `2012-10-17` or a later supported version\.

   The following example shows a trust policy for a role designed for a SAML federated user:

   ```
   {
     "Version": "2012-10-17",
     "Statement": {
       "Effect": "Allow",
       "Action": "sts:AssumeRoleWithSAML",
       "Principal": {"Federated": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:saml-provider/PROVIDER-NAME"},
       "Condition": {"StringEquals": {"SAML:aud": "https://signin.aws.amazon.com/saml"}}
     }
   }
   ```

   Replace the principal ARN with the actual ARN for the SAML provider that you created in IAM\. It will have your own account ID and the actual provider name\. 

   After completing the prerequisite steps, you can create the role itself\. 

**To create a role for SAML\-based federation**

1. Make sure you've created a SAML provider in IAM, as described in [About SAML 2\.0\-based Federation](id_roles_providers_saml.md)\.

1. In the navigation pane of the IAM console, choose **Roles** and then choose **Create role**\.

1. Choose the **SAML 2\.0 federation** role type\.

1. In the **SAML Provider** list, select the provider that you're creating the role for\. 

1. Choose the SAML 2\.0 access level method\. 
   + Choose **Allow programmatic access only** to create a role that can be assumed programmatically from the AWS API\.
   + Choose **Allow programmatic and AWS Management Console access** to create a role that can be assumed programmatically and from the console\.

   The roles created by both are similar, but the role that can also be assumed from the console includes a trust policy with a particular condition\. That condition explicitly ensures that the SAML audience \(`SAML:aud` attribute\) is set to the AWS sign\-in endpoint for SAML \(https://signin\.aws\.amazon\.com/saml\)\.

1. If you're creating a role for programmatic access, select an attribute from the **Attribute** list\. Then in the **Value** box, type a value to include in the role\. This restricts role access to users from the identity provider whose SAML authentication response \(assertion\) includes the attributes that you specify\. You must specify at least one attribute to ensure that your role is limited to a subset of users at your organization\. 

   If you're creating a role for programmatic and console access, the `SAML:aud` attribute is automatically added and set to the URL of the AWS SAML endpoint \(https://signin\.aws\.amazon\.com/saml\)\. 

1. To add more attribute\-related conditions to the trust policy, choose **Add condition \(optional\)**, select the additional condition, and specify a value\. 
**Note**  
The list displays the most commonly used SAML attributes\. IAM supports additional attributes that you can use to create conditions\. \(For a list of the supported attributes, see [Available Keys for SAML Federation](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html#condition-keys-saml) in the topic [IAM JSON Policy Elements Reference](reference_policies_elements.md)\.\) If you need a condition for a supported SAML attribute that's not in the list, you can manually add that condition by editing the trust policy after you create the role\.

1.  Review your SAML 2\.0 trust information and then choose **Next: Permissions**\. 

1. Choose one or more permissions policies to attach to the role\. By default, roles have no permissions\. Select the box next to the policy that assigns the permissions that you want the federated users to have\. Then choose **Next: Review**\.

1. For **Role name**, type a role name that helps you identify the purpose of this role\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because various entities might reference the role, you cannot edit the name of the role after it has been created\. 

1. \(Optional\) For **Role description**, type a description for the new role\.

1. Review the role and then choose **Create role**\.

After you create the role, you complete the SAML trust by configuring your identity provider software with information about AWS and the roles that you want your federated users to use\. This is referred to as configuring relying party trust between your IdP and AWS\. For more information, see [Configuring your SAML 2\.0 IdP with Relying Party Trust and Adding Claims](id_roles_providers_create_saml_relying-party.md)\. 