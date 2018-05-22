# Actions, Resources, and Condition Keys for AWS Budget Service<a name="list_awsbudgetservice"></a>

AWS Budget Service \(service prefix: `budgets`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions) permission policies\.

**Topics**
+ [Actions Defined by AWS Budget Service](#awsbudgetservice-actions-as-permissions)
+ [Resources Defined by Budget](#awsbudgetservice-resources-for-iam-policies)
+ [Condition Keys for AWS Budget Service](#awsbudgetservice-policy-keys)

## Actions Defined by AWS Budget Service<a name="awsbudgetservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.

The actions in this table are not APIs, but are instead permissions that grant access to the AWS Billing and Cost Management APIs that access budgets\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions) | Modify budgets and budget details | Write | [budget\*](#awsbudgetservice-budget)  |  |  | 
| [http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions) | View budgets and budget details | Read | [budget\*](#awsbudgetservice-budget)  |  |  | 

## Resources Defined by Budget<a name="awsbudgetservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsbudgetservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-managing-costs.html](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-managing-costs.html) | arn:$\{Partition\}:budgets::$\{Account\}:budget/$\{BudgetName\} |  | 

## Condition Keys for AWS Budget Service<a name="awsbudgetservice-policy-keys"></a>

Budget has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.