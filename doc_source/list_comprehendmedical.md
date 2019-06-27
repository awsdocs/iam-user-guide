# Actions, Resources, and Condition Keys for Comprehend Medical<a name="list_comprehendmedical"></a>

Comprehend Medical \(service prefix: `comprehendmedical`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/comprehend/latest/dg/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/comprehend/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/comprehend/latest/dg/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Comprehend Medical](#comprehendmedical-actions-as-permissions)
+ [Resources Defined by Comprehend Medical](#comprehendmedical-resources-for-iam-policies)
+ [Condition Keys for Comprehend Medical](#comprehendmedical-policy-keys)

## Actions Defined by Comprehend Medical<a name="comprehendmedical-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ DetectEntities ](https://docs.aws.amazon.com/comprehend/latest/dg/API_hera_DetectEntities.html)  | Inspects the specified text for the specified type of entities and returns information about them\. | Read |  |  |  | 
|   [ DetectPHI ](https://docs.aws.amazon.com/comprehend/latest/dg/API_hera_DetectPHI.html)  | Inspects the specified text for PHI entities and returns information about them\. | Read |  |  |  | 

## Resources Defined by Comprehend Medical<a name="comprehendmedical-resources-for-iam-policies"></a>

Comprehend Medical has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Comprehend Medical<a name="comprehendmedical-policy-keys"></a>

ComprehendMedical has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.