# Using IAM with CodeCommit: Git credentials, SSH keys, and AWS access keys<a name="id_credentials_ssh-keys"></a>

CodeCommit is a managed version control service that hosts private Git repositories in the AWS cloud\. To use CodeCommit, you configure your Git client to communicate with CodeCommit repositories\. As part of this configuration, you provide IAM credentials that CodeCommit can use to authenticate you\. IAM supports CodeCommit with three types of credentials:
+ Git credentials, an IAM \-generated user name and password pair you can use to communicate with CodeCommit repositories over HTTPS\.
+ SSH keys, a locally generated public\-private key pair that you can associate with your IAM user to communicate with CodeCommit repositories over SSH\.
+  [AWS access keys](id_credentials_access-keys.md), which you can use with the credential helper included with the AWS CLI to communicate with CodeCommit repositories over HTTPS\.

See the following sections for more information about each option\. 

## Use Git credentials and HTTPS with CodeCommit \(recommended\)<a name="git-credentials-code-commit"></a>

With Git credentials, you generate a static user name and password pair for your IAM user, and then use those credentials for HTTPS connections\. You can also use these credentials with any third\-party tool or integrated development environment \(IDE\) that supports static Git credentials\.

Because these credentials are universal for all supported operating systems and compatible with most credential management systems, development environments, and other software development tools, this is the recommended method\. You can reset the password for Git credentials at any time\. You can also make the credentials inactive or delete them if you no longer need them\.

**Note**  
You cannot choose your own user name or password for Git credentials\. IAM generates these credentials for you to help ensure they meet the security standards for AWS and secure repositories in CodeCommit\. You can download the credentials only once, at the time they are generated\. Make sure that you save the credentials in a secure location\. If necessary, you can reset the password at any time, but doing so invalidates any connections configured with the old password\. You must reconfigure connections to use the new password before you can connect\.

See the following topics for more information: 
+ To create an IAM user, see [Creating an IAM user in your AWS account](id_users_create.md)\. 
+ To generate and use Git credentials with CodeCommit, see [For HTTPS Users Using Git Credentials](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-gc.html) in the *AWS CodeCommit User Guide*\. 

**Note**  
Changing the name of an IAM user after generating Git credentials does not change the user name of the Git credentials\. The user name and password remain the same and are still valid\. 

**To rotate service specific credentials**

1. Create a second service\-specific credential set in addition to the set currently in use\.

1. Update all of your applications to use the new set of credentials and validate that the applications are working\.

1. Change the state of the original credentials to "Inactive"\.

1. Ensure that all of your applications are still working\.

1. Delete the inactive service\-specific credentials\.

## Use SSH keys and SSH with CodeCommit<a name="ssh-keys-code-commit"></a>

With SSH connections, you create public and private key files on your local machine that Git and CodeCommit use for SSH authentication\. You associate the public key with your IAM user and store the private key on your local machine\. See the following topics for more information: 
+ To create an IAM user, see [Creating an IAM user in your AWS account](id_users_create.md)\. 
+ To create an SSH public key and associate it with an IAM user, see [For SSH Connections on Linux, macOS, or Unix](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-ssh-unixes.html) or see [For SSH Connections on Windows](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-ssh-windows.html) in the *AWS CodeCommit User Guide*\. 

**Note**  
The public key must be encoded in ssh\-rsa format or PEM format\. The minimum bit\-length of the public key is 2048 bits, and the maximum length is 16384 bits\. This is separate from the size of the file you upload\. For example, you can generate a 2048\-bit key, and the resulting PEM file is 1679 bytes long\. If you provide your public key in another format or size, you will see an error message stating that the key format is not valid\.

## Use HTTPS with the AWS CLI credential helper and CodeCommit<a name="access-keys-code-commit"></a>

As an alternative to HTTPS connections with Git credentials, you can allow Git to use a cryptographically signed version of your IAM user credentials or Amazon EC2 instance role whenever Git needs to authenticate with AWS to interact with CodeCommit repositories\. This is the only connection method for CodeCommit repositories that does not require an IAM user\. This is also the only method that works with federated access and temporary credentials\. Unless your business needs require federated access or the use of temporary credentials, creating and using IAM users for access is strongly recommended\. See the following topics for more information:
+ To learn more about federated access, see [Identity providers and federation](id_roles_providers.md) and [Providing access to externally authenticated users \(identity federation\)](id_roles_common-scenarios_federated-users.md)\. 
+ To learn more about temporary credentials, see [Temporary security credentials in IAM](id_credentials_temp.md) and [Temporary Access to CodeCommit Repositories](https://docs.aws.amazon.com/codecommit/latest/userguide/temporary-access.html)\. 

The AWS CLI credential helper is not compatible with other credential helper systems, such as Keychain Access or Windows Credential Management\. There are additional configuration considerations when you configure HTTPS connections with the credential helper\. For more information, see [For HTTPS Connections on Linux, macOS, or Unix with the AWS CLI Credential Helper](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-https-unixes.html) or [HTTPS Connections on Windows with the AWS CLI Credential Helper](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-https-windows.html) in the *AWS CodeCommit User Guide*\.