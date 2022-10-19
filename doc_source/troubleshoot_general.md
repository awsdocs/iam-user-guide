# Troubleshooting general IAM issues<a name="troubleshoot_general"></a>

Use the information here to help you diagnose and fix access\-denied or other common issues when you work with AWS Identity and Access Management \(IAM\)\.

**Topics**
+ [I can't sign in to my AWS account](#troubleshoot_general_cant-sign-in)
+ [I lost my access keys](#troubleshoot_general_access-keys)
+ [I get "access denied" when I make a request to an AWS service](#troubleshoot_general_access-denied-service)
+ [I get "access denied" when I make a request with temporary security credentials](#troubleshoot_general_access-denied-temp-creds)
+ [Policy variables aren't working](#troubleshoot_general_policy-variables-dont-work)
+ [Changes that I make are not always immediately visible](#troubleshoot_general_eventual-consistency)
+ [I am not authorized to perform: iam:DeleteVirtualMFADevice](#troubleshoot_general_access-denied-delete-mfa)
+ [How do I securely create IAM users?](#troubleshoot_general_securely-create-iam-users)
+ [Additional resources](#troubleshoot_general_resources)

## I can't sign in to my AWS account<a name="troubleshoot_general_cant-sign-in"></a>

Verify that you have the correct credentials and that you are using the correct method to sign in\. For more information, see [Troubleshoot AWS sign\-in or account issues](troubleshoot_sign_in.md)\.

## I lost my access keys<a name="troubleshoot_general_access-keys"></a>

Access keys consist of two parts:
+ **The access key identifier**\. This is not a secret, and can be seen in the IAM console wherever access keys are listed, such as on the user summary page\.
+ **The secret access key**\. This is provided when you initially create the access key pair\. Just like a password, it ***cannot be retrieved later***\. If you lost your secret access key, then you must create a new access key pair\. If you already have the [maximum number of access keys](reference_iam-quotas.md#reference_iam-quotas-entities), you must delete an existing pair before you can create another\.

For more information, see [Resetting lost or forgotten passwords or access keys for AWS](id_credentials_access-keys_retrieve.md)\.

## I get "access denied" when I make a request to an AWS service<a name="troubleshoot_general_access-denied-service"></a>
+ Check if the error message includes the type of policy responsible for denying access\. For example, if the error mentions that access is denied due to a Service Control Policy \(SCP\), then you can focus on troubleshooting SCP issues\. When you know the policy type, you can also check for a deny statement or a missing allow on the specific action in policies of that policy type\. For more information, see [Troubleshooting access denied error messages](troubleshoot_access-denied.md)\. If the error message doesn't mention the policy type responsible for denying access, use the rest of the guidelines in this section to troubleshoot further\.
+ Verify that you have the identity\-based policy permission to call the action and resource that you have requested\. If any conditions are set, you must also meet those conditions when you send the request\. For information about viewing or modifying policies for an IAM user, group, or role, see [Managing IAM policies](access_policies_manage.md)\.
+ If the AWS Management Console returns a message stating that you're not authorized to perform an action, then you must contact your administrator for assistance\. Your administrator provided you with your sign\-in credentials or sign\-in link\.

  The following example error occurs when the `mateojackson` IAM user attempts to use the console to view details about a fictional `my-example-widget` resource but does not have the fictional `widgets:GetWidget` permissions\.

  ```
  User: arn:aws:iam::123456789012:user/mateojackson is not authorized to perform: widgets:GetWidget on resource: my-example-widget
  ```

  In this case, Mateo must ask his administrator to update his policies to allow access to the `my-example-widget` resource using the `widgets:GetWidget` action\.
+ Are you trying to access a service that supports [resource\-based policies](access_policies_identity-vs-resource.md), such as Amazon S3, Amazon SNS, or Amazon SQS? If so, verify that the policy specifies you as a principal and grants you access\. If you make a request to a service within your account, either your identity\-based policies or the resource\-based policies can grant you permission\. If you make a request to a service in a different account, then both your identity\-based policies and the resource\-based policies must grant you permission\. To view the services that support resource\-based policies, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.
+ If your policy includes a condition with a key–value pair, review it carefully\. Examples include the [`aws:RequestTag/tag-key`](reference_policies_condition-keys.md) global condition key, the AWS KMS [https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context), and the `ResourceTag/tag-key` condition key supported by multiple services\. Make sure that the key name does not match multiple results\. Because condition key names are not case sensitive, a condition that checks for a key named `foo` matches `foo`, `Foo`, or `FOO`\. If your request includes multiple key–value pairs with key names that differ only by case, then your access might be unexpectedly denied\. For more information, see [IAM JSON policy elements: Condition](reference_policies_elements_condition.md)\.
+ If you have a [permissions boundary](access_policies_boundaries.md), verify that the policy that is used for the permissions boundary allows your request\. If your identity\-based policies allow the request, but your permissions boundary does not, then the request is denied\. A permissions boundary controls the maximum permissions that an IAM principal \(user or role\) can have\. Resource\-based policies are not limited by permissions boundaries\. Permissions boundaries are not common\. For more information about how AWS evaluates policies, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.
+ If you are signing requests manually \(without using the [AWS SDKs](http://aws.amazon.com/tools/)\), verify that you have correctly [signed the request](https://docs.aws.amazon.com/general/latest/gr/signing_aws_api_requests.html)\.

## I get "access denied" when I make a request with temporary security credentials<a name="troubleshoot_general_access-denied-temp-creds"></a>
+ First, make sure that you are not denied access for a reason that is unrelated to your temporary credentials\. For more information, see [I get "access denied" when I make a request to an AWS service](#troubleshoot_general_access-denied-service)\.
+ Verify that the service accepts temporary security credentials, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.
+ Verify that your requests are being signed correctly and that the request is well\-formed\. For details, see your [toolkit](http://aws.amazon.com/tools/) documentation or [Using temporary credentials with AWS resources](id_credentials_temp_use-resources.md)\.
+ Verify that your temporary security credentials haven't expired\. For more information, see [Temporary security credentials in IAM](id_credentials_temp.md)\. 
+ Verify that the IAM user or role has the correct permissions\. Permissions for temporary security credentials are derived from an IAM user or role\. As a result, the permissions are limited to those that are granted to the role whose temporary credentials you have assumed\. For more information about how permissions for temporary security credentials are determined, see [Controlling permissions for temporary security credentials](id_credentials_temp_control-access.md)\.
+ If you assumed a role, your role session might be limited by session policies\. When you [request temporary security credentials](id_credentials_temp_request.md) programmatically using AWS STS, you can optionally pass inline or managed [session policies](access_policies.md#policies_session)\. Session policies are advanced policies that you pass as a parameter when you programmatically create a temporary credential session for a role\. You can pass a single JSON inline session policy document using the `Policy` parameter\. You can use the `PolicyArns` parameter to specify up to 10 managed session policies\. The resulting session's permissions are the intersection of the role's identity\-based policies and the session policies\. Alternatively, if your administrator or a custom program provides you with temporary credentials, they might have included a session policy to limit your access\.
+ If you are a federated user, your session might be limited by session policies\. You become a federated user by signing in to AWS as an IAM user and then requesting a federation token\. For more information about federated users, see [[GetFederationToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)—federation through a custom identity broker](id_credentials_temp_request.md#api_getfederationtoken)\. If you or your identity broker passed session policies while requesting a federation token, then your session is limited by those policies\. The resulting session's permissions are the intersection of your IAM user identity\-based policies and the session policies\. For more information about session policies, see [Session policies](access_policies.md#policies_session)\.
+ If you are accessing a resource that has a resource\-based policy by using a role, verify that the policy grants permissions to the role\. For example, the following policy allows `MyRole` from account `111122223333` to access `MyBucket`\.

  ```
  {
    "Version": "2012-10-17",
    "Statement": [{
      "Sid": "S3BucketPolicy",
      "Effect": "Allow",
      "Principal": {"AWS": ["arn:aws:iam::111122223333:role/MyRole"]},
      "Action": ["s3:PutObject"],
      "Resource": ["arn:aws:s3:::MyBucket/*"]
    }]
  }
  ```

## Policy variables aren't working<a name="troubleshoot_general_policy-variables-dont-work"></a>
+ Verify that all policies that include variables include the following version number in the policy: `"Version": "2012-10-17"`\. Without the correct version number, the variables are not replaced during evaluation\. Instead, the variables are evaluated literally\. Any policies that don't include variables will still work if you include the latest version number\.

  A `Version` policy element is different from a policy version\. The `Version` policy element is used within a policy and defines the version of the policy language\. A policy version, on the other hand, is created when you make changes to a customer managed policy in IAM\. The changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new version of the managed policy\. To learn more about the `Version` policy element see [IAM JSON policy elements: Version](reference_policies_elements_version.md)\. To learn more about policy versions, see [Versioning IAM policies](access_policies_managed-versioning.md)\.
+ Verify that your policy variables are in the right case\. For details, see [IAM policy elements: Variables and tags](reference_policies_variables.md)\.

## Changes that I make are not always immediately visible<a name="troubleshoot_general_eventual-consistency"></a>

As a service that is accessed through computers in data centers around the world, IAM uses a distributed computing model called [eventual consistency](https://wikipedia.org/wiki/Eventual_consistency)\. Any change that you make in IAM \(or other AWS services\), including tags used in [attribute\-based access control \(ABAC\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_attribute-based-access-control.html), takes time to become visible from all possible endpoints\. Some of the delay results from the time it takes to send the data from server to server, from replication zone to replication zone, and from Region to Region around the world\. IAM also uses caching to improve performance, but in some cases this can add time\. The change might not be visible until the previously cached data times out\.

You must design your global applications to account for these potential delays\. Ensure that they work as expected, even when a change made in one location is not instantly visible at another\. Such changes include creating or updating users, groups, roles, or policies\. We recommend that you do not include such IAM changes in the critical, high\-availability code paths of your application\. Instead, make IAM changes in a separate initialization or setup routine that you run less frequently\. Also, be sure to verify that the changes have been propagated before production workflows depend on them\. 

For more information about how some other AWS services are affected by this, consult the following resources:
+ **Amazon DynamoDB**: [What is the consistency model of Amazon DynamoDB?](https://aws.amazon.com/dynamodb/faqs) in the *DynamoDB FAQ*, and [Read Consistency](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html) in the Amazon DynamoDB Developer Guide\.
+ **Amazon EC2**: [EC2 Eventual Consistency](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/query-api-troubleshooting.html#eventual-consistency) in the *Amazon EC2 API Reference*\.
+ **Amazon EMR**: [Ensuring Consistency When Using Amazon S3 and Amazon Elastic MapReduce for ETL Workflows](http://aws.amazon.com/blogs/big-data/ensuring-consistency-when-using-amazon-s3-and-amazon-elastic-mapreduce-for-etl-workflows/) in the AWS Big Data Blog
+ **Amazon Redshift**: [Managing Data Consistency](https://docs.aws.amazon.com/redshift/latest/dg/managing-data-consistency.html) in the *Amazon Redshift Database Developer Guide*
+ **Amazon S3**: [Amazon S3 Data Consistency Model](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html#ConsistencyModel) in the *Amazon Simple Storage Service User Guide*

## I am not authorized to perform: iam:DeleteVirtualMFADevice<a name="troubleshoot_general_access-denied-delete-mfa"></a>

You might receive the following error when you attempt to assign or remove a virtual MFA device for yourself or others:

```
User: arn:aws:iam::123456789012:user/Diego is not authorized to perform: iam:DeleteVirtualMFADevice on resource: arn:aws:iam::123456789012:mfa/Diego with an explicit deny
```

This could happen if someone previously began assigning a virtual MFA device to a user in the IAM console and then cancelled the process\. This creates an MFA device for the user in IAM but never activates it\. You must delete the existing MFA device before you can associate a new device with the user\.

AWS recommends a policy that allows a user to delete their own virtual MFA device only if they are authenticated using MFA\. For more information, see [AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the My Security Credentials page](reference_policies_examples_aws_my-sec-creds-self-manage.md)\. 

To fix this issue, an administrator should **not** edit policy permissions\. Instead, the administrator must use the AWS CLI or AWS API to remove the existing but deactivated device\.

**To delete an existing but deactivated MFA device**

1. View the virtual MFA devices in your account\.
   + AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/list-virtual-mfa-devices.html](https://docs.aws.amazon.com/cli/latest/reference/iam/list-virtual-mfa-devices.html)
   + AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListVirtualMFADevices.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListVirtualMFADevices.html)

1. In the response, locate the ARN of the virtual device for the user you are trying to fix\.

1. Delete the device\.
   + AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/delete-virtual-mfa-device.html](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-virtual-mfa-device.html)
   + AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteVirtualMFADevice.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteVirtualMFADevice.html)

## How do I securely create IAM users?<a name="troubleshoot_general_securely-create-iam-users"></a>

If you have employees that require access to AWS, you might choose to create IAM users or [use IAM Identity Center for authentication](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)\. If you use IAM, AWS recommends that you create an IAM user and securely communicate the credentials to the employee\. If you are not physically located next to your employee, use a secure workflow to communicate credentials to employees\.

Use the following workflow to securely create a new user in IAM:

1. [Create a new user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html) using the AWS Management Console\. Choose to grant AWS Management Console access with an auto\-generated password\. If necessary, select the **Users must create a new password at next sign\-in** check box\. Do not add a permissions policy to the user until after they have changed their password\.

1. After the user is added, copy the sign\-in URL, user name, and password for the new user\. To view the password, choose **Show**\.

1. Send the password to your employee using a secure communications method in your company, such as email, chat, or a ticketing system\. Separately, provide your users with the IAM user console link and their user name\. Tell the employee to confirm that they can sign in successfully before you will grant them permissions\.

1. After the employee confirms, add the permissions that they need\. As a security best practice, add a policy that requires the user to authenticate using MFA to manage their credentials\. For an example policy, see [AWS: Allows MFA\-authenticated IAM users to manage their own credentials on the My Security Credentials page](reference_policies_examples_aws_my-sec-creds-self-manage.md)\.

## Additional resources<a name="troubleshoot_general_resources"></a>

The following resources can help you troubleshoot as you work with AWS\.
+ **[AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)** – Use AWS CloudTrail to track a history of API calls made to AWS and store that information in log files\. This helps you determine which users and accounts accessed resources in your account, when the calls were made, what actions were requested, and more\. For more information, see [Logging IAM and AWS STS API calls with AWS CloudTrail](cloudtrail-integration.md)\.
+ **[AWS Knowledge Center](http://aws.amazon.com/premiumsupport/knowledge-center/)** – Find FAQs and links to other resources to help you troubleshoot issues\.
+ **[AWS Support Center](https://console.aws.amazon.com/support/home#/)** – Get technical support\.
+ **[AWS Premium Support Center](https://aws.amazon.com/premiumsupport/)** – Get premium technical support\.