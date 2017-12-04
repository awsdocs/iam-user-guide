# Switching to an IAM Role \(API\)<a name="id_roles_use_switch-role-api"></a>

A *role* specifies a set of permissions that you can use to access AWS resources that you need\. In that sense, it is similar to a [user in AWS Identity and Access Management](http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) \(IAM\)\. An application assumes a role to receive permissions to carry out required tasks and interact with AWS resources\. The role can be in your own account or any other AWS account\. For more information about roles, their benefits, and how to create and configure them, see [IAM Roles](id_roles.md), and [Creating IAM Roles](id_roles_create.md)\.

This section describes how to switch roles from within code that uses the AWS API\.

Note that all access keys and tokens are examples only and cannot be used as shown\. Replace with the appropriate values from your live environment\.

To assume a role, an application calls the AWS STS [http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html](http://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) API and passes the ARN of the role to use\. The `AssumeRole` API returns a set of temporary security credentials that you can use in subsequent AWS API calls to access resources in the account that owns the role\. The temporary credentials have whatever permissions are defined in the role's permission policy\. The call to `AssumeRole` can optionally pass a supplemental policy that can further restrict \(filter\) the permissions of the temporary security credentials that the `AssumeRole` API returns\. You can call `AssumeRole` only with IAM user or IAM role credentials\. You cannot call `AssumeRole` with the credentials of the AWS account root user\.

**Note**  
For security purposes, you can use AWS CloudTrail to audit the use of roles in the account\. The call to `AssumeRole` must include a role session name between 2 and 64 characters long that can include letters, numbers, and the `=,.@-` characters\. The role session name is used in CloudTrail logs to identify actions performed by the temporary security credentials\. For more information, see [CloudTrail Event Reference](http://docs.aws.amazon.com/awscloudtrail/latest/userguide/eventreference.html) in the *AWS CloudTrail User Guide*\.

The following example in Python using the Boto3 interface to AWS \([AWS SDK for Python \(Boto\) V3](https://aws.amazon.com/tools/)\) shows how to call `AssumeRole` and how to use the temporary security credentials returned by `AssumeRole` to list all Amazon S3 buckets in the account that owns the role\.

```
import boto3

# The calls to AWS STS AssumeRole must be signed with the access key ID
# and secret access key of an existing IAM user or by using existing temporary 
# credentials such as those from antoher role. (You cannot call AssumeRole 
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
assumedRoleObject = sts_client.assume_role(
    RoleArn="arn:aws:iam::account-of-role-to-assume:role/name-of-role",
    RoleSessionName="AssumeRoleSession1"
)

# From the response that contains the assumed role, get the temporary 
# credentials that can be used to make subsequent API calls
credentials = assumedRoleObject['Credentials']

# Use the temporary credentials that AssumeRole returns to make a 
# connection to Amazon S3  
s3_resource = boto3.resource(
    's3',
    aws_access_key_id = credentials['AccessKeyId'],
    aws_secret_access_key = credentials['SecretAccessKey'],
    aws_session_token = credentials['SessionToken'],
)

# Use the Amazon S3 resource object that is now configured with the 
# credentials to access your S3 buckets. 
for bucket in s3_resource.buckets.all():
    print(bucket.name)
```