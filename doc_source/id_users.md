# IAM Users<a name="id_users"></a>

An IAM *user* is an entity that you create in AWS to represent the person or service that uses it to interact with AWS\. A user in AWS consists of a name and credentials\.

An IAM user with administrator permissions is not the same thing as the AWS account root user\. For more information about the root user, see [The AWS Account Root User](id_root-user.md)\.

**Important**  
If you arrived at this page while trying to enable Amazon Advertising for your application or web site, see [Sign up for the Product Advertising API](http://docs.aws.amazon.com/AWSECommerceService/latest/DG/becomingDev.html)\.

## How AWS identifies an IAM user<a name="id_users_create_aws-identifiers"></a>

When you create a user, IAM creates these ways to identify that user:
+ A "friendly name" for the user, which is the name that you specified when you created the user, such as `Bob` or `Alice`\. These are the names you see in the AWS Management Console\. 
+ An Amazon Resource Name \(ARN\) for the user\. You use the ARN when you need to uniquely identify the user across all of AWS, such as when you specify the user as a `Principal` in an IAM policy for an Amazon S3 bucket\. An ARN for an IAM user might look like the following: 

  `arn:aws:iam::account-ID-without-hyphens:user/Bob`
+ A unique identifier for the user\. This ID is returned only when you use the API, Tools for Windows PowerShell, or AWS CLI to create the user; you do not see this ID in the console\.

For more information about these identifiers, see [IAM Identifiers](reference_identifiers.md)\.

## Users and credentials<a name="id_users_creds"></a>

You can access AWS in different ways depending on the user credentials:
+ [**Console password**](id_credentials_passwords.md): A password that the user can type to sign in to interactive sessions such as the AWS Management Console\.
+ [**Access keys**](id_credentials_access-keys.md): A combination of an access key ID and a secret access key\. You can assign two to a user at a time\. These can be used to make programmatic calls to AWS when using the API in program code or at a command prompt when using the AWS CLI or the AWS PowerShell tools\.
+ [**SSH keys for use with AWS CodeCommit**](id_credentials_ssh-keys.md): An SSH public key in the OpenSSH format that can be used to authenticate with AWS CodeCommit\.
+ [**Server certificates**](id_credentials_server-certs.md): SSL/TLS certificates that you can use to authenticate with some AWS services\. We recommend that you use AWS Certificate Manager \(ACM\) to provision, manage, and deploy your server certificates\. Use IAM only when you must support HTTPS connections in a region that is not supported by ACM\. To learn which regions support ACM, see the [AWS Certificate Manager](http://docs.aws.amazon.com/general/latest/gr/rande.html#acm_region) section of the *AWS General Reference*\.

By default, a brand new IAM user has no password and no access key \(neither an access key ID nor a secret access key\)—no credentials of any kind\. You must create the type of credentials for an IAM user based on what the user will be doing\. 

Take advantage of the following options to administer passwords, access keys, and MFA devices:
+ **[Manage passwords for your IAM users](id_credentials_passwords.md)\.** Create and change the passwords that permit access to the AWS Management Console\. Set a password policy to enforce a minimum password complexity\. Allow users to change their own passwords\. 
+ **[Manage access keys for your IAM users](id_credentials_access-keys.md)\.** Create and update access keys for programmatic access to the resources in your account\. 
+ You can enhance the security of the user's credentials by enabling [multi\-factor authentication \(MFA\)](id_credentials_mfa.md) for the user\. With MFA, users have to provide both the credentials that are part of their user identity \(a password or access key\) and a temporary numeric code that's generated on a hardware device or by an application on a smartphone or tablet, or sent by AWS to an SMS\-compatible mobile device\. 
+ **[Find unused passwords and access keys](id_credentials_finding-unused.md)\.** Anyone who has a password or access keys for your account or an IAM user in your account has access to your AWS resources\. The security [best practice](http://docs.aws.amazon.com/general/latest/gr/aws-access-keys-best-practices.html) is to remove passwords and access keys when users no longer need them\.
+ **[Download a credential report for your account](id_credentials_getting-report.md)\.** You can generate and download a credential report that lists all IAM users in your account and the status of their various credentials, including passwords, access keys, and MFA devices\. For passwords and access keys, the credential report shows how recently the password or access key has been used\.

## Users and permissions<a name="id_users_perms"></a>

By default, a brand new IAM user has no [permissions](access.md) to do anything\. The user is not authorized to perform any AWS actions or to access any AWS resources\. An advantage of having individual IAM users is that you can assign permissions individually to each user\. You might assign administrative permissions to a few users, who then can administer your AWS resources and can even create and manage other IAM users\. In most cases, however, you want to limit a user's permissions to just the tasks \(AWS actions\) and resources that the user needs for his or her job\. Imagine a user named Dave\. When you create the IAM user `Dave`, you create a password for that user and attach permissions to the IAM user that let him launch a specific Amazon EC2 instance and read \(`GET`\) information from a table in an Amazon RDS database\. For procedures on how to create users and grant them initial credentials and permissions, see [Creating an IAM User in Your AWS Account](id_users_create.md)\. For procedures on how to change the permissions for existing users, see [Changing Permissions for an IAM User](id_users_change-permissions.md)\. For procedures on how to change the user's password or access keys, see [Managing Passwords](id_credentials_passwords.md) and [Managing Access Keys for IAM Users](id_credentials_access-keys.md)\.

## Users and accounts<a name="id_users_accounts"></a>

Each IAM user is associated with one and only one AWS account\. Because users are defined within your AWS account, they don't need to have a payment method on file with AWS\. Any AWS activity performed by users in your account is billed to your account\.

There's a limit to the number of IAM users you can have in an AWS account\. For more information, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.

## Users as service accounts<a name="id_users_service_accounts"></a>

An IAM user doesn't necessarily have to represent an actual person\. An IAM user is really just an identity with associated credentials and permissions\. You might create an IAM user to represent an application that needs credentials in order to make requests to AWS\. This is typically referred to as a "service account\." An application might have its own service account in your AWS account, and its own set of permissions, the same way that processes have their own service accounts defined in an operating system like Windows or Linux\.