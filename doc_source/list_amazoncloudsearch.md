# Actions, Resources, and Condition Keys for Amazon CloudSearch<a name="list_amazoncloudsearch"></a>

Amazon CloudSearch \(service prefix: `cloudsearch`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon CloudSearch](#amazoncloudsearch-actions-as-permissions)
+ [Resources Defined by CloudSearch](#amazoncloudsearch-resources-for-iam-policies)
+ [Condition Keys for Amazon CloudSearch](#amazoncloudsearch-policy-keys)

## Actions Defined by Amazon CloudSearch<a name="amazoncloudsearch-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_AddTags.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_AddTags.html) | Attaches resource tags to an Amazon CloudSearch domain\. | Tagging | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_BuildSuggesters.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_BuildSuggesters.html) | Indexes the search suggestions\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_CreateDomain.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_CreateDomain.html) | Creates a new search domain\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineAnalysisScheme.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineAnalysisScheme.html) | Configures an analysis scheme that can be applied to a text or text\-array field to define language\-specific text processing options\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineExpression.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineExpression.html) | Configures an Expression for the search domain\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineIndexField.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineIndexField.html) | Configures an IndexField for the search domain\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineSuggester.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineSuggester.html) | Configures a suggester for a domain\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteAnalysisScheme.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteAnalysisScheme.html) | Deletes an analysis scheme\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteDomain.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteDomain.html) | Permanently deletes a search domain and all of its data\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteExpression.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteExpression.html) | Removes an Expression from the search domain\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteIndexField.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteIndexField.html) | Removes an IndexField from the search domain\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteSuggester.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteSuggester.html) | Deletes a suggester\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeAnalysisSchemes.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeAnalysisSchemes.html) | Gets the analysis schemes configured for a domain\. | Read | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeAvailabilityOptions.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeAvailabilityOptions.html) | Gets the availability options configured for a domain\. | Read | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeDomains.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeDomains.html) | Gets information about the search domains owned by this account\. | List | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeExpressions.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeExpressions.html) | Gets the expressions configured for the search domain\. | Read | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeIndexFields.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeIndexFields.html) | Gets information about the index fields configured for the search domain\. | Read | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeScalingParameters.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeScalingParameters.html) | Gets the scaling parameters configured for a domain\. | Read | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeServiceAccessPolicies.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeServiceAccessPolicies.html) | Gets information about the access policies that control access to the domain's document and search endpoints\. | Read | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeSuggesters.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeSuggesters.html) | Gets the suggesters configured for a domain\. | Read | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_IndexDocuments.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_IndexDocuments.html) | Tells the search domain to start indexing its documents using the latest indexing options\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_ListDomainNames.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_ListDomainNames.html) | Lists all search domains owned by an account\. | List | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_ListTags.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_ListTags.html) | Displays all of the resource tags for an Amazon CloudSearch domain\. | Read | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_RemoveTags.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_RemoveTags.html) | Removes the specified resource tags from an Amazon ES domain\. | Tagging | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateAvailabilityOptions.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateAvailabilityOptions.html) | Configures the availability options for a domain\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateScalingParameters.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateScalingParameters.html) | Configures scaling parameters for a domain\. | Write | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateServiceAccessPolicies.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateServiceAccessPolicies.html) | Configures the access rules that control access to the domain's document and search endpoints\. | Permissions management | [domain\*](#amazoncloudsearch-domain)  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions) \[permission only\] | Allows access to the document service operations\.  | Write |  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions) \[permission only\] | Allows access to the search operations\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions) \[permission only\] | Allows access to the suggest operations\. | Read |  |  |  | 

## Resources Defined by CloudSearch<a name="amazoncloudsearch-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncloudsearch-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.

For information about using Amazon CloudSearch resource ARNs in an IAM policy, see [Amazon CloudSearch ARNs](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-arns) in the *Amazon CloudSearch Developer Guide*\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/cloudsearch/latest/developerguide/creating-domains.html](http://docs.aws.amazon.com/cloudsearch/latest/developerguide/creating-domains.html) | arn:$\{Partition\}:cloudsearch:$\{Region\}:$\{Account\}:domain/$\{DomainName\} |  | 

## Condition Keys for Amazon CloudSearch<a name="amazoncloudsearch-policy-keys"></a>

CloudSearch has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.