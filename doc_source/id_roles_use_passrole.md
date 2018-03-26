# Granting a User Permissions to Pass a Role to an AWS Service<a name="id_roles_use_passrole"></a>

To configure many AWS services, you must *pass* an IAM role to the service that defines what that service can do on your behalf\. For example, to provide applications running on an Amazon EC2 instance with AWS credentials, you pass a role to EC2 to use with the instance that provides those credentials\. You define what the credentials allow the applications running on the instance to do by attaching an IAM policy that grants the required permissions to the role\.

To pass a role \(and its permissions\) to an AWS service, a user must have permissions to *pass the role* to the service\. This helps administrators ensure that only approved users can configure a service with a role that grants permissions\. To allow a user to pass a role to an AWS service, you must grant the `PassRole` permission to the user's IAM user, role, or group\.

A user can pass a role ARN as a parameter in any API operation that uses the role to assign permissions to the service\. The service then checks whether that user has the `iam:PassRole` permission\. To limit the user to passing only approved roles, you can filter the `iam:PassRole` permission with the `Resources` element of the IAM policy statement\. 

**Example 1**  
Imagine that you want to grant a user the ability to pass any of an approved set of roles to the Amazon EC2 service upon launching an instance\. You need three elements:
+ An IAM *permissions policy* attached to the role that determines what the role can do\. Scope permissions to only the actions that the role must perform, and to only the resources that the role needs for those actions\. You can use AWS managed or customer\-created IAM permissions policy\.

  ```
  {
      "Version": "2012-10-17",
      "Statement": {
          "Effect": "Allow",
          "Action": [ "A list of the permissions the role is allowed to use" ],
          "Resource": [ "A list of the resources the role is allowed to access" ]
      }
  }
  ```
+ A* trust policy* for the role that allows the service to assume the role\. For example, you could attach the following trust policy to the role with the `UpdateAssumeRolePolicy` action\. This trust policy allows Amazon EC2 to use the role and the permissions attached to the role\.

  ```
  {
      "Version": "2012-10-17",
      "Statement": {
          "Sid": "TrustPolicyStatementThatAllowsEC2ServiceToAssumeTheAttachedRole",
          "Effect": "Allow",
          "Principal": { "Service": "ec2.amazonaws.com" },
         "Action": "sts:AssumeRole"
      }
  }
  ```
+ An IAM *permissions policy* attached to the IAM user that allows the user to pass only those policies that are approved\. `iam:PassRole` usually is accompanied by `iam:GetRole` so that the user can get the details of the role to be passed\. In this example, the user can pass only roles that exist in the specified account with names that begin with `EC2-roles-for-XYZ-`:

  ```
  {
      "Version": "2012-10-17",
      "Statement": [{
          "Effect": "Allow",
          "Action": [
              "iam:GetRole",
              "iam:PassRole"
          ],
          "Resource": "arn:aws:iam::<account-id>:role/EC2-roles-for-XYZ-*"
      }]
  }
  ```

Now the user can start an Amazon EC2 instance with an assigned role\. Applications running on the instance can access temporary credentials for the role through the instance profile metadata\. The permission policies attached to the role determine what the instance can do\. 

**Example 2**  
Amazon Relational Database Service \(Amazon RDS\) supports a feature called Enhanced Monitoring\. This feature enables Amazon RDS to monitor a database instance using an agent\. It also allows Amazon RDS to log metrics to Amazon CloudWatch Logs\. To enable this feature, you must create a service role to give Amazon RDS permissions to monitor and write metrics to your logs\. 

**To create a role for Amazon RDS Enhanced Monitoring**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Roles**, and then choose **Create role**\.

1. Choose the **AWS Service** role type, and then choose the **Amazon RDS Role for Enhanced Monitoring** service\. Then choose **Next: Permissions**\.

1. Choose the **AmazonRDSEnhancedMonitoringRole**, permissions policy and then choose **Next: Review**\.

1. For **Role name**, type a role name that helps you identify the purpose of this role\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **PRODROLE** and **prodrole**\. Because various entities might reference the role, you cannot edit the name of the role after it has been created\. 

1. \(Optional\) For **Role description**, type a description for the new role\.

1. Review the role and then choose **Create role**\.

The role automatically gets a trust policy that grants the `monitoring.rds.amazonaws.com` service permissions to assume the role\. After it does, Amazon RDS can perform all of the actions that the `AmazonRDSEnhancedMonitoringRole` policy allows\.

The user that you want to enable Enhanced Monitoring needs a policy that includes a statement that allows the user to pass the role, like the following\. Use your account number and replace the role name with the name you provided in step 3:

```
    {
        "Sid": "PolicyStatementToAllowUserToPassOneSpecificRole",
        "Effect": "Allow",
        "Action": [ "iam:PassRole" ],
        "Resource": "arn:aws:iam:::role/RDS-Monitoring-Role"
    }
```

You can combine this statement with statements in another policy or put it in its own policy\. To instead specify that the user can pass any role that begins with `RDS-`, you can replace the role name in the resource ARN with a wildcard, for example:

```
        "Resource": "arn:aws:iam:::role/RDS-*"
```