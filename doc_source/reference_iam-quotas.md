# IAM and STS quotas<a name="reference_iam-quotas"></a>

AWS Identity and Access Management \(IAM\) and AWS Security Token Service \(STS\) have quotas that limit the size of objects\. This affects how you name an object, the number of objects you can create, and the number of characters you can use when you pass an object\. 

**Note**  
To get account\-level information about IAM usage and quotas, use the [GetAccountSummary](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountSummary.html) API operation or the [get\-account\-summary](https://docs.aws.amazon.com/cli/latest/reference/iam/get-account-summary.html) AWS CLI command\. 

## IAM name requirements<a name="reference_iam-quotas-names"></a>

IAM names have the following requirements and restrictions:
+ Policy documents can contain only the following Unicode characters: horizontal tab \(U\+0009\), linefeed \(U\+000A\), carriage return \(U\+000D\), and characters in the range U\+0020 to U\+00FF\. 
+ Names of users, groups, roles, policies, instance profiles, and server certificates must be alphanumeric, including the following common characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), underscore \(\_\), and hyphen \(\-\)\.
+ Names of users, groups, roles, and instance profiles must be unique within the account\. They are not distinguished by case, for example, you cannot create groups named both **ADMINS** and **admins**\.
+ The external ID value that a third party uses to assume a role must have a minimum of 2 characters and a maximum of 1,224 characters\. The value must be alphanumeric without white space\. It can also include the following symbols: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), colon \(:\), forward slash \(/\), and hyphen \(\-\)\. For more information about the external ID, see [How to use an external ID when granting access to your AWS resources to a third party](id_roles_create_for-user_externalid.md)\.
+ Path names must begin and end with a forward slash \(/\)\.
+ Policy names for [inline policies](access_policies_managed-vs-inline.md) must be unique to the user, group, or role they are embedded in\. The names can contain any Basic Latin \(ASCII\) characters minus the following reserved characters: backward slash \(\\\), forward slash \(/\), asterisk \(\*\), question mark \(?\), and white space\. These characters are reserved according to [RFC 3986](https://tools.ietf.org/html/rfc3986#section-2.2)\. 
+ User passwords \(login profiles\) can contain any Basic Latin \(ASCII\) characters\.
+ AWS account ID aliases must be unique across AWS products, and must be alphanumeric following DNS naming conventions\. An alias must be lowercase, it must not start or end with a hyphen, it cannot contain two consecutive hyphens, and it cannot be a 12\-digit number\. 

For a list of Basic Latin \(ASCII\) characters, go to the [Library of Congress Basic Latin \(ASCII\) Code Table](http://lcweb2.loc.gov/diglib/codetables/42.html)\. 

## IAM object quotas<a name="reference_iam-quotas-entities"></a>

AWS allows you to request an increase to default quotas for IAM entities\. You can use Service Quotas to manage your IAM quotas\. For adjustable IAM quotas, you can request a quota increase\. Smaller increases are automatically approved in Service Quotas and are completed within a few minutes\. Larger requests above the [maximum autoapproved increase](#autoapproved) are submitted to AWS Support\. Some adjustable quotas can't be increased above the maximum autoapproved increase amount\. You can track your request case in the AWS Support console\.

To request a quota increase, sign in to the AWS Management Console and open the Service Quotas console at [https://console\.aws\.amazon\.com/servicequotas/](https://console.aws.amazon.com/servicequotas/)\. In the navigation pane, choose **AWS services**\. On the navigation bar, choose the **US East \(N\. Virginia\)** Region\. Then search for **IAM**\. Choose **AWS Identity and Access Management \(IAM\)**, choose a quota, and follow the directions to request a quota increase\. For more information, see [Requesting a Quota Increase](https://docs.aws.amazon.com/servicequotas/latest/userguide/request-quota-increase.html) in the *Service Quotas User Guide*\.

The following quotas are adjustable\.


**Default quotas for IAM entities**  

| Resource | Default quota | Maximum autoapproval | 
| --- | --- | --- | 
| ACL \(Assume role policy\) size per role | 2048 characters | 4096 characters | 
| Customer managed policies in an AWS account | 1500 | 5000 | 
| Groups in an AWS account | 300 | 500 | 
| Roles in an AWS account | 1000 | 5000 | 
| Managed policies attached to an IAM role | 10 | 20 | 
| Managed policies attached to an IAM user | 10 | 20 | 
| Virtual MFA devices \(assigned or unassigned\) in an AWS account | Equal to the user quota for the account | Not applicable | 
| Instance profiles in an AWS account | 1000 | 5000 | 
| Server certificates stored in an AWS account | 20 | 1000 | 

You cannot request an increase for the following quotas\.


**Quotas for IAM entities**  

| Resource | Quota | 
| --- | --- | 
| Access keys assigned to an IAM user | 2 | 
| Access keys assigned to the AWS account root user | 2 | 
| Aliases for an AWS account | 1 | 
| Domains for an AWS account | 2 | 
| Groups an IAM user can be a member of | 10 | 
| IAM users in a group | Equal to the user quota for the account | 
| Identity providers \(IdPs\) associated with an IAM SAML provider object | 10 | 
| Keys per SAML provider | 10 | 
| Login profiles for an IAM user | 1 | 
| Managed policies attached to an IAM group | 10 | 
| OpenId Connect identity providers per AWS account | 100 | 
| Permissions boundaries for an IAM user | 1 | 
| Permissions boundaries for an IAM role | 1 | 
| MFA devices in use by an IAM user | 1 | 
| MFA devices in use by the AWS account root user | 1 | 
| Roles in an instance profile | 1 | 
| SAML providers in an AWS account | 100 | 
| Signing certificates assigned to an IAM user | 2 | 
| SSH public keys assigned to an IAM user | 5 | 
| Tags that can be attached to an IAM role | 50 | 
| Tags that can be attached to an IAM user | 50 | 
| Users in an AWS account | 5000 \(If you need to add a large number of users, consider using [temporary security credentials](id_credentials_temp.md)\.\) | 
| Versions of a managed policy that can be stored | 5 | 

## IAM and STS character quotas<a name="reference_iam-quotas-entity-length"></a>

The following are the maximum character counts and size quotas for IAM and AWS STS\. You cannot request an increase for the following quotas\.


| Description | Quota | 
| --- | --- | 
| Path | 512 characters | 
| User name | 64 characters | 
| Group name | 128 characters | 
| Role name | 64 characters If you intend to use a role with the **Switch Role** feature in the AWS console, then the combined `Path` and `RoleName` cannot exceed 64 characters\.  | 
| Tag key | 128 charactersThis character quota applies to user tags, role tags, and [session tags](id_session-tags.md)\. | 
| Tag value | 256 charactersThis character quota applies to user tags, role tags, and [session tags](id_session-tags.md)\.Tag values can be empty\. That is, tag values can have a length of 0 characters\. | 
| Instance profile name | 128 characters | 
|  Unique IDs created by IAM, for example: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html)  This is not intended to be an exhaustive list, nor is it a guarantee that IDs of a certain type begin only with the specified letter combination\.   | 128 characters | 
| Policy name | 128 characters | 
| Password for a login profile | 1–128 characters | 
| Alias for an AWS account ID | 3–63 characters | 
| Role trust policy JSON text \(the policy that determines who is allowed to assume the role\) | 2,048 characters | 
| Role session name | 64 characters | 
| Role session duration |  12 hours When you assume a role from the AWS CLI or API, you can use the `duration-seconds` CLI parameter or the `DurationSeconds` API parameter to request a longer role session\. You can specify a value from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role, which can range 1–12 hours\. If you don't specify a value for the `DurationSeconds` parameter, your security credentials are valid for one hour\. IAM users who switch roles in the console are granted the maximum session duration, or the remaining time in the IAM user's session, whichever is less\. The maximum session duration setting does not limit sessions assumed by AWS services\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\.   | 
| Role [session policies](access_policies.md#policies_session) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html)  | 
| Role [session tags](id_session-tags.md) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html)  | 
| For [inline policies](access_policies_managed-vs-inline.md) | You can add as many inline policies as you want to an IAM user, role, or group\. But the total aggregate policy size \(the sum size of all inline policies\) per entity cannot exceed the following quotas: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html)  IAM does not count white space when calculating the size of a policy against these quotas\.  | 
| For [managed policies](access_policies_managed-vs-inline.md) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html)  IAM does not count white space when calculating the size of a policy against this quota\.   | 