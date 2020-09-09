# Switching to an IAM role \(AWS API\)<a name="id_roles_use_switch-role-api"></a>

A *role* specifies a set of permissions that you can use to access AWS resources\. In that sense, it is similar to an [IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html)\. A principal \(person or application\) assumes a role to receive temporary permissions to carry out required tasks and interact with AWS resources\. The role can be in your own account or any other AWS account\. For more information about roles, their benefits, and how to create and configure them, see [IAM roles](id_roles.md), and [Creating IAM roles](id_roles_create.md)\. To learn about the different methods that you can use to assume a role, see [Using IAM roles](id_roles_use.md)\.

**Important**  
The permissions of your IAM user and any roles that you assume are not cumulative\. Only one set of permissions is active at a time\. When you assume a role, you temporarily give up your previous user or role permissions and work with the permissions that are assigned to the role\. When you exit the role, your original permissions are automatically restored\.

To assume a role, an application calls the AWS STS [https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API operation and passes the ARN of the role to use\. The operation creates a new session with temporary credentials\. This session has the same permissions as the identity\-based policies for that role\. 

When you call [https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html), you can optionally pass inline or managed [session policies](access_policies.md#policies_session)\. Session policies are advanced policies that you pass as a parameter when you programmatically create a temporary credential session for a role or federated user\. You can pass a single JSON inline session policy document using the `Policy` parameter\. You can use the `PolicyArns` parameter to specify up to 10 managed session policies\. The resulting session's permissions are the intersection of the entity's identity\-based policies and the session policies\. Session policies are useful when you need to give the role's temporary credentials to someone else\. They can use the role's temporary credentials in subsequent AWS API calls to access resources in the account that owns the role\. You cannot use session policies to grant more permissions than those allowed by the identity\-based policy\. To learn more about how AWS determines the effective permissions of a role, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\. 

![\[PermissionsWhenPassingRoles_Diagram\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/role_passed_policy_permissions.png)

You can call `AssumeRole` when you are signed in as an IAM user, or as an [externally authenticated user](id_roles_providers.md) \([SAML](id_roles_providers_saml.md) or [OIDC](id_roles_providers_oidc.md)\) already using a role\. You can also use [*role chaining*](id_roles_terms-and-concepts.md#iam-term-role-chaining), which is using a role to assume a second role\. You cannot assume a role when you are signed in as the AWS account root user\.

By default, your role session lasts for one hour\. When you assume this role using the AWS STS [https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API operations, you can specify a value for the `DurationSeconds` parameter\. This value can range from 900 seconds \(15 minutes\) up to the maximum session duration setting for the role\. To learn how to view the maximum value for your role, see [View the maximum session duration setting for a role](id_roles_use.md#id_roles_use_view-role-max-session)\. 

If you use role chaining, your session is limited to a maximum of one hour\. If you then use the `DurationSeconds` parameter to provide a value greater than one hour, the operation fails\.

**Note**  
For security purposes, administrators can [review AWS CloudTrail logs](cloudtrail-integration.md#cloudtrail-integration_signin-tempcreds) to learn who performed an action in AWS\. Your administrator might require that you specify your IAM user name as the session name when you assume the role\. For more information, see [`aws:RoleSessionName`](reference_policies_iam-condition-keys.md#ck_rolesessionname)\.

The following example in Python using the Boto3 interface to AWS \([AWS SDK for Python \(Boto\) V3](https://aws.amazon.com/tools/)\) shows how to call `AssumeRole`\. It also shows how to use the temporary security credentials returned by `AssumeRole` to list all Amazon S3 buckets in the account that owns the role\.

```
import boto3

# The calls to AWS STS AssumeRole must be signed with the access key ID
# and secret access key of an existing IAM user or by using existing temporary 
# credentials such as those from another role. (You cannot call AssumeRole 
# with the access key for the root account.) The credentials can be in 
# environment variables or in a configuration file and will be discovered 
# automatically by the boto3.client() function. For more information, see the 
# Python SDK documentation: 
# http://boto3.readthedocs.io/en/latest/reference/services/sts.html#client

# create an STS client object that represents a live connection to the 
# STS service
sts_client = boto3.client('sts')

# Call the assume_role method of the STSConnection object and pass the role
# ARN and a role session name.
assumed_role_object=sts_client.assume_role(
    RoleArn="arn:aws:iam::account-of-role-to-assume:role/name-of-role",
    RoleSessionName="AssumeRoleSession1"
)

# From the response that contains the assumed role, get the temporary 
# credentials that can be used to make subsequent API calls
credentials=assumed_role_object['Credentials']

# Use the temporary credentials that AssumeRole returns to make a 
# connection to Amazon S3  
s3_resource=boto3.resource(
    's3',
    aws_access_key_id=credentials['AccessKeyId'],
    aws_secret_access_key=credentials['SecretAccessKey'],
    aws_session_token=credentials['SessionToken'],
)

# Use the Amazon S3 resource object that is now configured with the 
# credentials to access your S3 buckets. 
for bucket in s3_resource.buckets.all():
    print(bucket.name)
```