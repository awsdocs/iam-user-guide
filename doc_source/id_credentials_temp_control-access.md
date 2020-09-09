# Controlling permissions for temporary security credentials<a name="id_credentials_temp_control-access"></a>

You can use AWS Security Token Service \(AWS STS\) to create and provide trusted users with temporary security credentials that can control access to your AWS resources\. For more information about AWS STS, see [Temporary security credentials in IAM](id_credentials_temp.md)\. After AWS STS issues temporary security credentials, they are valid through the expiration period and cannot be revoked\. However, the permissions assigned to temporary security credentials are evaluated each time a request is made that uses the credentials, so you can achieve the effect of revoking the credentials by changing their access rights after they have been issued\. 

The following topics assume you have a working knowledge of AWS permissions and policies\. For more information on these topics, see [Access management for AWS resources](access.md)\. 

**Topics**
+ [Permissions for AssumeRole, AssumeRoleWithSAML, and AssumeRoleWithWebIdentity](id_credentials_temp_control-access_assumerole.md)
+ [Permissions for GetFederationToken](id_credentials_temp_control-access_getfederationtoken.md)
+ [Permissions for GetSessionToken](id_credentials_temp_control-access_getsessiontoken.md)
+ [Disabling permissions for temporary security credentials](id_credentials_temp_control-access_disable-perms.md)
+ [Granting permissions to create temporary security credentials](id_credentials_temp_control-access_enable-create.md)