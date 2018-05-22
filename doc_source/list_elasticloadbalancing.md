# Actions, Resources, and Condition Keys for Elastic Load Balancing<a name="list_elasticloadbalancing"></a>

Elastic Load Balancing \(service prefix: `elasticloadbalancing`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/load-balancer-authentication-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Elastic Load Balancing](#elasticloadbalancing-actions-as-permissions)
+ [Resources Defined by ELB](#elasticloadbalancing-resources-for-iam-policies)
+ [Condition Keys for Elastic Load Balancing](#elasticloadbalancing-policy-keys)

## Actions Defined by Elastic Load Balancing<a name="elasticloadbalancing-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_elasticloadbalancing.html)

## Resources Defined by ELB<a name="elasticloadbalancing-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#elasticloadbalancing-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-listeners.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listener/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\} |  | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-update-rules.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-update-rules.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listenerrule/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\}/$\{ListenerRuleId\} |  | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/$\{LoadBalancerName\} |  | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/application/application-load-balancers.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/application/application-load-balancers.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/app/$\{LoadBalancerName\}/$\{LoadBalancerId\} |  | 
| [http://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html](http://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) | arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:targetgroup/$\{TargetGroupName\}/$\{TargetGroupId\} |  | 

## Condition Keys for Elastic Load Balancing<a name="elasticloadbalancing-policy-keys"></a>

ELB has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.