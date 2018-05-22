# Actions, Resources, and Condition Keys for AWS Code Signing for Amazon FreeRTOS<a name="list_awscodesigningforamazonfreertos"></a>

AWS Code Signing for Amazon FreeRTOS \(service prefix: `signer`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by AWS Code Signing for Amazon FreeRTOS](#awscodesigningforamazonfreertos-actions-as-permissions)
+ [Resources Defined by Signer](#awscodesigningforamazonfreertos-resources-for-iam-policies)
+ [Condition Keys for AWS Code Signing for Amazon FreeRTOS](#awscodesigningforamazonfreertos-policy-keys)

## Actions Defined by AWS Code Signing for Amazon FreeRTOS<a name="awscodesigningforamazonfreertos-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/signer/latest/api/API_DescribeSigningJob.html](http://docs.aws.amazon.com/signer/latest/api/API_DescribeSigningJob.html) | Describe the signing job request\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/signer/latest/api/API_ListSigningJobs.html](http://docs.aws.amazon.com/signer/latest/api/API_ListSigningJobs.html) | List signing jobs\. | List |  |  |  | 
| [http://docs.aws.amazon.com/signer/latest/api/API_StartSigningJob.html](http://docs.aws.amazon.com/signer/latest/api/API_StartSigningJob.html) | Start a code signing request\. | Write |  |  |  | 

## Resources Defined by Signer<a name="awscodesigningforamazonfreertos-resources-for-iam-policies"></a>

Signer has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Code Signing for Amazon FreeRTOS<a name="awscodesigningforamazonfreertos-policy-keys"></a>

Signer has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.