# Actions, resources, and condition keys for AWS Budget Service<a name="list_awsbudgetservice"></a>

**Tip**  
This page is moving to a new location on November 16, 2020\. Please update your bookmark to use the new page at [https://docs\.aws\.amazon\.com/service\-authorization/latest/reference/list\_awsbudgetservice\.html](https://docs.aws.amazon.com/service-authorization/latest/reference/list_awsbudgetservice.html)\. 

AWS Budget Service \(service prefix: `budgets`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/api-reference.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions) permission policies\.

**Topics**
+ [Actions defined by AWS Budget Service](#awsbudgetservice-actions-as-permissions)
+ [Resource types defined by AWS Budget Service](#awsbudgetservice-resources-for-iam-policies)
+ [Condition keys for AWS Budget Service](#awsbudgetservice-policy-keys)

## Actions defined by AWS Budget Service<a name="awsbudgetservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.

**Note**  
The actions in this table are not APIs, but are instead permissions that grant access to the AWS Billing and Cost Management APIs that access budgets\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateBudgetAction ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to create and define a response that you can configure to execute once your budget has exceeded a specific budget threshold\. | Write |   [ budgetAction\* ](#awsbudgetservice-budgetAction)   |  |   iam:PassRole   | 
|   [ DeleteBudgetAction ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to delete an action that is associated with a specific budget\. | Write |   [ budgetAction\* ](#awsbudgetservice-budgetAction)   |  |  | 
|   [ DescribeBudgetAction ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to retrieve the details of specific budget action associated with a budget\. | Read |   [ budgetAction\* ](#awsbudgetservice-budgetAction)   |  |  | 
|   [ DescribeBudgetActionHistories ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to retrieve a historical view of the budget actions statuses associated with a particular budget action\. These status include statues such as 'Standby', 'Pending' and 'Executed'\. | Read |   [ budgetAction\* ](#awsbudgetservice-budgetAction)   |  |  | 
|   [ DescribeBudgetActionsForAccount ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to retrieve the details of all of the budget actions associated with your account\. | Read |  |  |  | 
|   [ DescribeBudgetActionsForBudget ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to retrieve the details of all of the budget actions associated with a budget\. | Read |   [ budget\* ](#awsbudgetservice-budget)   |  |  | 
|   [ ExecuteBudgetAction ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to initiate a pending budget action as well as reverse a previously executed budget action\. | Write |   [ budgetAction\* ](#awsbudgetservice-budgetAction)   |  |  | 
|   [ ModifyBudget ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to modify budgets and budget details | Write |   [ budget\* ](#awsbudgetservice-budget)   |  |  | 
|   [ UpdateBudgetAction ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to update the details of a specific budget action associated with a budget\. | Write |   [ budgetAction\* ](#awsbudgetservice-budgetAction)   |  |   iam:PassRole   | 
|   [ ViewBudget ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-permissions-ref.html#user-permissions)  | Grants permissions to view budgets and budget details | Read |   [ budget\* ](#awsbudgetservice-budget)   |  |  | 

## Resource types defined by AWS Budget Service<a name="awsbudgetservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsbudgetservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ budget ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-managing-costs.html)  |  arn:$\{Partition\}:budgets::$\{Account\}:budget/$\{BudgetName\}  |  | 
|   [ budgetAction ](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-managing-costs.html)  |  arn:$\{Partition\}:budgets::$\{Account\}:budget/$\{BudgetName\}/action/$\{ActionId\}  |  | 

## Condition keys for AWS Budget Service<a name="awsbudgetservice-policy-keys"></a>

Budget has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.