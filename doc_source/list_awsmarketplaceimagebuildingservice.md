# Actions, Resources, and Condition Keys for AWS Marketplace Image Building Service<a name="list_awsmarketplaceimagebuildingservice"></a>

AWS Marketplace Image Building Service \(service prefix: `aws-marketplace`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://alpha-docs-aws.amazon.com/MIB/latest/APIReference/)\.
+ View a [list of the API operations available for this service](https://alpha-docs-aws.amazon.com/MIB/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://alpha-docs-aws.amazon.com/MIB/latest/APIReference/) permission policies\.

**Topics**
+ [Actions Defined by AWS Marketplace Image Building Service](#awsmarketplaceimagebuildingservice-actions-as-permissions)
+ [Resources Defined by Marketplace Image Build](#awsmarketplaceimagebuildingservice-resources-for-iam-policies)
+ [Condition Keys for AWS Marketplace Image Building Service](#awsmarketplaceimagebuildingservice-policy-keys)

## Actions Defined by AWS Marketplace Image Building Service<a name="awsmarketplaceimagebuildingservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DescribeBuilds ](https://alpha-docs-aws.amazon.com/MIB/latest/APIReference/API_DescribeBuilds.html) \[permission only\] | Describes Image Builds identified by a build Id | Read |  |  |  | 
|   [ ListBuilds ](https://alpha-docs-aws.amazon.com/MIB/latest/APIReference/API_ListBuilds.html) \[permission only\] | Lists Image Builds\. | Read |  |  |  | 
|   [ StartBuild ](https://alpha-docs-aws.amazon.com/MIB/latest/APIReference/API_StartBuild.html) \[permission only\] | Starts an Image Build | Write |  |  |  | 

## Resources Defined by Marketplace Image Build<a name="awsmarketplaceimagebuildingservice-resources-for-iam-policies"></a>

AWS Marketplace Image Building Service has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Marketplace Image Building Service<a name="awsmarketplaceimagebuildingservice-policy-keys"></a>

Marketplace Image Build has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.