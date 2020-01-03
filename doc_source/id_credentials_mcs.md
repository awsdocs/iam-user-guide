# Using IAM with Amazon Managed Apache Cassandra Service<a name="id_credentials_mcs"></a>

Amazon Managed Apache Cassandra Service \(MCS\) is a scalable, highly available, and managed Apache Cassandra–compatible database service\. You can access MCS using the AWS Management Console, by running a `cqlsh` client, or using an Apache 2\.0 licensed Cassandra driver\. 

**Note**  
If you plan to interact with MCS only through the console, you don't need to generate service\-specific credentials\. For more information, see [Accessing Amazon Managed Apache Cassandra Service Using the Console](https://docs.aws.amazon.com/mcs/latest/devguide/console_MCS.html) in the *Amazon Managed Apache Cassandra Service Developer Guide*\.

You must generate service\-specific credentials to allow your users to access MCS using `cqlsh` or an Apache 2\.0 licensed Cassandra driver\. *Service\-specific credentials* allow an IAM user to interact with one AWS service, but no others\. 

For more information about the permissions required to access MCS, see [Generating Service\-Specific Credentials](https://docs.aws.amazon.com/mcs/latest/devguide/accessing.html#ssc) in the *Amazon Managed Apache Cassandra Service Developer Guide*\.

## Generating MCS Credentials \(Console\)<a name="mcs_credentials_console"></a>

You can use the AWS Management Console to generate Amazon Managed Apache Cassandra Service \(MCS\) credentials for your IAM users\.

**To generate MCS service\-specific credentials \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users** and then choose the name of the user that requires the credentials\.

1. On the **Security Credentials** tab beneath **Credentials for Amazon Managed Apache Cassandra Service \(MCS\)**, choose **Generate credentials**\.

1. Your service\-specific credentials are now available\. This is the only time that the password can be viewed or downloaded\. You cannot recover it later\. However, you can reset your password at any time\. Save the user and password in a secure location, because you'll need them later\.

## Generating MCS Credentials \(AWS CLI\)<a name="mcs_credentials_cli"></a>

You can use the AWS CLI to generate Amazon Managed Apache Cassandra Service \(MCS\) credentials for your IAM users\.

**To generate MCS service\-specific credentials \(AWS CLI\)**
+ Use the following command:
  + [aws iam create\-service\-specific\-credential](https://docs.aws.amazon.com/cli/latest/reference/iam/create-service-specific-credential.html)

## Generating MCS Credentials \(AWS API\)<a name="mcs_credentials_api"></a>

You can use the AWS API to generate Amazon Managed Apache Cassandra Service \(MCS\) credentials for your IAM users\.

**To generate MCS service\-specific credentials \(AWS API\)**
+ Complete the following operation:
  + [CreateServiceSpecificCredential](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateServiceSpecificCredential.html) 