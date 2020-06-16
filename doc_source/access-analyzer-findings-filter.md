# Filtering Findings<a name="access-analyzer-findings-filter"></a>

The default filtering for the page is to display all active findings\. To view archived findings, choose the **Archived** tab\. When you first start using Access Analyzer, there are no archived findings\.

Use filters to display only the findings for a specific resource, account, principal, or other value\. To create a filter, select the property to filter on, then choose a property value to filter on\. For example, to create a filter that displays only findings for a specific AWS account, choose **AWS Account** for the property, then enter the account number for the AWS account that you want to view findings for\.

**To filter the findings displayed**

1. Choose the **Filter active findings** field\.

1. Choose the property to use to filter the findings displayed\.

1. Choose the value to match for the property\. Only findings with that value in the finding are displayed\.

   For example, if you choose **Resource** as the property, type part or all of the name of a bucket, then press Enter\. Only findings for the bucket that matches the filer criteria are displayed\.

You can add additional properties to further filter the findings displayed\. When you add additional properties, only findings that match all conditions in the filter are displayed\. Defining a filter to display findings that match one property OR another property is not supported\.

Some fields are displayed only when you are viewing findings for an analyzer with an organization as its zone of trust\.

The following properties are available for defining filters:
+ **Resource** – To filter by resource, type all or part of the name of the resource\.
+ **Resource Type** – To filter by resource type, choose the type from the list displayed\.
+ **AWS Account** – Use this property to filter by AWS account that is granted access in the **Principal** section of a policy statement\. To filter by AWS account, type all or part of the 12\-digit AWS account ID, or all or part of the full account ARN of the external AWS user or role that has access to resources in the current account\.
+ **Canonical User** – To filter by canonical user, type the canonical user ID as defined for S3 buckets\. To learn more, see [AWS Account Identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html)\.
+ **Federated User** – To filter by federated user, type all or part of the ARN of the federated identity\. To learn more, see [Identity Providers and Federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html)\.
+ **Principal ARN** – Use this property to filter on the ARN of the principal \(IAM user, role, or group\) used in an **aws:PrincipalArn** condition key\. To filter by Principal ARN, type all or part of the ARN of the IAM user, role, or group from an external AWS account reported in a finding\.
+ **Principal OrgID** – To filter by Principal OrgID, type all or part of the organization ID associated with the external principals that belong to the AWS organization specified as a condition in the finding\. To learn more, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html)\.
+ **Principal Org Paths** – To filter by Principal Org Paths, type all or part of the ID for the AWS organization or organizational unit \(OU\) that allows access to all external principals that are account members of the specified organization or OU as a condition in the policy\. To learn more, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html)\.
+ **Source Account** – To filter on source account, type all or part of the AWS account ID associated with the resources, as used in some cross\-service permissions in AWS\.
+ **Source ARN** – To filter by Source ARN, type all or part of the ARN specified as a condition in the finding\. To learn more, see To filter by Principal Org Paths, type all or part of the ID for the AWS organization or organizational unit \(OU\) that allows access to all external principals that are account members of the specified organization or OU as a condition in the policy\. To learn more, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html)\.
+ **Source IP** – To filter by Source IP, type all or part of the IP address that allows external entities access to resources in the current account when using the specified IP address\. To learn more, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html)\.
+ **Source VPC** – To filter by Source VPC, type all or part of the VPC ID that allows external entities access to resources in the current account when using the specified VPC\. To learn more, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html)\.
+ **Source VPCE** – filter by Source VPCE, type all or part of the VPC endpoint ID that allows external entities access to resources in the current account when using the specified VPC endpoint\. To learn more, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html)\.
+ **User ID** – To filter by User ID, type all or part of the user ID of the IAM user from an external AWS account who is allowed access to resource in the current account\. To learn more, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html)\.
+ **KMS Key ID** – To filter by KMS Key ID, type all or part of the key ID for the KMS key specified as a condition for KMS\-encrypted S3 object access in your current account\.
+ **Google Audience** – To filter by Google Audience, type all or part of the Google application ID specified as a condition for IAM role access in your current account\. To learn more, see [IAM and AWS STS Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html)\.
+ **Cognito Audience** – To filter by Cognito Audience, type all or part of the Amazon Cognito identity pool ID specified as a condition for IAM role access in your current account\. To learn more, see [IAM and AWS STS Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html)\.
+ **Caller Account** – The AWS account ID of the account that owns or contains the calling entity, such as an IAM role, user, or account root user\. This is used by services calling KMS\. To filter by caller account, type all or part of the AWS account ID\.
+ **Facebook App ID** – To filter by Facebook App ID, type all or part of the Facebook application ID \(or site ID\) specified as a condition to allow Login with Facebook federation access to an IAM role in your current account\. To learn more, see [IAM and AWS STS Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html)\.
+ **Amazon App ID** – To filter by Amazon App ID, type all or part of the Amazon application ID \(or site ID\) specified as a condition to allow Login with Amazon federation access to an IAM role in your current account\. To learn more, see [IAM and AWS STS Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_iam-condition-keys.html)\.
+ **Lambda Event Source Token** – To filter on Lambda Event Source Token passed in with Alexa integrations, type all or part of the token string\.