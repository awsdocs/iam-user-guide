# Providing access to an IAM user in another AWS account that you own<a name="id_roles_common-scenarios_aws-accounts"></a>

You can grant your IAM users permission to switch to roles within your AWS account or to roles defined in other AWS accounts that you own\. 

**Note**  
If you want to grant access to an account that you do not own or control, see [Providing access to AWS accounts owned by third parties](id_roles_common-scenarios_third-party.md) later in this topic\. 

Imagine that you have Amazon EC2 instances that are critical to your organization\. Instead of directly granting your users permission to terminate the instances, you can create a role with those privileges\. Then allow administrators to switch to the role when they need to terminate an instance\. Doing this adds the following layers of protection to the instances:
+ You must explicitly grant your users permission to assume the role\.
+ Your users must actively switch to the role using the AWS Management Console or assume the role using the AWS CLI or AWS API\.
+ You can add multi\-factor authentication \(MFA\) protection to the role so that only users who sign in with an MFA device can assume the role\. To learn how to configure a role so that users who assume the role must first be authenticated using multi\-factor authentication \(MFA\), see [Configuring MFA\-protected API access](id_credentials_mfa_configure-api-require.md)\.

We recommend using this approach to enforce the *principle of least privilege*\. That means restricting the use of elevated permissions to only those times when they are needed for specific tasks\. With roles you can help prevent accidental changes to sensitive environments, especially if you combine them with [auditing](cloudtrail-integration.md) to help ensure that roles are only used when needed\.

When you create a role for this purpose, you specify the accounts by ID whose users need access in the `Principal` element of the role's trust policy\. You can then grant specific users in those other accounts permissions to switch to the role\. To learn whether principals in accounts outside of your zone of trust \(trusted organization or account\) have access to assume your roles, see [What is IAM Access Analyzer?](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)\.

A user in one account can switch to a role in the same or a different account\. While using the role, the user can perform only the actions and access only the resources permitted by the role; their original user permissions are suspended\. When the user exits the role, the original user permissions are restored\.

## Example scenario using separate development and production accounts<a name="id_roles_common-scenarios_aws-accounts-example"></a>

Imagine that your organization has multiple AWS accounts to isolate a development environment from a production environment\. Users in the development account might occasionally need to access resources in the production account\. For example, you might need cross\-account access when you are promoting an update from the development environment to the production environment\. Although you could create separate identities \(and passwords\) for users who work in both accounts, managing credentials for multiple accounts makes identity management difficult\. In the following figure, all users are managed in the development account, but some developers require limited access to the production account\. The development account has two groups: Testers and Developers, and each group has its own policy\.

![\[Use a role to delegate permissions to a user in a different account\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/roles-usingroletodelegate.png)

1. In the production account, an administrator uses IAM to create the `UpdateApp` role in that account\. In the role, the administrator defines a trust policy that specifies the development account as a `Principal`, meaning that authorized users from the development account can use the `UpdateApp` role\. The administrator also defines a permissions policy for the role that specifies which role users have read and write permissions to the Amazon S3 bucket named `productionapp`\.

   The administrator then shares the appropriate information with anyone who needs to assume the role\. That information is the account number and name of the role \(for AWS console users\) or the Amazon Resource Name \(ARN\) \(for AWS CLI or AWS API access\)\. The role ARN might look like `arn:aws:iam::123456789012:role/UpdateApp`, where the role is named `UpdateApp` and the role was created in account number 123456789012\.
**Note**  
The administrator can optionally configure the role so that users who assume the role must first be authenticated using multi\-factor authentication \(MFA\)\. For more information, see [Configuring MFA\-protected API access](id_credentials_mfa_configure-api-require.md)\. 

1. In the development account, an administrator grants members of the Developers group permission to switch to the role\. This is done by granting the Developers group permission to call the AWS Security Token Service \(AWS STS\) `AssumeRole` API for the `UpdateApp` role\. Any IAM user that belongs to the Developers group in the development account can now switch to the `UpdateApp` role in the production account\. Other users who are not in the developer group do not have permission to switch to the role and therefore cannot access the S3 bucket in the production account\.

1. The user requests switches to the role:
   + AWS console: The user chooses the account name on the navigation bar and chooses **Switch Role**\. The user specifies the account ID \(or alias\) and role name\. Alternatively, the user can click on a link sent in email by the administrator\. The link takes the user to the **Switch Role** page with the details already filled in\.
   + AWS API/AWS CLI: A user in the Developers group of the development account calls the `AssumeRole` function to obtain credentials for the `UpdateApp` role\. The user specifies the ARN of the `UpdateApp` role as part of the call\. If a user in the Testers group makes the same request, the request fails because Testers do not have permission to call `AssumeRole` for the `UpdateApp` role ARN\.

1. AWS STS returns temporary credentials:
   + AWS console: AWS STS verifies the request with the role's trust policy to ensure that the request is from a trusted entity \(which it is: the development account\)\. After verification, AWS STS returns [temporary security credentials](https://docs.aws.amazon.com/STS/latest/UsingSTS/Welcome.html) to the AWS console\.
   + API/CLI: AWS STS verifies the request against the role's trust policy to ensure that the request is from a trusted entity \(which it is: the Development account\)\. After verification, AWS STS returns [temporary security credentials](https://docs.aws.amazon.com/STS/latest/UsingSTS/Welcome.html) to the application\.

1. The temporary credentials allow access to the AWS resource:
   + AWS console: The AWS console uses the temporary credentials on behalf of the user for all subsequent console actions, in this case, to read and write to the `productionapp` bucket\. The console cannot access any other resource in the production account\. When the user exits the role, the user's permissions revert to the original permissions held before switching to the role\.
   + API/CLI: The application uses the temporary security credentials to update the `productionapp` bucket\. With the temporary security credentials, the application can only read from and write to the `productionapp` bucket and cannot access any other resource in the Production account\. The application does not have to exit the role, but instead stops using the temporary credentials and uses the original credentials in subsequent API calls\.