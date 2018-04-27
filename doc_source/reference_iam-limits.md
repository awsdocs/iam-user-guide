# Limitations on IAM Entities and Objects<a name="reference_iam-limits"></a>

Entities and objects in IAM have size limitations\. IAM limits how you name an entity, the number of entities you can create, and the number of characters you can use in an entity\. 

**Note**  
To get account\-level information about entity usage and quotas, use the [GetAccountSummary](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountSummary.html) API action or the [get\-account\-summary](http://docs.aws.amazon.com/cli/latest/reference/iam/get-account-summary.html) AWS CLI command\. 

## IAM Entity Name Limits<a name="reference_iam-limits-names"></a>

The following are restrictions on IAM names:
+ Policy documents can contain only the following Unicode characters: horizontal tab \(U\+0009\), linefeed \(U\+000A\), carriage return \(U\+000D\), and characters in the range U\+0020 to U\+00FF\. 
+ Names of users, groups, roles, policies, instance profiles, and server certificates must be alphanumeric, including the following common characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), underscore \(\_\), and hyphen \(\-\)\.
+ Names of users, groups, and roles must be unique within the account\. They are not distinguished by case, for example, you cannot create groups named both "ADMINS" and "admins"\.
+ Path names must begin and end with a forward slash \(/\)\.
+ Policy names for [inline policies](access_policies_managed-vs-inline.md) must be unique to the user, group, or role they are embedded in\. The names can contain any Basic Latin \(ASCII\) characters minus the following reserved characters: backward slash \(\\\), forward slash \(/\), asterisk \(\*\), question mark \(?\), and white space\. These characters are reserved according to [RFC 3986](https://tools.ietf.org/html/rfc3986#section-2.2)\. 
+ User passwords \(login profiles\) can contain any Basic Latin \(ASCII\) characters\.
+ AWS account ID aliases must be unique across AWS products, and must be alphanumeric following DNS naming conventions\. An alias must be lowercase, it must not start or end with a hyphen, it cannot contain two consecutive hyphens, and it cannot be a 12 digit number\. 

For a list of Basic Latin \(ASCII\) characters, go to the [Library of Congress Basic Latin \(ASCII\) Code Table](http://lcweb2.loc.gov/diglib/codetables/42.html)\. 

## IAM Entity Object Limits<a name="reference_iam-limits-entities"></a>

AWS allows you to request an increase to default IAM entity limits\. To learn how to request a limit increase to these default limits, see [AWS Service Limits](http://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *Amazon Web Services General Reference* documentation\.


**Default limits for IAM entities:**  

| Resource | Default Limit | 
| --- | --- | 
| Customer managed policies in an AWS account | 1500 | 
| Groups in an AWS account | 300 | 
| Roles in an AWS account | 1000 | 
| Users in an AWS account | 5000 \(If you need to add a large number of users, consider using [temporary security credentials](id_credentials_temp.md)\.\) | 
| Virtual MFA devices \(assigned or unassigned\) in an AWS account | Equal to the user quota for the account | 
| Instance profiles in an AWS account | 1000 | 
| Server certificates stored in an AWS account | 20 | 

For most IAM entity limits, you cannot request a limit increase\.


**Limits for IAM entities:**  

| Resource | Limit | 
| --- | --- | 
| Access keys assigned to an IAM user | 2 | 
| Access keys assigned to the AWS account root user | 2 | 
| Aliases for an AWS account | 1 | 
| Groups an IAM user can be a member of | 10 | 
| IAM users in a group | Equal to the user quota for the account | 
| Identity providers \(IdPs\) associated with an IAM SAML provider object | 10 | 
| Keys per SAML provider | 10 | 
| Login profiles for an IAM user | 1 | 
| Managed policies attached to an IAM group | 10 | 
| Managed policies attached to an IAM role | 10 | 
| Managed policies attached to an IAM user | 10 | 
| MFA devices in use by an IAM user | 1 | 
| MFA devices in use by the AWS account root user | 1 | 
| Roles in an instance profile | 1 | 
| SAML providers in an AWS account | 100 | 
| Signing certificates assigned to an IAM user | 2 | 
| SSH public keys assigned to an IAM user | 5 | 
| Versions of a managed policy that can be stored | 5 | 

## IAM Entity Character Limits<a name="reference_iam-limits-entity-length"></a>

The following are the maximum lengths for entities:


| Description | Limit | 
| --- | --- | 
| Path | 512 characters | 
| User name | 64 characters | 
| Group name | 128 characters | 
| Role name | 64 characters If you intend to use a role with the Switch Role feature in the AWS console, then the combined `Path` and `RoleName` cannot exceed 64 characters\.  | 
| Instance profile name | 128 characters | 
|  Unique IDs created by IAM, for example: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html)  This is not intended to be an exhaustive list, nor is it a guarantee that IDs of a certain type begin only with the specified letter combination\.   | 128 characters | 
| Policy name | 128 characters | 
| Password for a login profile | 1 to 128 characters | 
| Alias for an AWS account ID | 3 to 63 characters | 
| Role trust policy JSON text \(the policy that determines who is allowed to assume the role\) | 2,048 characters | 
| Role session name | 64 characters | 
| Role session duration |  12 hours When you assume a role from the AWS CLI or API, you can use the `duration-seconds` CLI parameter or the `DurationSeconds` API parameter to request a longer role session\. You can specify a value from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role, which can range from 1 hour to 12 hours\. To learn how to view the maximum value for your role, see [View the Maximum Session Duration Setting for a Role](id_roles_use.md#id_roles_use_view-role-max-session)\. If you don't specify a value for the `DurationSeconds` parameter, your security credentials are valid for one hour\.  | 
| For [inline policies](access_policies_managed-vs-inline.md) | You can add as many inline policies as you want to an IAM user, role, or group\. But the total aggregate policy size \(the sum size of all inline policies\) per entity cannot exceed the following limits: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html)  IAM does not count white space when calculating the size of a policy against these limitations\.  | 
| For [managed policies](access_policies_managed-vs-inline.md) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html)  IAM does not count white space when calculating the size of a policy against this limitation\.   | 