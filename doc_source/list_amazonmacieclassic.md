# Actions, resources, and condition keys for Amazon Macie Classic<a name="list_amazonmacieclassic"></a>

Amazon Macie Classic \(service prefix: `macie`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/macie/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/macie/1.0/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/macie/latest/userguide/macie-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Macie Classic](#amazonmacieclassic-actions-as-permissions)
+ [Resource types defined by Amazon Macie Classic](#amazonmacieclassic-resources-for-iam-policies)
+ [Condition keys for Amazon Macie Classic](#amazonmacieclassic-policy-keys)

## Actions defined by Amazon Macie Classic<a name="amazonmacieclassic-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateMemberAccount ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_AssociateMemberAccount.html)  | Enables the user to associate a specified AWS account with Amazon Macie as a member account\. | Write |  |  |  | 
|   [ AssociateS3Resources ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_AssociateS3Resources.html)  | Enables the user to associate specified S3 resources with Amazon Macie for monitoring and data classification\. | Write |  |   [ aws:SourceArn ](#amazonmacieclassic-aws_SourceArn)   |  | 
|   [ DisassociateMemberAccount ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_DisassociateMemberAccount.html)  | Enables the user to remove the specified member account from Amazon Macie\. | Write |  |  |  | 
|   [ DisassociateS3Resources ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_DisassociateS3Resources.html)  | Enables the user to remove specified S3 resources from being monitored by Amazon Macie\. | Write |  |   [ aws:SourceArn ](#amazonmacieclassic-aws_SourceArn)   |  | 
|   [ ListMemberAccounts ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_ListMemberAccounts.html)  | Enables the user to list all Amazon Macie member accounts for the current Macie master account\. | List |  |  |  | 
|   [ ListS3Resources ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_ListS3Resources.html)  | Enables the user to list all the S3 resources associated with Amazon Macie\. | List |  |  |  | 
|   [ UpdateS3Resources ](https://docs.aws.amazon.com/macie/1.0/APIReference/API_UpdateS3Resources.html)  | Enables the user to update the classification types for the specified S3 resources\. | Write |  |   [ aws:SourceArn ](#amazonmacieclassic-aws_SourceArn)   |  | 

## Resource types defined by Amazon Macie Classic<a name="amazonmacieclassic-resources-for-iam-policies"></a>

Amazon Macie Classic does not support specifying a resource ARN in the `Resource` element of an IAM policy statement\. To allow access to Amazon Macie Classic, specify `“Resource”: “*”` in your policy\.

## Condition keys for Amazon Macie Classic<a name="amazonmacieclassic-policy-keys"></a>

Amazon Macie Classic defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   aws:SourceArn  | Allow access to the specified actions only when the request operates on the specified aws resource | Arn | 