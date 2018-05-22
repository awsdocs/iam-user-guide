# Granting Permissions to Create Temporary Security Credentials<a name="id_credentials_temp_control-access_enable-create"></a>

By default, IAM users do not have permission to create temporary security credentials for federated users and roles\. However, by default IAM users can call [http://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html](http://docs.aws.amazon.com/STS/latest/APIReference/API_GetSessionToken.html) with their own permissions and thereby create temporary credentials for others\.\.

**Note**  
Although you can grant permissions directly to a user, we strongly recommend that you grant permissions to a group\. This makes management of the permissions much easier\. When someone no longer needs to perform the tasks associated with the permissions, you simply remove them from the group\. If someone else needs to perform that task, add them to the group to grant the permissions\.

To grant an IAM group permission to create temporary security credentials for federated users or roles, you attach a policy that grants one or both of the following privileges:
+ For federated users to access an IAM role, grant access to AWS STS `AssumeRole`\.
+ <a name="para_gsy_hxg_1t"></a>For federated users that don't need a role, grant access to AWS STS `GetFederationToken`\.

 For more information about the differences between the `AssumeRole` and `GetFederationToken` API operations, see [Requesting Temporary Security Credentials](id_credentials_temp_request.md)\.

**Example : A policy that grants permission to assume a role**  
The following example policy grants permission to call `AssumeRole` for the `UpdateApp` role in AWS account `123123123123`\. When `AssumeRole` is used, the user \(or application\) that creates the security credentials on behalf of a federated user cannot delegate any permissions not already specified in the role permission policy\.   

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

**Example : A policy that grants permission to create temporary security credentials for a federated user**  
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
When you give an IAM user permission to create temporary security credentials for federated users with `GetFederationToken`, be aware that this permits the IAM user to delegate his or her own permissions\. For more information about delegating permissions across IAM users and AWS accounts, see [Examples of Policies for Delegating Access](id_roles_create_policy-examples.md)\. For more information about controlling permissions in temporary security credentials, see [Controlling Permissions for Temporary Security Credentials](id_credentials_temp_control-access.md)\. 

**Example : A policy that grants a user limited permission to create temporary security credentials for federated users**  
When you let an IAM user call `GetFederationToken` to create temporary security credentials for federated users, it is a best practice to restrict as much as practical the permissions that the IAM user is allowed to delegate\. For example, the following policy shows how to let an IAM user create temporary security credentials only for federated users whose names start with *Manager*\.  

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