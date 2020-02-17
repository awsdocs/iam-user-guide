# Actions, Resources, and Condition Keys for Amazon Macie<a name="list_amazonmacie"></a>

Amazon Macie \(service prefix: `macie`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/macie/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/macie/1.0/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/macie/latest/userguide/macie-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Macie](#amazonmacie-actions-as-permissions)
+ [Resource Types Defined by Amazon Macie](#amazonmacie-resources-for-iam-policies)
+ [Condition Keys for Amazon Macie](#amazonmacie-policy-keys)

## Actions Defined by Amazon Macie<a name="amazonmacie-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateMemberAccount ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_AssociateMemberAccount.html)  | Enables the user to associate a specified AWS account with Amazon Macie as a member account\. | Write |  |  |  | 
|   [ AssociateS3Resources ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_AssociateS3Resources.html)  | Enables the user to associate specified S3 resources with Amazon Macie for monitoring and data classification\. | Write |  |   [ aws:SourceArn ](#amazonmacie-aws_SourceArn)   |  | 
|   [ DisassociateMemberAccount ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_DisassociateMemberAccount.html)  | Enables the user to remove the specified member account from Amazon Macie\. | Write |  |  |  | 
|   [ DisassociateS3Resources ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_DisassociateS3Resources.html)  | Enables the user to remove specified S3 resources from being monitored by Amazon Macie\. | Write |  |   [ aws:SourceArn ](#amazonmacie-aws_SourceArn)   |  | 
|   [ ListMemberAccounts ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_ListMemberAccounts.html)  | Enables the user to list all Amazon Macie member accounts for the current Macie master account\. | List |  |  |  | 
|   [ ListS3Resources ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_ListS3Resources.html)  | Enables the user to list all the S3 resources associated with Amazon Macie\. | List |  |  |  | 
|   [ UpdateS3Resources ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_UpdateS3Resources.html)  | Enables the user to update the classification types for the specified S3 resources\. | Write |  |   [ aws:SourceArn ](#amazonmacie-aws_SourceArn)   |  | 

## Resource Types Defined by Amazon Macie<a name="amazonmacie-resources-for-iam-policies"></a>

Amazon Macie does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Macie, specify `“Resource”: “*”` in your policy\.

## Condition Keys for Amazon Macie<a name="amazonmacie-policy-keys"></a>

Amazon Macie defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   aws:SourceArn  | Allow access to the specified actions only when the request operates on the specified aws resource | Arn | 