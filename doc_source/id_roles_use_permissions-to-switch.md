# Granting a user permissions to switch roles<a name="id_roles_use_permissions-to-switch"></a>

When an administrator [creates a role for cross\-account access](id_roles_create_for-user.md), they establish trust between the account that owns the role, the resources \(trusting account\), and the account that contains the users \(trusted account\)\. To do this, the administrator of the trusting account specifies the trusted account number as the `Principal` in the role's trust policy\. That *potentially* allows any user in the trusted account to assume the role\. To complete the configuration, the administrator of the trusted account must give specific groups or users in that account permission to switch to the role\.

**To grant permission to switch to a role**

1. As the administrator of the trusted account,create a new policy for the user, or edits an existing policy to add the required elements\. For details, see [Creating or editing the policy](#roles-usingrole-createpolicy)\.

1. Then, choose how you want to share the role information: 
   + **Role link:** Send users a link that takes them to the **Switch Role** page with all the details already filled in\. 
   + **Account ID or alias:** Provide each user with the role name along with the account ID number or account alias\. The user then goes to the **Switch Role** page and adds the details manually\. 

   For details, see [Providing information to the user](#roles-usingrole-giveuser)\.

Note that you can switch roles only when you sign in as an IAM user, a SAML\-federated role, or a web\-identity federated role\. You cannot switch roles when you sign in as the AWS account root user\.

**Important**  
You cannot switch roles in the AWS Management Console to a role that requires an [ExternalId](id_roles_create_for-user_externalid.md) value\. You can switch to such a role only by calling the [https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API that supports the `ExternalId` parameter\.

**Notes**  
This topic discusses policies for a *user*, because you are ultimately granting permissions to a user to accomplish a task\. However, we don't recommend that you grant permissions directly to an individual user\. When a user assumes a role, they are assigned the permissions associated with that role\.
When you switch roles in the AWS Management Console, the console always uses your original credentials to authorize the switch\. This applies whether you sign in as an IAM user, as a SAML\-federated role, or as a web\-identity federated role\. For example, if you switch to RoleA, IAM uses your original user or federated role credentials to determine if you are allowed to assume RoleA\. If you then try to switch to RoleB *while you are using RoleA*, your **original** user or federated role credentials are used to authorize your attempt\. The credentials for RoleA are not used for this action\.

**Topics**
+ [Creating or editing the policy](#roles-usingrole-createpolicy)
+ [Providing information to the user](#roles-usingrole-giveuser)

## Creating or editing the policy<a name="roles-usingrole-createpolicy"></a>

A policy that grants a user permission to assume a role must include a statement with the `Allow` effect on the following: 
+ The `sts:AssumeRole` action
+ The Amazon Resource Name \(ARN\) of the role in a `Resource` element

Users that get the policy are allowed to switch roles on the resource listed \(either through group membership or directly attached\)\.

**Note**  
If `Resource` is set to `*`, the user can assume any role in any account that trusts the user's account\. \(In other words, the role's trust policy specifies the user's account as `Principal`\)\. As a best practice, we recommend that you follow the [principle of least privilege](http://en.wikipedia.org/wiki/Principle_of_least_privilege) and specify the complete ARN for only the roles that the user needs\.

The following example shows a policy that lets the user assume roles in only one account\. In addition, the policy uses a wildcard \(\*\) to specify that the user can switch to a role only if the role name begins with the letters `Test`\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "sts:AssumeRole",
    "Resource": "arn:aws:iam::account-id:role/Test*"
  }
}
```

**Note**  
The permissions that the role grants to the user do not add to the permissions already granted to the user\. When a user switches to a role, the user temporarily gives up his or her original permissions in exchange for those granted by the role\. When the user exits the role, then the original user permissions are automatically restored\. For example, let's say the user's permissions allow working with Amazon EC2 instances, but the role's permissions policy does not grant those permissions\. In that case, while using the role, the user cannot work with Amazon EC2 instances in the console\. In addition, temporary credentials obtained via `AssumeRole` do not work with Amazon EC2 instances programmatically\.

## Providing information to the user<a name="roles-usingrole-giveuser"></a>

After you create a role and grant your user permissions to switch to it, you must provide the user with the following:
+ The name of the role
+ The ID or alias of the account that contains the role

You can streamline access for your users by sending them a link that is preconfigured with the account ID and role name\. You can see the role link on the final page of the **Create Role** wizard or in the **Role Summary** page for any cross\-account enabled role\.

You can also use the following format to manually construct the link\. Substitute your account ID or alias and the role name for the two parameters in the following example\.

`https://signin.aws.amazon.com/switchrole?account=your_account_ID_or_alias&roleName=optional_path/role_name`

We recommend that you direct your users to [Switching to a role \(console\)](id_roles_use_switch-role-console.md) to walk them through the process\. To troubleshoot common issues that you might encounter when you assume a role, see [I can't assume a role](troubleshoot_roles.md#troubleshoot_roles_cant-assume-role)\.

**Considerations**
+ If you create the role programmatically, you can create the role with a path and a name\. If you do so, you must provide the complete path and role name to your users so they can enter it on the **Switch Role** page of the AWS Management Console\. For example: `division_abc/subdivision_efg/role_XYZ`\.
+ If you create the role programmatically, you can add a `Path` of up to 512 characters and a `RoleName`\. The role name can be up to 64 characters long\. However, to use a role with the **Switch Role** feature in the AWS Management Console, the combined `Path` and `RoleName` cannot exceed 64 characters\.
+ For security purposes, you can [review AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) to learn who performed an action in AWS\. You can use the `sts:SourceIdentity` condition key in the role trust policy to require users to specify an identity when they assume a role\. For example, you can require that IAM users specify their own user name as their source identity\. This can help you determine which user performed a specific action in AWS\. For more information, see [`sts:SourceIdentity`](reference_policies_iam-condition-keys.md#ck_sourceidentity)\. You can also use [`sts:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname) to require users to specify a session name when they assume a role\. This can help you differentiate between role sessions when a role is used by different principals\.