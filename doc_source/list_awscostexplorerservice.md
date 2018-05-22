# Actions, Resources, and Condition Keys for AWS Cost Explorer Service<a name="list_awscostexplorerservice"></a>

AWS Cost Explorer Service \(service prefix: `ce`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-explorer-access.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Cost Explorer Service](#awscostexplorerservice-actions-as-permissions)
+ [Resources Defined by Cost Explorer Service](#awscostexplorerservice-resources-for-iam-policies)
+ [Condition Keys for AWS Cost Explorer Service](#awscostexplorerservice-policy-keys)

## Actions Defined by AWS Cost Explorer Service<a name="awscostexplorerservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetCostAndUsage.html](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetCostAndUsage.html) | Get cost and usage metrics for your account | Read |  |  |  | 
| [http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetDimensionValues.html](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetDimensionValues.html) | Retrieve all available filter values for a filter over a period of time\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetReservationUtilization.html](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetReservationUtilization.html) | Get reservation utilization for your account\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetTags.html](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetTags.html) | Query tags for a specified time period\. | Read |  |  |  | 

## Resources Defined by Cost Explorer Service<a name="awscostexplorerservice-resources-for-iam-policies"></a>

Cost Explorer Service has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Cost Explorer Service<a name="awscostexplorerservice-policy-keys"></a>

Cost Explorer Service has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.