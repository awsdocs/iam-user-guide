# Actions, resources, and condition keys for Elastic Load Balancing<a name="list_elasticloadbalancing"></a>

Elastic Load Balancing \(service prefix: `elasticloadbalancing`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/load-balancer-authentication-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Elastic Load Balancing](#elasticloadbalancing-actions-as-permissions)
+ [Resource types defined by Elastic Load Balancing](#elasticloadbalancing-resources-for-iam-policies)
+ [Condition keys for Elastic Load Balancing](#elasticloadbalancing-policy-keys)

## Actions defined by Elastic Load Balancing<a name="elasticloadbalancing-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddTags ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_AddTags.html)  | Adds the specified tags to the specified load balancer\. Each load balancer can have a maximum of 10 tags | Tagging |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ ApplySecurityGroupsToLoadBalancer ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_ApplySecurityGroupsToLoadBalancer.html)  | Associates one or more security groups with your load balancer in a virtual private cloud \(VPC\) | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ AttachLoadBalancerToSubnets ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_AttachLoadBalancerToSubnets.html)  | Adds one or more subnets to the set of configured subnets for the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ ConfigureHealthCheck ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_ConfigureHealthCheck.html)  | Specifies the health check settings to use when evaluating the health state of your back\-end instances | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ CreateAppCookieStickinessPolicy ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_CreateAppCookieStickinessPolicy.html)  | Generates a stickiness policy with sticky session lifetimes that follow that of an application\-generated cookie | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ CreateLBCookieStickinessPolicy ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_CreateLBCookieStickinessPolicy.html)  | Generates a stickiness policy with sticky session lifetimes controlled by the lifetime of the browser \(user\-agent\) or a specified expiration period | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ CreateLoadBalancer ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_CreateLoadBalancer.html)  | Creates a load balancer | Write |   [ loadbalancer ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ CreateLoadBalancerListeners ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_CreateLoadBalancerListeners.html)  | Creates one or more listeners for the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ CreateLoadBalancerPolicy ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_CreateLoadBalancerPolicy.html)  | Creates a policy with the specified attributes for the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ DeleteLoadBalancer ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DeleteLoadBalancer.html)  | Deletes the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ DeleteLoadBalancerListeners ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DeleteLoadBalancerListeners.html)  | Deletes the specified listeners from the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ DeleteLoadBalancerPolicy ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DeleteLoadBalancerPolicy.html)  | Deletes the specified policy from the specified load balancer\. This policy must not be enabled for any listeners | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ DeregisterInstancesFromLoadBalancer ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DeregisterInstancesFromLoadBalancer.html)  | Deregisters the specified instances from the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ DescribeInstanceHealth ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DescribeInstanceHealth.html)  | Describes the state of the specified instances with respect to the specified load balancer | Read |  |  |  | 
|   [ DescribeLoadBalancerAttributes ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DescribeLoadBalancerAttributes.html)  | Describes the attributes for the specified load balancer | Read |  |  |  | 
|   [ DescribeLoadBalancerPolicies ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DescribeLoadBalancerPolicies.html)  | Describes the specified policies | Read |  |  |  | 
|   [ DescribeLoadBalancerPolicyTypes ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DescribeLoadBalancerPolicyTypes.html)  | Describes the specified load balancer policy types | Read |  |  |  | 
|   [ DescribeLoadBalancers ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DescribeLoadBalancers.html)  | Describes the specified the load balancers\. If no load balancers are specified, the call describes all of your load balancers | List |  |  |  | 
|   [ DescribeTags ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DescribeTags.html)  | Describes the tags associated with the specified load balancers | Read |  |  |  | 
|   [ DetachLoadBalancerFromSubnets ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DetachLoadBalancerFromSubnets.html)  | Removes the specified subnets from the set of configured subnets for the load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ DisableAvailabilityZonesForLoadBalancer ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_DisableAvailabilityZonesForLoadBalancer.html)  | Removes the specified Availability Zones from the set of Availability Zones for the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ EnableAvailabilityZonesForLoadBalancer ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_EnableAvailabilityZonesForLoadBalancer.html)  | Adds the specified Availability Zones to the set of Availability Zones for the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ ModifyLoadBalancerAttributes ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_ModifyLoadBalancerAttributes.html)  | Modifies the attributes of the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ RegisterInstancesWithLoadBalancer ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_RegisterInstancesWithLoadBalancer.html)  | Adds the specified instances to the specified load balancer | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ RemoveTags ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_RemoveTags.html)  | Removes one or more tags from the specified load balancer | Tagging |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ SetLoadBalancerListenerSSLCertificate ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_SetLoadBalancerListenerSSLCertificate.html)  | Sets the certificate that terminates the specified listener's SSL connections | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ SetLoadBalancerPoliciesForBackendServer ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_SetLoadBalancerPoliciesForBackendServer.html)  | Replaces the set of policies associated with the specified port on which the back\-end server is listening with a new set of policies | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 
|   [ SetLoadBalancerPoliciesOfListener ](https://docs.aws.amazon.com/elasticloadbalancing/2012-06-01/APIReference/API_SetLoadBalancerPoliciesOfListener.html)  | Replaces the current set of policies for the specified load balancer port with the specified set of policies | Write |   [ loadbalancer\* ](#elasticloadbalancing-loadbalancer)   |  |  | 

## Resource types defined by Elastic Load Balancing<a name="elasticloadbalancing-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#elasticloadbalancing-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ listener ](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-listener-config.html)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:listener/$\{LoadBalancerName\}/$\{LoadBalancerId\}/$\{ListenerId\}  |  | 
|   [ loadbalancer ](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)  |  arn:$\{Partition\}:elasticloadbalancing:$\{Region\}:$\{Account\}:loadbalancer/$\{LoadBalancerName\}  |   [ aws:RequestTag/$\{TagKey\} ](#elasticloadbalancing-aws_RequestTag___TagKey_)   [ aws:TagKeys ](#elasticloadbalancing-aws_TagKeys)   [ elasticloadbalancing:ResourceTag/$\{TagKey\} ](#elasticloadbalancing-elasticloadbalancing_ResourceTag___TagKey_)   | 

## Condition keys for Elastic Load Balancing<a name="elasticloadbalancing-policy-keys"></a>

Elastic Load Balancing defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   aws:RequestTag/$\{TagKey\}  | A key that is present in the request the user makes to the ELB service | String | 
|   aws:TagKeys  | The list of all the tag key names associated with the resource in the request | String | 
|   elasticloadbalancing:ResourceTag/  | The preface string for a tag key and value pair attached to a resource | String | 
|   elasticloadbalancing:ResourceTag/$\{TagKey\}  | A tag key and value pair | String | 