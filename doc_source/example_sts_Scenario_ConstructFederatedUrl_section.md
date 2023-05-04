# Construct a URL with AWS STS for federated users using an AWS SDK<a name="example_sts_Scenario_ConstructFederatedUrl_section"></a>

The following code example shows how to:
+ Create an IAM role that grants read\-only access to the current account's Amazon S3 resources\.
+ Get a security token from the AWS federation endpoint\.
+ Construct a URL that can be used to access the console with federated credentials\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/sts/sts_temporary_credentials#code-examples)\. 
Create a role that grants read\-only access to the current account's S3 resources\.  

```
def setup(iam_resource):
    """
    Creates a role that can be assumed by the current user.
    Attaches a policy that allows only Amazon S3 read-only access.

    :param iam_resource: A Boto3 AWS Identity and Access Management (IAM) instance
                         that has the permission to create a role.
    :return: The newly created role.
    """
    role = iam_resource.create_role(
        RoleName=unique_name('role'),
        AssumeRolePolicyDocument=json.dumps({
            'Version': '2012-10-17',
            'Statement': [
                {
                    'Effect': 'Allow',
                    'Principal': {'AWS': iam_resource.CurrentUser().arn},
                    'Action': 'sts:AssumeRole'
                }
            ]
        })
    )
    role.attach_policy(PolicyArn='arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess')
    print(f"Created role {role.name}.")

    print("Give AWS time to propagate these new resources and connections.", end='')
    progress_bar(10)

    return role
```
Get a security token from the AWS federation endpoint and construct a URL that can be used to access the console with federated credentials\.  

```
def construct_federated_url(assume_role_arn, session_name, issuer, sts_client):
    """
    Constructs a URL that gives federated users direct access to the AWS Management
    Console.

    1. Acquires temporary credentials from AWS Security Token Service (AWS STS) that
       can be used to assume a role with limited permissions.
    2. Uses the temporary credentials to request a sign-in token from the
       AWS federation endpoint.
    3. Builds a URL that can be used in a browser to navigate to the AWS federation
       endpoint, includes the sign-in token for authentication, and redirects to
       the AWS Management Console with permissions defined by the role that was
       specified in step 1.

    :param assume_role_arn: The role that specifies the permissions that are granted.
                            The current user must have permission to assume the role.
    :param session_name: The name for the STS session.
    :param issuer: The organization that issues the URL.
    :param sts_client: A Boto3 STS instance that can assume the role.
    :return: The federated URL.
    """
    response = sts_client.assume_role(
        RoleArn=assume_role_arn, RoleSessionName=session_name)
    temp_credentials = response['Credentials']
    print(f"Assumed role {assume_role_arn} and got temporary credentials.")

    session_data = {
        'sessionId': temp_credentials['AccessKeyId'],
        'sessionKey': temp_credentials['SecretAccessKey'],
        'sessionToken': temp_credentials['SessionToken']
    }
    aws_federated_signin_endpoint = 'https://signin.aws.amazon.com/federation'

    # Make a request to the AWS federation endpoint to get a sign-in token.
    # The requests.get function URL-encodes the parameters and builds the query string
    # before making the request.
    response = requests.get(
        aws_federated_signin_endpoint,
        params={
            'Action': 'getSigninToken',
            'SessionDuration': str(datetime.timedelta(hours=12).seconds),
            'Session': json.dumps(session_data)
        })
    signin_token = json.loads(response.text)
    print(f"Got a sign-in token from the AWS sign-in federation endpoint.")

    # Make a federated URL that can be used to sign into the AWS Management Console.
    query_string = urllib.parse.urlencode({
        'Action': 'login',
        'Issuer': issuer,
        'Destination': 'https://console.aws.amazon.com/',
        'SigninToken': signin_token['SigninToken']
    })
    federated_url = f'{aws_federated_signin_endpoint}?{query_string}'
    return federated_url
```
Destroy the resources created for the demo\.  

```
def teardown(role):
    """
    Removes all resources created during setup.

    :param role: The demo role.
    """
    for attached in role.attached_policies.all():
        role.detach_policy(PolicyArn=attached.arn)
        print(f"Detached {attached.policy_name}.")
    role.delete()
    print(f"Deleted {role.name}.")
```
Run this scenario by using the previously defined functions\.  

```
def usage_demo():
    """Drives the demonstration."""
    print('-'*88)
    print(f"Welcome to the AWS Security Token Service federated URL demo.")
    print('-'*88)
    iam_resource = boto3.resource('iam')
    role = setup(iam_resource)
    sts_client = boto3.client('sts')
    try:
        federated_url = construct_federated_url(
            role.arn, 'AssumeRoleDemoSession', 'example.org', sts_client)
        print("Constructed a federated URL that can be used to connect to the "
              "AWS Management Console with role-defined permissions:")
        print('-'*88)
        print(federated_url)
        print('-'*88)
        _ = input("Copy and paste the above URL into a browser to open the AWS "
                  "Management Console with limited permissions. When done, press "
                  "Enter to clean up and complete this demo.")
    finally:
        teardown(role)
        print("Thanks for watching!")
```
+  For API details, see [AssumeRole](https://docs.aws.amazon.com/goto/boto3/sts-2011-06-15/AssumeRole) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------

## Troubleshooting
### The endpoint `https://signin.aws.amazon.com/federation` returns status code 400 without additional error messages.
If you encounter a 400 status code error without any additional error messages when accessing the https://signin.aws.amazon.com/federation endpoint, the issue might be related to the `SessionDuration` setting.

The default `str(datetime.timedelta(hours=12).seconds)` will only work for IAM users. If you are using an IAM role, you will hit the 1 hour session limit for role chaining. To verify if this is the cause of the issue, you can try setting the session duration to a value slightly lower than 3600 seconds (e.g. 3590 seconds). Note that setting it to exactly 3600 seconds will not work.

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.
