# Common scenarios for roles: Users, applications, and services<a name="id_roles_common-scenarios"></a>

As with most AWS features, you generally have two ways to use a role: interactively in the IAM console, or programmatically with the AWS CLI, Tools for Windows PowerShell, or API\.
+ IAM users in your account using the IAM console can *switch to* a role to temporarily use the permissions of the role in the console\. The users give up their original permissions and take on the permissions assigned to the role\. When the users exit the role, their original permissions are restored\.
+ An application or a service offered by AWS \(like Amazon EC2\) can *assume* a role by requesting temporary security credentials for a role with which to make programmatic requests to AWS\. You use a role this way so that you don't have to share or maintain long\-term security credentials \(for example, by creating an IAM user\) for each entity that requires access to a resource\.

**Note**  
This guide uses the phrases *switch to a role* and *assume a role* interchangeably\.

The simplest way to use roles is to grant your IAM users permissions to switch to roles that you create within your own or another AWS account\. They can switch roles easily using the IAM console to use permissions that you don't ordinarily want them to have, and then exit the role to surrender those permissions\. This can help prevent *accidental* access to or modification of sensitive resources\.

For more complex uses of roles, such as granting access to applications and services, or federated external users, you can call the `AssumeRole` API\. This API call returns a set of temporary credentials that the application can use in subsequent API calls\. Actions attempted with the temporary credentials have only the permissions granted by the associated role\. An application doesn't have to "exit" the role the way a user in the console does; rather the application simply stops using the temporary credentials and resumes making calls with the original credentials\.

Federated users sign in by using credentials from an identity provider \(IdP\)\. AWS then provides temporary credentials to the trusted IdP to pass on to the user for including in subsequent AWS resource requests\. Those credentials provide the permissions granted to the assigned role\.

This section provides overviews of the following scenarios:
+ [Provide access for an IAM user in one AWS account that you own to access resources in another account that you own](id_roles_common-scenarios_aws-accounts.md)
+ [Provide access to IAM users in AWS accounts owned by third parties](id_roles_common-scenarios_third-party.md)
+ [Provide access for services offered by AWS to AWS resources](id_roles_common-scenarios_services.md)
+ [Provide access for externally authenticated users \(identity federation\)](id_roles_common-scenarios_federated-users.md)