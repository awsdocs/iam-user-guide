# Actions, Resources, and Condition Keys for AWS WAF Regional<a name="list_awswafregional"></a>

AWS WAF Regional \(service prefix: `waf-regional`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/waf/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/waf/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/waf/latest/developerguide/waf-auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS WAF Regional](#awswafregional-actions-as-permissions)
+ [Resources Defined by WAF Regional](#awswafregional-resources-for-iam-policies)
+ [Condition Keys for AWS WAF Regional](#awswafregional-policy-keys)

## Actions Defined by AWS WAF Regional<a name="awswafregional-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awswafregional.html)

## Resources Defined by WAF Regional<a name="awswafregional-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awswafregional-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_ByteMatchSet.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_ByteMatchSet.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:bytematchset/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_GeoMatchSet.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_GeoMatchSet.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:geomatchset/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_IPSet.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_IPSet.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:ipset/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_regional_WebACL.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_regional_WebACL.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/app/$\{LoadBalancerName\}/$\{LoadBalancerId\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_regional_RateBasedRule.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_regional_RateBasedRule.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:ratebasedrule/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_RegexMatchSet.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_RegexMatchSet.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:regexmatchset/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_RegexPatternSet.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_RegexPatternSet.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:regexpatternset/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_Rule.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:rule/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_RuleGroup.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:rulegroup/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_SizeConstraintSet.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_SizeConstraintSet.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:sizeconstraintset/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_SqlInjectionMatchSet.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_SqlInjectionMatchSet.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:sqlinjectionmatchset/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_WebACL.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_WebACL.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:webacl/$\{Id\} |  | 
| [http://docs.aws.amazon.com/waf/latest/APIReference/API_XssMatchSet.html](http://docs.aws.amazon.com/waf/latest/APIReference/API_XssMatchSet.html) | arn:$\{Partition\}:waf\-regional:$\{Region\}:$\{Account\}:xssmatchset/$\{Id\} |  | 

## Condition Keys for AWS WAF Regional<a name="awswafregional-policy-keys"></a>

WAF Regional has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.