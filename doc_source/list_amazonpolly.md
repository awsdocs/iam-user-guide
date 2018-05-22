# Actions, Resources, and Condition Keys for Amazon Polly<a name="list_amazonpolly"></a>

Amazon Polly \(service prefix: `polly`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/polly/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/polly/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/polly/latest/dg/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Polly](#amazonpolly-actions-as-permissions)
+ [Resources Defined by Polly](#amazonpolly-resources-for-iam-policies)
+ [Condition Keys for Amazon Polly](#amazonpolly-policy-keys)

## Actions Defined by Amazon Polly<a name="amazonpolly-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/polly/latest/dg/API_DeleteLexicon.html](http://docs.aws.amazon.com/polly/latest/dg/API_DeleteLexicon.html) | Deletes the specified pronunciation lexicon stored in an AWS Region | Write | [lexicon\*](#amazonpolly-lexicon)  |  |  | 
| [http://docs.aws.amazon.com/polly/latest/dg/API_DescribeVoices.html](http://docs.aws.amazon.com/polly/latest/dg/API_DescribeVoices.html) | Returns the list of voices that are available for use when requesting speech synthesis\. | List |  |  |  | 
| [http://docs.aws.amazon.com/polly/latest/dg/API_GetLexicon.html](http://docs.aws.amazon.com/polly/latest/dg/API_GetLexicon.html) | Returns the content of the specified pronunciation lexicon stored in an AWS Region\. | Read | [lexicon\*](#amazonpolly-lexicon)  |  |  | 
| [http://docs.aws.amazon.com/polly/latest/dg/API_ListLexicons.html](http://docs.aws.amazon.com/polly/latest/dg/API_ListLexicons.html) | Returns a list of pronunciation lexicons stored in an AWS Region\. | List |  |  |  | 
| [http://docs.aws.amazon.com/polly/latest/dg/API_PutLexicon.html](http://docs.aws.amazon.com/polly/latest/dg/API_PutLexicon.html) | Stores a pronunciation lexicon in an AWS Region\. | Write | [lexicon\*](#amazonpolly-lexicon)  |  |  | 
| [http://docs.aws.amazon.com/polly/latest/dg/API_SynthesizeSpeech.html](http://docs.aws.amazon.com/polly/latest/dg/API_SynthesizeSpeech.html) | Synthesizes UTF\-8 input, plain text or SSML, to a stream of bytes\. | Read | [lexicon](#amazonpolly-lexicon)  |  |  | 

## Resources Defined by Polly<a name="amazonpolly-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonpolly-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/polly/latest/dg/managing-lexicons.html](http://docs.aws.amazon.com/polly/latest/dg/managing-lexicons.html) | arn:$\{Partition\}:polly:$\{Region\}:$\{Account\}:lexicon/$\{LexiconName\} |  | 

## Condition Keys for Amazon Polly<a name="amazonpolly-policy-keys"></a>

Polly has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.