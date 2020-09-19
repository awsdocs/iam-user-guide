# Actions, resources, and condition keys for AWS WAF Regional<a name="list_awswafregional"></a>

AWS WAF Regional \(service prefix: `waf-regional`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/waf/latest/developerguide/classic-waf-chapter.htm)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/waf/latest/APIReference/API_Operations_AWS_WAF_Regional.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/waf/latest/developerguide/classic-waf-auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by AWS WAF Regional](#awswafregional-actions-as-permissions)
+ [Resource types defined by AWS WAF Regional](#awswafregional-resources-for-iam-policies)
+ [Condition keys for AWS WAF Regional](#awswafregional-policy-keys)

## Actions defined by AWS WAF Regional<a name="awswafregional-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awswafregional.html)

## Resource types defined by AWS WAF Regional<a name="awswafregional-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awswafregional-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ bytematchset ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_ByteMatchSet.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:bytematchset/$\{Id\}  |  | 
|   [ ipset ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_IPSet.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:ipset/$\{Id\}  |  | 
|   [ loadbalancer/app/ ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_WebACL.html)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/app/$\{LoadBalancerName\}/$\{LoadBalancerId\}  |  | 
|   [ ratebasedrule ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_RateBasedRule.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:ratebasedrule/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awswafregional-aws_ResourceTag___TagKey_)   | 
|   [ rule ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_Rule.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:rule/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awswafregional-aws_ResourceTag___TagKey_)   | 
|   [ sizeconstraintset ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_SizeConstraintSet.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:sizeconstraintset/$\{Id\}  |  | 
|   [ sqlinjectionmatchset ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_SqlInjectionMatchSet.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:sqlinjectionset/$\{Id\}  |  | 
|   [ webacl ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_WebACL.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:webacl/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awswafregional-aws_ResourceTag___TagKey_)   | 
|   [ xssmatchset ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_XssMatchSet.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:xssmatchset/$\{Id\}  |  | 
|   [ regexmatchset ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_RegexMatchSet.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:regexmatch/$\{Id\}  |  | 
|   [ regexpatternset ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_RegexPatternSet.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:regexpatternset/$\{Id\}  |  | 
|   [ geomatchset ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_GeoMatchSet.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:geomatchset/$\{Id\}  |  | 
|   [ rulegroup ](https://docs.aws.amazon.com/waf/latest/APIReference/API_wafRegional_RuleGroup.html)  |  arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:rulegroup/$\{Id\}  |   [ aws:ResourceTag/$\{TagKey\} ](#awswafregional-aws_ResourceTag___TagKey_)   | 

## Condition keys for AWS WAF Regional<a name="awswafregional-policy-keys"></a>

AWS WAF Regional defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-requesttag)  | Filters actions based on the allowed set of values for each of the tags | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on tag\-value assoicated with the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-tagkeys)  | Filters actions based on the presence of mandatory tags in the request | String | 