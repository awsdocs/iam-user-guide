# Granting permissions to create temporary security credentials<a name="id_credentials_temp_control-access_enable-create"></a>

By default, IAM users do not have permission to create temporary security credentials for federated users and roles\. You must use a policy to provide your users with these permissions\. Although you can grant permissions directly to a user, we strongly recommend that you grant permissions to a group\. This makes management of the permissions much easier\. When someone no longer needs to perform the tasks associated with the permissions, you simply remove them from the group\. If someone else needs to perform that task, add them to the group to grant the permissions\.

To grant an IAM group permission to create temporary security credentials for federated users or roles, you attach a policy that grants one or both of the following privileges:
+ For federated users to access an IAM role, grant access to AWS STS `AssumeRole`\.
+ <a name="para_gsy_hxg_1t"></a>For federated users that don't need a role, grant access to AWS STS `GetFederationToken`\.

 For more information about the differences between the `AssumeRole` and `GetFederationToken` API operations, see [Requesting temporary security credentials](id_credentials_temp_request.md)\.

IAM users can also call [https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html) to create temporary security credentials\. No permissions are required for a user to call `GetSessionToken`\. The purpose of this operation is to authenticate the user using MFA\. You cannot use policies to control authentication\. This means that you cannot prevent IAM users from calling `GetSessionToken` to create temporary credentials\.

**Example policy that grants permission to assume a role**  
The following example policy grants permission to call `AssumeRole` for the `UpdateApp` role in AWS account `123123123123`\. When `AssumeRole` is used, the user \(or application\) that creates the security credentials on behalf of a federated user cannot delegate any permissions that are not already specified in the role permission policy\.   

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "sts:AssumeRole",
    "Resource": "arn:aws:iam::123123123123:role/UpdateAPP"
  }]
}
```

**Example policy that grants permission to create temporary security credentials for a federated user**  
The following example policy grants permission to access `GetFederationToken`\.  

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "sts:GetFederationToken",
    "Resource": "*"
  }]
}
```

**Important**  
When you give IAM users permission to create temporary security credentials for federated users with `GetFederationToken`, be aware that this permits those users to delegate their own permissions\. For more information about delegating permissions across IAM users and AWS accounts, see [Examples of policies for delegating access](id_roles_create_policy-examples.md)\. For more information about controlling permissions in temporary security credentials, see [Controlling permissions for temporary security credentials](id_credentials_temp_control-access.md)\. 

**Example policy that grants a user limited permission to create temporary security credentials for federated users**  
When you let an IAM user call `GetFederationToken`, it is a best practice to restrict the permissions that the IAM user can delegate\. For example, the following policy shows how to let an IAM user create temporary security credentials only for federated users whose names start with *Manager*\.  

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": "sts:GetFederationToken",
    "Resource": ["arn:aws:sts::123456789012:federated-user/Manager*"]
  }]
}
```