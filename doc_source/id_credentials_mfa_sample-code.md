# Sample code: Requesting credentials with multi\-factor authentication<a name="id_credentials_mfa_sample-code"></a>

The following examples show how to call `GetSessionToken` and `AssumeRole` operations and pass MFA authentication parameters\. No permissions are required to call `GetSessionToken`, but you must have a policy that allows you to call `AssumeRole`\. The credentials returned are then used to list all S3 buckets in the account\.

## Calling GetSessionToken with MFA authentication \(Python and C\#\)<a name="MFAProtectedAPI-example-getsessiontoken"></a>

The following examples, written using the [AWS SDK for Python \(Boto\)](http://aws.amazon.com/sdkforpython/) and [AWS SDK for \.NET](http://aws.amazon.com/sdkfornet/), show how to call `GetSessionToken` and pass MFA authentication information\. The temporary security credentials returned by the `GetSessionToken` operation are then used to list all S3 buckets in the account\.

The policy attached to the user who runs this code \(or to a group that the user is in\) provides the permissions for the returned temporary credentials\. For this example code, the policy must grant the user permission to request the Amazon S3 `ListBuckets` operation\. 

### Using Python<a name="MFAProtectedAPI-python-example"></a>

```
import boto
from boto.s3.connection import S3Connection
from boto.sts import STSConnection

# Prompt for MFA time-based one-time password (TOTP)
mfa_TOTP = raw_input("Enter the MFA code: ")

# The calls to AWS STS GetSessionToken must be signed with the access key ID and secret
# access key of an IAM user. The credentials can be in environment variables or in 
# a configuration file and will be discovered automatically
# by the STSConnection() function. For more information, see the Python SDK 
# documentation: http://boto.readthedocs.org/en/latest/boto_config_tut.html

sts_connection = STSConnection()

# Use the appropriate device ID (serial number for hardware device or ARN for virtual device). 
# Replace ACCOUNT-NUMBER-WITHOUT-HYPHENS and MFA-DEVICE-ID with appropriate values.

tempCredentials = sts_connection.get_session_token(
    duration=3600,
    mfa_serial_number="&region-arn;iam::ACCOUNT-NUMBER-WITHOUT-HYPHENS:mfa/MFA-DEVICE-ID",
    mfa_token=mfa_TOTP
)

# Use the temporary credentials to list the contents of an S3 bucket
s3_connection = S3Connection(
    aws_access_key_id=tempCredentials.access_key,
    aws_secret_access_key=tempCredentials.secret_key,
    security_token=tempCredentials.session_token
)

# Replace BUCKET-NAME with an appropriate value.
bucket = s3_connection.get_bucket(bucket_name="BUCKET-NAME")
objectlist = bucket.list()
for obj in objectlist:
    print obj.name
```

### Using C\#<a name="MFAProtectedAPI-csharp-example"></a>

```
Console.Write("Enter MFA code: ");
string mfaTOTP = Console.ReadLine(); // Get string from user

/* The calls to AWS STS GetSessionToken must be signed using the access key ID and secret
   access key of an IAM user. The credentials can be in environment variables or in 
   a configuration file and will be discovered automatically
   by the AmazonSecurityTokenServiceClient constructor. For more information, see 
   https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/net-dg-config-creds.html
*/
AmazonSecurityTokenServiceClient stsClient = 
    new AmazonSecurityTokenServiceClient();
GetSessionTokenRequest getSessionTokenRequest = new GetSessionTokenRequest();
getSessionTokenRequest.DurationSeconds = 3600;

// Replace ACCOUNT-NUMBER-WITHOUT-HYPHENS and MFA-DEVICE-ID with appropriate values
getSessionTokenRequest.SerialNumber = "arn:aws:iam::ACCOUNT-NUMBER-WITHOUT-HYPHENS:mfa/MFA-DEVICE-ID"; 
getSessionTokenRequest.TokenCode = mfaTOTP;

GetSessionTokenResponse getSessionTokenResponse = 
    stsClient.GetSessionToken(getSessionTokenRequest);

// Extract temporary credentials from result of GetSessionToken call
GetSessionTokenResult getSessionTokenResult = 
    getSessionTokenResponse.GetSessionTokenResult;
string tempAccessKeyId = getSessionTokenResult.Credentials.AccessKeyId;
string tempSessionToken = getSessionTokenResult.Credentials.SessionToken;
string tempSecretAccessKey = getSessionTokenResult.Credentials.SecretAccessKey;
SessionAWSCredentials tempCredentials = new SessionAWSCredentials(tempAccessKeyId, 
    tempSecretAccessKey, tempSessionToken);

// Use the temporary credentials to list the contents of an S3 bucket
// Replace BUCKET-NAME with an appropriate value
ListObjectsRequest S3ListObjectsRequest = new ListObjectsRequest();
S3ListObjectsRequest.BucketName = "BUCKET-NAME";
S3Client = AWSClientFactory.CreateAmazonS3Client(tempCredentials);
ListObjectsResponse S3ListObjectsResponse = 
    S3Client.ListObjects(S3ListObjectsRequest);
foreach (S3Object s3Object in S3ListObjectsResponse.S3Objects)
{
    Console.WriteLine(s3Object.Key);
}
```

## Calling AssumeRole with MFA authentication \(Python\)<a name="MFAProtectedAPI-example-assumerole"></a>

The following example, written using the [AWS SDK for Python \(Boto\)](http://aws.amazon.com/sdkforpython/), shows how to call `AssumeRole` and pass MFA authentication information\. The temporary security credentials returned by `AssumeRole` are then used to list all Amazon S3 buckets in the account\. 

 For more information about this scenario, see [Scenario: MFA protection for cross\-account delegation](id_credentials_mfa_configure-api-require.md#MFAProtectedAPI-cross-account-delegation)\. 

```
import boto
from boto.s3.connection import S3Connection
from boto.sts import STSConnection

# Prompt for MFA time-based one-time password (TOTP)
mfa_TOTP = raw_input("Enter the MFA code: ")

# The calls to AWS STS AssumeRole must be signed with the access key ID and secret
# access key of an IAM user. (The AssumeRole API operation can also be called using temporary
# credentials, but this example does not show that scenario.) 
# The IAM user credentials can be in environment variables or in 
# a configuration file and will be discovered automatically
# by the STSConnection() function. For more information, see the Python SDK 
# documentation: http://boto.readthedocs.org/en/latest/boto_config_tut.html

sts_connection = STSConnection()

# Use appropriate device ID (serial number for hardware device or ARN for virtual device)
# Replace ACCOUNT-NUMBER-WITHOUT-HYPHENS, ROLE-NAME, and MFA-DEVICE-ID with appropriate values
tempCredentials = sts_connection.assume_role(
    role_arn="arn:aws:iam::ACCOUNT-NUMBER-WITHOUT-HYPHENS:role/ROLE-NAME",
    role_session_name="AssumeRoleSession1",
    mfa_serial_number="arn:aws:iam::ACCOUNT-NUMBER-WITHOUT-HYPHENS:mfa/MFA-DEVICE-ID",
    mfa_token=mfa_TOTP
)

# Use the temporary credentials to list the contents of an S3 bucket
s3_connection = S3Connection(
    aws_access_key_id=tempCredentials.credentials.access_key,
    aws_secret_access_key=tempCredentials.credentials.secret_key,
    security_token=tempCredentials.credentials.session_token
)

# Replace BUCKET-NAME with a real bucket name
bucket = s3_connection.get_bucket(bucket_name="BUCKET-NAME")
objectlist = bucket.list()
for obj in objectlist:
    print obj.name
```