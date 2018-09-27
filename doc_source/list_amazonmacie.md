# Actions, Resources, and Condition Keys for Amazon Macie<a name="list_amazonmacie"></a>

Amazon Macie \(service prefix: `macie`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com//macie/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com//macie/1.0/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com//macie/latest/userguide/macie-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Macie](#amazonmacie-actions-as-permissions)
+ [Resources Defined by Macie](#amazonmacie-resources-for-iam-policies)
+ [Condition Keys for Amazon Macie](#amazonmacie-policy-keys)

## Actions Defined by Amazon Macie<a name="amazonmacie-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateMemberAccount ](https://docs.aws.amazon.com//macie/1.0/APIReference/API_AssociateMemberAccount.html)  | Enables the user to associate a specified AWS account with Amazon Macie as a member account\. | Write |  |  |  | 
|   [ AssociateS3Resources ](https://docs.aws.amazon.com//macie/1.0/APIReference/API_AssociateS3Resources.html)  | Enables the user to associate specified S3 resources with Amazon Macie for monitoring and data classification\. | Write |  |  |  | 
|   [ DisassociateMemberAccount ](https://docs.aws.amazon.com//macie/1.0/APIReference/API_DisassociateMemberAccount.html)  | Enables the user to remove the specified member account from Amazon Macie\. | Write |  |  |  | 
|   [ DisassociateS3Resources ](https://docs.aws.amazon.com//macie/1.0/APIReference/API_DisassociateS3Resources.html)  | Enables the user to remove specified S3 resources from being monitored by Amazon Macie\. | Write |  |  |  | 
|   [ ListMemberAccounts ](https://docs.aws.amazon.com//macie/1.0/APIReference/API_ListMemberAccounts.html)  | Enables the user to list all Amazon Macie member accounts for the current Macie master account\. | List |  |  |  | 
|   [ ListS3Resources ](https://docs.aws.amazon.com//macie/1.0/APIReference/API_ListS3Resources.html)  | Enables the user to list all the S3 resources associated with Amazon Macie\. | List |  |  |  | 
|   [ UpdateS3Resources ](https://docs.aws.amazon.com//macie/1.0/APIReference/API_UpdateS3Resources.html)  | Enables the user to update the classification types for the specified S3 resources\. | Write |  |  |  | 

## Resources Defined by Macie<a name="amazonmacie-resources-for-iam-policies"></a>

Amazon Macie has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Macie<a name="amazonmacie-policy-keys"></a>

Macie has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.