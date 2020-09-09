# Using IAM with Amazon Keyspaces \(for Apache Cassandra\)<a name="id_credentials_keyspaces"></a>

Amazon Keyspaces \(for Apache Cassandra\) is a scalable, highly available, and managed Apache Cassandra\-compatible database service\. You can access Amazon Keyspaces using the AWS Management Console, by running a `cqlsh` client, or using an Apache 2\.0 licensed Cassandra driver\. 

**Note**  
If you plan to interact with Amazon Keyspaces only through the console, you don't need to generate service\-specific credentials\. For more information, see [Accessing Amazon Keyspaces \(for Apache Cassandra\)](https://docs.aws.amazon.com/keyspaces/latest/devguide/console_keyspaces.html) in the *Amazon Keyspaces \(for Apache Cassandra\) Developer Guide*\.

You must generate service\-specific credentials to allow your users to access Amazon Keyspaces using `cqlsh` or an Apache 2\.0 licensed Cassandra driver\. *Service\-specific credentials* allow an IAM user to interact with one AWS service, but no others\. 

For more information about the permissions required to access Amazon Keyspaces, see [Amazon Keyspaces \(for Apache Cassandra\) Identity\-Based Policy Examples](https://docs.aws.amazon.com/keyspaces/latest/devguide/security_iam_id-based-policy-examples.html#security_iam_id-based-policy-examples-console) in the *Amazon Keyspaces \(for Apache Cassandra\) Developer Guide*\.

## Generating Amazon Keyspaces credentials \(console\)<a name="keyspaces_credentials_console"></a>

You can use the AWS Management Console to generate Amazon Keyspaces \(for Apache Cassandra\) credentials for your IAM users\.

**To generate Amazon Keyspaces service\-specific credentials \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users** and then choose the name of the user that requires the credentials\.

1. On the **Security Credentials** tab beneath **Credentials for Amazon Keyspaces \(for Apache Cassandra\)**, choose **Generate credentials**\.

1. Your service\-specific credentials are now available\. This is the only time that the password can be viewed or downloaded\. You cannot recover it later\. However, you can reset your password at any time\. Save the user and password in a secure location, because you'll need them later\.

## Generating Amazon Keyspaces credentials \(AWS CLI\)<a name="keyspaces_credentials_cli"></a>

You can use the AWS CLI to generate Amazon Keyspaces \(for Apache Cassandra\) credentials for your IAM users\.

**To generate Amazon Keyspaces service\-specific credentials \(AWS CLI\)**
+ Use the following command:
  + [aws iam create\-service\-specific\-credential](https://docs.aws.amazon.com/cli/latest/reference/iam/create-service-specific-credential.html)

## Generating Amazon Keyspaces credentials \(AWS API\)<a name="keyspaces_credentials_api"></a>

You can use the AWS API to generate Amazon Keyspaces \(for Apache Cassandra\) credentials for your IAM users\.

**To generate Amazon Keyspaces service\-specific credentials \(AWS API\)**
+ Complete the following operation:
  + [CreateServiceSpecificCredential](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateServiceSpecificCredential.html) 