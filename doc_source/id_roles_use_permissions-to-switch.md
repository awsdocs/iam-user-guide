# Granting a user permissions to switch roles<a name="id_roles_use_permissions-to-switch"></a>

When an administrator [creates a role for cross\-account access](id_roles_create_for-user.md) they establish trust between the account that owns the role and the resources \(trusting account\) and the account that contains the users \(trusted account\)\. To do this, the administrator of the trusting account specifies the trusted account number as the `Principal` in the role's trust policy\. That allows *potentially* any user in the trusted account to assume the role\. To complete the configuration, the administrator of the trusted account must give specific groups or users in that account permission to switch to the role\.

To grant a user permission to switch to a role, the administrator of the trusted account creates a new policy for the user\. Or the administrator might edit an existing policy to add the required elements\. The administrator can then send the users a link that takes the user to the **Switch Role** page with all the details already filled in\. Alternatively, the administrator can provide the user with the account ID number or account alias that contains the role and the role name\. The user then goes to the **Switch Role** page and adds the details manually\. For details on how a user switches roles, see [Switching to a role \(console\)](id_roles_use_switch-role-console.md)\. 

Note that you can switch roles only when you sign in as an IAM user\. You cannot switch roles when you sign in as the AWS account root user\.

**Important**  
You cannot switch roles in the AWS Management Console to a role that requires an [ExternalId](id_roles_create_for-user_externalid.md) value\. You can switch to such a role only by calling the AssumeRole API that supports the `ExternalId` parameter\.

**Notes**  
This topic discusses policies for a *user*, because we are ultimately granting permissions to a user to accomplish a task\. However, it is [best practice not to grant permissions directly to an individual user](best-practices.md#use-groups-for-permissions)\. For easier management, we recommend assigning policies and granting permissions to IAM groups and then making the users members of the appropriate groups\. 
When you switch roles in the AWS Management Console, the console always uses your original credentials to authorize the switch\. This applies whether you sign in as an IAM user, as a SAML\-federated role, or as a web\-identity federated role\. For example, if you switch to RoleA, it uses your original user or federated role credentials to determine if you are allowed to assume RoleA\. If you then try to switch to RoleB *while you are using RoleA*, your **original** user or federated role credentials are used to authorize your attempt, not the credentials for RoleA\.

**Topics**
+ [Creating or editing the policy](#roles-usingrole-createpolicy)
+ [Providing information to the user](#roles-usingrole-giveuser)

## Creating or editing the policy<a name="roles-usingrole-createpolicy"></a>

A policy that grants a user permission to assume a role must include a statement with the `Allow` effect on the following: 
+ The `sts:AssumeRole` action
+ The Amazon Resource Name \(ARN\) of the role in a `Resource` element

This is as shown in the following example\. Users that get the policy \(either through group membership or directly attached\) are allowed to switch to the specified role\.

**Note**  
If `Resource` is set to `*`, the user can assume any role in any account that trusts the user's account\. \(In other words, the role's trust policy specifies the user's account as `Principal`\)\. As a best practice, we recommend that you follow the [principle of least privilege](http://en.wikipedia.org/wiki/Principle_of_least_privilege) and specify the complete ARN for only the roles that the user needs\.

The following example shows a policy that lets the user assume roles in only one account\. In addition, the policy uses a wildcard \(\*\) to specify that the user can switch to a role only if the role name begins with the letters `Test`\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "sts:AssumeRole",
    "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:role/Test*"
  }
}
```

**Note**  
The permissions that the role grants to the user do not add to the permissions already granted to the user\. When a user switches to a role, the user temporarily gives up his or her original permissions in exchange for those granted by the role\. When the user exits the role, then the original user permissions are automatically restored\. For example, let's say the user's permissions allow working with Amazon EC2 instances, but the role's permissions policy does not grant those permissions\. In that case, while using the role, the user cannot work with Amazon EC2 instances in the console\. In addition, temporary credentials obtained via `AssumeRole` do not work with Amazon EC2 instances programmatically\.

## Providing information to the user<a name="roles-usingrole-giveuser"></a>

After you create a role and grant your user permissions to switch to it, you must provide the user with the following:
+ The name of the role
+ The ID or alias of the account that contains the role

You can make things easier for your users by sending them a link that is preconfigured with the account ID and role name\. You can see the role link on the final page of the **Create Role** wizard or in the **Role Summary** page for any cross\-account enabled role\.

You can also use the following format to manually construct the link\. Substitute your account ID or alias and the role name for the two parameters in the following example\.

`https://signin.aws.amazon.com/switchrole?account=your_account_ID_or_alias&roleName=optional_path/role_name`

We recommend that you direct your users to [Switching to a role \(console\)](id_roles_use_switch-role-console.md) to step them through the process\.

**Considerations**
+ If you create the role programmatically, you can create the role with a path in addition to a name\. If you do so, you must provide the complete path and role name to your users so they can enter it on the **Switch Role** page of the AWS Management Console\. For example: `division_abc/subdivision_efg/role_XYZ`\.
+ If you create the role programmatically, you can add a `Path` of up to 512 characters in addition to a `RoleName`\. The role name can be up to 64 characters long\. However, to use a role with the **Switch Role** feature in the AWS Management Console, the combined `Path` and `RoleName` cannot exceed 64 characters\.
+ For security purposes, you can [review AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) to learn who performed an action in AWS\. You can use the `aws:RoleSessionName` condition key in the role trust policy to require users to specify a session name when they assume a role\. For example, you can require that IAM users specify their own user name as their session name\. For more information, see [`aws:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname)\.