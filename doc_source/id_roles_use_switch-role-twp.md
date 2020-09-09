# Switching to an IAM role \(Tools for Windows PowerShell\)<a name="id_roles_use_switch-role-twp"></a>

A *role* specifies a set of permissions that you can use to access AWS resources that you need\. In that sense, it is similar to a [user in AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) \(IAM\)\. When you sign in as a user, you get a specific set of permissions\. However, you don't sign in to a role, but once signed in you can switch to a role\. This temporarily sets aside your original user permissions and instead gives you the permissions assigned to the role\. The role can be in your own account or any other AWS account\. For more information about roles, their benefits, and how to create and configure them, see [IAM roles](id_roles.md), and [Creating IAM roles](id_roles_create.md)\.

**Important**  
The permissions of your IAM user and any roles that you switch to are not cumulative\. Only one set of permissions is active at a time\. When you switch to a role, you temporarily give up your user permissions and work with the permissions that are assigned to the role\. When you exit the role, your user permissions are automatically restored\.

This section describes how to switch roles when you work at the command line with the AWS Tools for Windows PowerShell\.

Imagine that you have an account in the development environment and you occasionally need to work with the production environment at the command line using the [Tools for Windows PowerShell](http://aws.amazon.com/powershell/)\. You already have one access key credential set available to you\. These can be an access key pair assigned to your standard IAM user\. Or, if you signed\-in as a federated user, they can be the access key pair for the role initially assigned to you\. You can use these credentials to run the `Use-STSRole` cmdlet that passes the ARN of a new role as a parameter\. The command returns temporary security credentials for the requested role\. You can then use those credentials in subsequent PowerShell commands with the role's permissions to access resources in production\. While you use the role, you cannot use your user permissions in the Development account because only one set of permissions are in effect at a time\.

**Note**  
For security purposes, administrators can [review AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) to learn who performed an action in AWS\. Your administrator might require that you specify your IAM user name as the session name when you assume the role\. For more information, see [`aws:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname)\.

Note that all access keys and tokens are examples only and cannot be used as shown\. Replace with the appropriate values from your live environment\.

**To switch to a role \(Tools for Windows PowerShell\)**

1. Open a PowerShell command prompt and configure the default profile to use the access key from your current IAM user or from your federated role\. If you have previously used the Tools for Windows PowerShell, then this is likely already done\. Note that you can switch roles only if you are signed in as an IAM user, not the AWS account root user\.

   ```
   PS C:\> Set-AWSCredentials -AccessKey AKIAIOSFODNN7EXAMPLE -SecretKey wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY -StoreAs MyMainUserProfile
   PS C:\> Initialize-AWSDefaults -ProfileName MyMainUserProfile -Region us-east-2
   ```

   For more information, see [Using AWS Credentials](https://docs.aws.amazon.com/powershell/latest/userguide/specifying-your-aws-credentials.html) in the *AWS Tools for Windows PowerShell User Guide*\.

1. To retrieve credentials for the new role, run the following command to switch to the `RoleName` role in the 123456789012 account\. You get the role ARN from the account administrator who created the role\. The command requires that you provide a session name as well\. You can choose any text for that\. The following command requests the credentials and then captures the `Credentials` property object from the returned results object and stores it in the `$Creds` variable\.

   ```
   PS C:\> $Creds = (Use-STSRole -RoleArn "arn:aws:iam::123456789012:role/RoleName" -RoleSessionName "MyRoleSessionName").Credentials
   ```

   `$Creds` is an object that now contains the `AccessKeyId`, `SecretAccessKey`, and `SessionToken` elements that you need in the following steps\. The following sample commands illustrate typical values:

   ```
   PS C:\> $Creds.AccessKeyId
   AKIAIOSFODNN7EXAMPLE
   
   PS C:\> $Creds.SecretAccessKey
   wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
   
   PS C:\> $Creds.SessionToken
   AQoDYXdzEGcaEXAMPLE2gsYULo+Im5ZEXAMPLEeYjs1M2FUIgIJx9tQqNMBEXAMPLECvSRyh0FW7jEXAMPLEW+vE/7s1HRp
   XviG7b+qYf4nD00EXAMPLEmj4wxS04L/uZEXAMPLECihzFB5lTYLto9dyBgSDyEXAMPLE9/g7QRUhZp4bqbEXAMPLENwGPy
   Oj59pFA4lNKCIkVgkREXAMPLEjlzxQ7y52gekeVEXAMPLEDiB9ST3UuysgsKdEXAMPLE1TVastU1A0SKFEXAMPLEiywCC/C
   s8EXAMPLEpZgOs+6hz4AP4KEXAMPLERbASP+4eZScEXAMPLEsnf87eNhyDHq6ikBQ==
   
   PS C:\> $Creds.Expiration
   Thursday, June 18, 2018 2:28:31 PM
   ```

1. To use these credentials for any subsequent command, include them with the `-Credentials` parameter\. For example, the following command uses the credentials from the role and works only if the role is granted the `iam:ListRoles` permission and can therefore run the `Get-IAMRoles` cmdlet:

   ```
           PS C:\> get-iamroles -Credential $Creds
   ```

1. To return to your original credentials, simply stop using the `-Credentials $Creds` parameter and allow PowerShell to revert to the credentials that are stored in the default profile\.