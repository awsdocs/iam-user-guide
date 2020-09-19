# Actions, resources, and condition keys for Amazon CloudSearch<a name="list_amazoncloudsearch"></a>

Amazon CloudSearch \(service prefix: `cloudsearch`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/access_permissions.html) permission policies\.

**Topics**
+ [Actions defined by Amazon CloudSearch](#amazoncloudsearch-actions-as-permissions)
+ [Resource types defined by Amazon CloudSearch](#amazoncloudsearch-resources-for-iam-policies)
+ [Condition keys for Amazon CloudSearch](#amazoncloudsearch-policy-keys)

## Actions defined by Amazon CloudSearch<a name="amazoncloudsearch-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddTags ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_AddTags.html)  | Attaches resource tags to an Amazon CloudSearch domain\. | Tagging |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ BuildSuggesters ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_BuildSuggesters.html)  | Indexes the search suggestions\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ CreateDomain ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_CreateDomain.html)  | Creates a new search domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DefineAnalysisScheme ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineAnalysisScheme.html)  | Configures an analysis scheme that can be applied to a text or text\-array field to define language\-specific text processing options\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DefineExpression ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineExpression.html)  | Configures an Expression for the search domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DefineIndexField ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineIndexField.html)  | Configures an IndexField for the search domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DefineSuggester ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DefineSuggester.html)  | Configures a suggester for a domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DeleteAnalysisScheme ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteAnalysisScheme.html)  | Deletes an analysis scheme\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DeleteDomain ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteDomain.html)  | Permanently deletes a search domain and all of its data\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DeleteExpression ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteExpression.html)  | Removes an Expression from the search domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DeleteIndexField ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteIndexField.html)  | Removes an IndexField from the search domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DeleteSuggester ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DeleteSuggester.html)  | Deletes a suggester\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeAnalysisSchemes ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeAnalysisSchemes.html)  | Gets the analysis schemes configured for a domain\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeAvailabilityOptions ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeAvailabilityOptions.html)  | Gets the availability options configured for a domain\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeDomainEndpointOptions ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeDomainEndpointOptions.html)  | Gets the domain endpoint options configured for a domain\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeDomains ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeDomains.html)  | Gets information about the search domains owned by this account\. | List |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeExpressions ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeExpressions.html)  | Gets the expressions configured for the search domain\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeIndexFields ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeIndexFields.html)  | Gets information about the index fields configured for the search domain\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeScalingParameters ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeScalingParameters.html)  | Gets the scaling parameters configured for a domain\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeServiceAccessPolicies ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeServiceAccessPolicies.html)  | Gets information about the access policies that control access to the domain's document and search endpoints\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ DescribeSuggesters ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_DescribeSuggesters.html)  | Gets the suggesters configured for a domain\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ IndexDocuments ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_IndexDocuments.html)  | Tells the search domain to start indexing its documents using the latest indexing options\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ ListDomainNames ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_ListDomainNames.html)  | Lists all search domains owned by an account\. | List |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ ListTags ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_ListTags.html)  | Displays all of the resource tags for an Amazon CloudSearch domain\. | Read |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ RemoveTags ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_RemoveTags.html)  | Removes the specified resource tags from an Amazon ES domain\. | Tagging |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ UpdateAvailabilityOptions ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateAvailabilityOptions.html)  | Configures the availability options for a domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ UpdateDomainEndpointOptions ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateDomainEndpointOptions.html)  | Configures the domain endpoint options for a domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ UpdateScalingParameters ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateScalingParameters.html)  | Configures scaling parameters for a domain\. | Write |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ UpdateServiceAccessPolicies ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/API_UpdateServiceAccessPolicies.html)  | Configures the access rules that control access to the domain's document and search endpoints\. | Permissions management |   [ domain\* ](#amazoncloudsearch-domain)   |  |  | 
|   [ document ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions) \[permission only\] | Allows access to the document service operations\.  | Write |   [ domain ](#amazoncloudsearch-domain)   |  |  | 
|   [ search ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions) \[permission only\] | Allows access to the search operations\. | Read |   [ domain ](#amazoncloudsearch-domain)   |  |  | 
|   [ suggest ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-actions) \[permission only\] | Allows access to the suggest operations\. | Read |   [ domain ](#amazoncloudsearch-domain)   |  |  | 

## Resource types defined by Amazon CloudSearch<a name="amazoncloudsearch-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazoncloudsearch-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.

**Note**  
For information about using Amazon CloudSearch resource ARNs in an IAM policy, see [Amazon CloudSearch ARNs](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/configuring-access.html#cloudsearch-arns) in the *Amazon CloudSearch Developer Guide*\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ domain ](https://docs.aws.amazon.com/cloudsearch/latest/developerguide/creating-domains.html)  |  arn:$\{Partition\}:cloudsearch:$\{Region\}:$\{Account\}:domain/$\{DomainName\}  |  | 

## Condition keys for Amazon CloudSearch<a name="amazoncloudsearch-policy-keys"></a>

CloudSearch has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.