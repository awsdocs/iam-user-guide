# Using bearer tokens<a name="id_credentials_bearer"></a>

Some AWS services require that you have permission to get an AWS STS service bearer token before you can access their resources programmatically\. These services support a protocol that requires you to use a bearer token instead of using a traditional [Signature Version 4 signed request](https://docs.aws.amazon.com/general/latest/gr/sigv4_signing.html)\. When you perform AWS CLI or AWS API operations that require bearer tokens, the AWS service requests a bearer token on your behalf\. The service provides you with the token, which you can then use to perform subsequent operations in that service\. 

AWS STS service bearer tokens include information from your original principal authentication that might affect your permissions\. This information can include principal tags, session tags, and session policies\. The token's access key ID begins with the `ABIA` prefix\. This helps you to identify operations that were performed using service bearer tokens in your CloudTrail logs\.

**Important**  
The bearer token can be used only for calls to the service that generates it and in the Region where it was generated\. You can't use the bearer token to perform operations in other services or Regions\.

An example of a service that supports bearer tokens is AWS CodeArtifact\. Before you can interact with AWS CodeArtifact using a package manager such as NPM, Maven, or PIP, you must call the `aws codeartifact get-authorization-token` operation\. This operation returns a bearer token that you can use to perform AWS CodeArtifact operations\. Alternatively, you can use the `aws codeartifact login` command that completes the same operation and then configures your client automatically\. 

If you perform an action in an AWS service that generates a bearer token for you, you must have the following permissions in your IAM policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowServiceBearerToken",
            "Effect": "Allow",
            "Action": "sts:GetServiceBearerToken",
            "Resource": "arn:aws:iam::111122223333:user/TestUser1"
        }
    ]
}
```