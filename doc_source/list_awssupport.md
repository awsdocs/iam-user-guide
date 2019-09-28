# Actions, Resources, and Condition Keys for AWS Support<a name="list_awssupport"></a>

AWS Support \(service prefix: `support`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/awssupport/latest/user/getting-started.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/awssupport/latest/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/awssupport/latest/user/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Support](#awssupport-actions-as-permissions)
+ [Resources Defined by AWS Support](#awssupport-resources-for-iam-policies)
+ [Condition Keys for AWS Support](#awssupport-policy-keys)

## Actions Defined by AWS Support<a name="awssupport-actions-as-permissions"></a>

AWS Support has no API operations that can be used in the `Actions` element of an IAM policy statement\. To allow access to AWS Support, specify `“Action”: “support:*”` in your policy\.

**Note**  
Support does not let you allow or deny access to individual actions; therefore your policy must use the "Action": "support:\*" to use the AWS Support Center or to use the Support API\. In addition, when you use the Support API to call Trusted Advisor\-related actions \(such as DescribeTrustedAdvisorChecks\), none of the "trustedadvisor:\*" actions restrict your access\. The "trustedadvisor:\*" actions apply only to TrustedAdvisor in the Console\.

## Resources Defined by AWS Support<a name="awssupport-resources-for-iam-policies"></a>

AWS Support does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to AWS Support, specify `“Resource”: “*”` in your policy\.

## Condition Keys for AWS Support<a name="awssupport-policy-keys"></a>

Support has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.