# Actions, Resources, and Condition Keys for Elastic Load Balancing V2<a name="list_elasticloadbalancingv2"></a>

Elastic Load Balancing V2 \(service prefix: `elasticloadbalancing`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/elasticloadbalancing/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/load-balancer-authentication-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Elastic Load Balancing V2](#elasticloadbalancingv2-actions-as-permissions)
+ [Resources Defined by ELB v2](#elasticloadbalancingv2-resources-for-iam-policies)
+ [Condition Keys for Elastic Load Balancing V2](#elasticloadbalancingv2-policy-keys)

## Actions Defined by Elastic Load Balancing V2<a name="elasticloadbalancingv2-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_elasticloadbalancingv2.html)

## Resources Defined by ELB v2<a name="elasticloadbalancingv2-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#elasticloadbalancingv2-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listener/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\} |  | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-update-rules.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-update-rules.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listener\-rule/app/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\}/$\{ListenerRuleId\} |  | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html#application-load-balancer-overview](http://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html#application-load-balancer-overview) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/app/$\{LoadBalancerName\}/$\{LoadBalancerId\} | [aws:RequestTag/tag\-key](#elasticloadbalancingv2-aws_RequestTag_tag-key) [aws:TagKeys](#elasticloadbalancingv2-aws_TagKeys) [elasticloadbalancing:ResourceTag/tag\-key](#elasticloadbalancingv2-elasticloadbalancing_ResourceTag_tag-key)  | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html#network-load-balancer-overview](http://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html#network-load-balancer-overview) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/net/$\{LoadBalancerName\}/$\{LoadBalancerId\} | [aws:RequestTag/tag\-key](#elasticloadbalancingv2-aws_RequestTag_tag-key) [aws:TagKeys](#elasticloadbalancingv2-aws_TagKeys) [elasticloadbalancing:ResourceTag/tag\-key](#elasticloadbalancingv2-elasticloadbalancing_ResourceTag_tag-key)  | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/elasticloadbalancing/latest/application/load-balancer-target-groups.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/elasticloadbalancing/latest/application/load-balancer-target-groups.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:targetgroup/$\{TargetGroupName\}/$\{TargetGroupId\} | [aws:RequestTag/tag\-key](#elasticloadbalancingv2-aws_RequestTag_tag-key) [aws:TagKeys](#elasticloadbalancingv2-aws_TagKeys) [elasticloadbalancing:ResourceTag/tag\-key](#elasticloadbalancingv2-elasticloadbalancing_ResourceTag_tag-key)  | 

## Condition Keys for Elastic Load Balancing V2<a name="elasticloadbalancingv2-policy-keys"></a>

Elastic Load Balancing V2 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| aws:RequestTag/tag\-key | A key that is present in the request the user makes to the ELB service\. | String | 
| aws:TagKeys | The list of all the tag key names associated with the resource in the request\. | String | 
| elasticloadbalancing:ResourceTag/ | The preface string for a tag key and value pair attached to a resource\. | String | 
| elasticloadbalancing:ResourceTag/tag\-key | A tag key and value pair\. | String | 