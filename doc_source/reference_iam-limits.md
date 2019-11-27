# IAM and STS Limits<a name="reference_iam-limits"></a>

Objects in AWS Identity and Access Management \(IAM\) and AWS Security Token Service \(STS\) have size limitations\. These services also limit how you name an object, the number of objects you can create, and the number of characters you can use when you pass an object\. 

**Note**  
To get account\-level information about IAM usage and limit quotas, use the [GetAccountSummary](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetAccountSummary.html) API operation or the [get\-account\-summary](https://docs.aws.amazon.com/cli/latest/reference/iam/get-account-summary.html) AWS CLI command\. 

## IAM Name Limits<a name="reference_iam-limits-names"></a>

The following are restrictions on IAM names:
+ Policy documents can contain only the following Unicode characters: horizontal tab \(U\+0009\), linefeed \(U\+000A\), carriage return \(U\+000D\), and characters in the range U\+0020 to U\+00FF\. 
+ Names of users, groups, roles, policies, instance profiles, and server certificates must be alphanumeric, including the following common characters: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), underscore \(\_\), and hyphen \(\-\)\.
+ Names of users, groups, roles, and instance profiles must be unique within the account\. They are not distinguished by case, for example, you cannot create groups named both **ADMINS** and **admins**\.
+ The external ID value that a third party uses to assume a role must have a minimum of 2 characters and a maximum of 1,224 characters\. The value must be alphanumeric without white space\. It can also include the following symbols: plus \(\+\), equal \(=\), comma \(,\), period \(\.\), at \(@\), colon \(:\), forward slash \(/\), and hyphen \(\-\)\. For more information about the external ID, see [How to Use an External ID When Granting Access to Your AWS Resources to a Third Party](id_roles_create_for-user_externalid.md)\.
+ Path names must begin and end with a forward slash \(/\)\.
+ Policy names for [inline policies](access_policies_managed-vs-inline.md) must be unique to the user, group, or role they are embedded in\. The names can contain any Basic Latin \(ASCII\) characters minus the following reserved characters: backward slash \(\\\), forward slash \(/\), asterisk \(\*\), question mark \(?\), and white space\. These characters are reserved according to [RFC 3986](https://tools.ietf.org/html/rfc3986#section-2.2)\. 
+ User passwords \(login profiles\) can contain any Basic Latin \(ASCII\) characters\.
+ AWS account ID aliases must be unique across AWS products, and must be alphanumeric following DNS naming conventions\. An alias must be lowercase, it must not start or end with a hyphen, it cannot contain two consecutive hyphens, and it cannot be a 12\-digit number\. 

For a list of Basic Latin \(ASCII\) characters, go to the [Library of Congress Basic Latin \(ASCII\) Code Table](http://lcweb2.loc.gov/diglib/codetables/42.html)\. 

## IAM Object Limits<a name="reference_iam-limits-entities"></a>

AWS allows you to request an increase to default IAM entity limits\. To learn how to request a limit increase to these default limits, see [AWS Service Limits](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) in the *Amazon Web Services General Reference* documentation\.


**Default limits for IAM entities:**  

| Resource | Default Limit | 
| --- | --- | 
| Customer managed policies in an AWS account | 1500 | 
| Groups in an AWS account | 300 | 
| Roles in an AWS account | 1000 | 
| Managed policies attached to an IAM role | 10 | 
| Managed policies attached to an IAM user | 10 | 
| Virtual MFA devices \(assigned or unassigned\) in an AWS account | Equal to the user quota for the account | 
| Instance profiles in an AWS account | 1000 | 
| Server certificates stored in an AWS account | 20 | 

You cannot request a limit increase for the following limits\.


**Limits for IAM entities:**  

| Resource | Limit | 
| --- | --- | 
| Access keys assigned to an IAM user | 2 | 
| Access keys assigned to the AWS account root user | 2 | 
| Aliases for an AWS account | 1 | 
| Groups an IAM user can be a member of | 10 | 
| IAM users in a group | Equal to the user quota for the account | 
| Users in an AWS account | 5000 \(If you need to add a large number of users, consider using [temporary security credentials](id_credentials_temp.md)\.\) | 
| Identity providers \(IdPs\) associated with an IAM SAML provider object | 10 | 
| Keys per SAML provider | 10 | 
| Login profiles for an IAM user | 1 | 
| Managed policies attached to an IAM group | 10 | 
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
| Versions of a managed policy that can be stored | 5 | 

## IAM and STS Character Limits<a name="reference_iam-limits-entity-length"></a>

The following are the maximum character counts and size limits for IAM and AWS STS:


| Description | Limit | 
| --- | --- | 
| Path | 512 characters | 
| User name | 64 characters | 
| Group name | 128 characters | 
| Role name | 64 characters If you intend to use a role with the **Switch Role** feature in the AWS console, then the combined `Path` and `RoleName` cannot exceed 64 characters\.  | 
| Tag key | 128 charactersThis character limit applies to user tags, role tags, and [session tags](id_session-tags.md)\. | 
| Tag value | 256 charactersThis character limit applies to user tags, role tags, and [session tags](id_session-tags.md)\.Tag values can be empty\. That is, tag values can have a length of 0 characters\. | 
| Instance profile name | 128 characters | 
|  Unique IDs created by IAM, for example: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html)  This is not intended to be an exhaustive list, nor is it a guarantee that IDs of a certain type begin only with the specified letter combination\.   | 128 characters | 
| Policy name | 128 characters | 
| Password for a login profile | 1 to 128 characters | 
| Alias for an AWS account ID | 3 to 63 characters | 
| Role trust policy JSON text \(the policy that determines who is allowed to assume the role\) | 2,048 characters | 
| Role session name | 64 characters | 
| Role session duration |  12 hours When you assume a role from the AWS CLI or API, you can use the `duration-seconds` CLI parameter or the `DurationSeconds` API parameter to request a longer role session\. You can specify a value from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role, which can range from 1 to 12 hours\. The maximum session duration setting does not limit sessions assumed by AWS services\. To learn how to view the maximum value for your role, see [View the Maximum Session Duration Setting for a Role](id_roles_use.md#id_roles_use_view-role-max-session)\. If you don't specify a value for the `DurationSeconds` parameter, your security credentials are valid for one hour\.  | 
| Role [session policies](access_policies.md#policies_session) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html)  | 
| Role [session tags](id_session-tags.md) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html)  | 
| For [inline policies](access_policies_managed-vs-inline.md) | You can add as many inline policies as you want to an IAM user, role, or group\. But the total aggregate policy size \(the sum size of all inline policies\) per entity cannot exceed the following limits: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html)  IAM does not count white space when calculating the size of a policy against these limitations\.  | 
| For [managed policies](access_policies_managed-vs-inline.md) |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-limits.html)  IAM does not count white space when calculating the size of a policy against this limitation\.   | 