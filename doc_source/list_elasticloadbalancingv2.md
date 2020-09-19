# Actions, resources, and condition keys for Elastic Load Balancing V2<a name="list_elasticloadbalancingv2"></a>

Elastic Load Balancing V2 \(service prefix: `elasticloadbalancing`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/elasticloadbalancing/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/load-balancer-authentication-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Elastic Load Balancing V2](#elasticloadbalancingv2-actions-as-permissions)
+ [Resource types defined by Elastic Load Balancing V2](#elasticloadbalancingv2-resources-for-iam-policies)
+ [Condition keys for Elastic Load Balancing V2](#elasticloadbalancingv2-policy-keys)

## Actions defined by Elastic Load Balancing V2<a name="elasticloadbalancingv2-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_elasticloadbalancingv2.html)

## Resource types defined by Elastic Load Balancing V2<a name="elasticloadbalancingv2-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#elasticloadbalancingv2-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ listener/app ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listener/app/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\}  |  | 
|   [ listener\-rule/app ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-update-rules.html)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listener\-rule/app/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\}/$\{ListenerRuleId\}  |  | 
|   [ listener/net ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listener/net/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\}  |  | 
|   [ listener\-rule/net ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-update-rules.html)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listener\-rule/net/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\}/$\{ListenerRuleId\}  |  | 
|   [ loadbalancer/app/ ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html#application-load-balancer-overview)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/app/$\{LoadBalancerName\}/$\{LoadBalancerId\}  |   [ aws:RequestTag/$\{TagKey\} ](#elasticloadbalancingv2-aws_RequestTag___TagKey_)   [ aws:TagKeys ](#elasticloadbalancingv2-aws_TagKeys)   [ elasticloadbalancing:ResourceTag/$\{TagKey\} ](#elasticloadbalancingv2-elasticloadbalancing_ResourceTag___TagKey_)   | 
|   [ loadbalancer/net/ ](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html#network-load-balancer-overview)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/net/$\{LoadBalancerName\}/$\{LoadBalancerId\}  |   [ aws:RequestTag/$\{TagKey\} ](#elasticloadbalancingv2-aws_RequestTag___TagKey_)   [ aws:TagKeys ](#elasticloadbalancingv2-aws_TagKeys)   [ elasticloadbalancing:ResourceTag/$\{TagKey\} ](#elasticloadbalancingv2-elasticloadbalancing_ResourceTag___TagKey_)   | 
|   [ targetgroup ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:targetgroup/$\{TargetGroupName\}/$\{TargetGroupId\}  |   [ aws:RequestTag/$\{TagKey\} ](#elasticloadbalancingv2-aws_RequestTag___TagKey_)   [ aws:TagKeys ](#elasticloadbalancingv2-aws_TagKeys)   [ elasticloadbalancing:ResourceTag/$\{TagKey\} ](#elasticloadbalancingv2-elasticloadbalancing_ResourceTag___TagKey_)   | 

## Condition keys for Elastic Load Balancing V2<a name="elasticloadbalancingv2-policy-keys"></a>

Elastic Load Balancing V2 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   aws:RequestTag/$\{TagKey\}  | A key that is present in the request the user makes to the ELB service | String | 
|   aws:TagKeys  | The list of all the tag key names associated with the resource in the request | String | 
|   elasticloadbalancing:ResourceTag/$\{TagKey\}  | A tag key and value pair\. | String | 