# Actions, Resources, and Condition Keys for Amazon Mobile Analytics<a name="list_amazonmobileanalytics"></a>

Amazon Mobile Analytics \(service prefix: `mobileanalytics`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/mobileanalytics/latest/ug/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/mobileanalytics/latest/ug/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/mobileanalytics/latest/ug/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Mobile Analytics](#amazonmobileanalytics-actions-as-permissions)
+ [Resources Defined by Mobile Analytics](#amazonmobileanalytics-resources-for-iam-policies)
+ [Condition Keys for Amazon Mobile Analytics](#amazonmobileanalytics-policy-keys)

## Actions Defined by Amazon Mobile Analytics<a name="amazonmobileanalytics-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| GetFinancialReports | Grant access to financial metrics for an app | Read |  |  |  | 
| GetReports | Grant access to standard metrics for an app | Read |  |  |  | 
| [http://docs.aws.amazon.com/mobileanalytics/latest/ug/PutEvents.html](http://docs.aws.amazon.com/mobileanalytics/latest/ug/PutEvents.html) | The PutEvents operation records one or more events | Write |  |  |  | 

## Resources Defined by Mobile Analytics<a name="amazonmobileanalytics-resources-for-iam-policies"></a>

Mobile Analytics has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Mobile Analytics<a name="amazonmobileanalytics-policy-keys"></a>

Mobile Analytics has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.