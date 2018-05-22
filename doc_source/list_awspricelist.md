# Actions, Resources, and Condition Keys for AWS Price List<a name="list_awspricelist"></a>

AWS Price List \(service prefix: `pricing`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Price List](#awspricelist-actions-as-permissions)
+ [Resources Defined by Price List](#awspricelist-resources-for-iam-policies)
+ [Condition Keys for AWS Price List](#awspricelist-policy-keys)

## Actions Defined by AWS Price List<a name="awspricelist-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_DescribeServices.html](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_DescribeServices.html) | Returns the service details for all \(paginated\) services \(if serviceCode is not set\) or service detail for a particular service \(if given serviceCode\)\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetAttributeValues.html](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetAttributeValues.html) | Returns all \(paginated\) possible values for a given attribute\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetProducts.html](http://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetProducts.html) | Returns all matching products with given search criteria\. | Read |  |  |  | 

## Resources Defined by Price List<a name="awspricelist-resources-for-iam-policies"></a>

Price List has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Price List<a name="awspricelist-policy-keys"></a>

Price List has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.