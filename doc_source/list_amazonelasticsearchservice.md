# Actions, Resources, and Condition Keys for Amazon Elasticsearch Service<a name="list_amazonelasticsearchservice"></a>

Amazon Elasticsearch Service \(service prefix: `es`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

**Topics**
+ [Actions Defined by Amazon Elasticsearch Service](#amazonelasticsearchservice-actions-as-permissions)
+ [Resources Defined by Elasticsearch Service](#amazonelasticsearchservice-resources-for-iam-policies)
+ [Condition Keys for Amazon Elasticsearch Service](#amazonelasticsearchservice-policy-keys)

## Actions Defined by Amazon Elasticsearch Service<a name="amazonelasticsearchservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-addtags](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-addtags) | Grants permission to attach resource tags to an Amazon ES domain\. | Tagging | [domain\*](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-createelasticsearchdomain](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-createelasticsearchdomain) | Grants permission to create an Amazon ES domain\. | Write | [domain](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-deleteelasticsearchdomain](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-deleteelasticsearchdomain) | Grants permission to delete an Amazon ES domain and all of its data\. | Write | [domain\*](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-deleteelasticsearchservicerole](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-deleteelasticsearchservicerole) | Grants permission to delete the service\-linked role required for Amazon ES domains that use VPC access\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-describeelasticsearchdomain](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-describeelasticsearchdomain) | Grants permission to view a description of the domain configuration for the specified Amazon ES domain, including the domain ID, domain service endpoint, and domain ARN\. | Read | [domain\*](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-describeelasticsearchdomainconfig](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-describeelasticsearchdomainconfig) | Grants permission to view a description of the configuration options and status of an Amazon ES domain\. | Read | [domain\*](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-describeelasticsearchdomain](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-describeelasticsearchdomain) | Grants permission to view a description of the domain configuration for up to five specified Amazon ES domains\. | List | [domain\*](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-describeinstancetypelimits](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-describeinstancetypelimits) | Grants permission to view the instance count, storage, and master node limits for a given Elasticsearch version and instance type\. | List |  |  |  | 
| ESHttpDelete | Grants permission to send HTTP DELETE requests to the Elasticsearch APIs\. | Write | [domain](#amazonelasticsearchservice-domain)  |  |  | 
| ESHttpGet | Grants permission to send HTTP GET requests to the Elasticsearch APIs\. | Read | [domain](#amazonelasticsearchservice-domain)  |  |  | 
| ESHttpHead | Grants permission to send HTTP HEAD requests to the Elasticsearch APIs\. | Read | [domain](#amazonelasticsearchservice-domain)  |  |  | 
| ESHttpPost | Grants permission to send HTTP POST requests to the Elasticsearch APIs\. | Write | [domain](#amazonelasticsearchservice-domain)  |  |  | 
| ESHttpPut | Grants permission to send HTTP PUT requests to the Elasticsearch APIs\. | Write | [domain](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listdomainnames](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listdomainnames) | Grants permission to display the names of all Amazon ES domains that the current user owns\. | List |  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listelasticsearchinstancetypes](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listelasticsearchinstancetypes) | Grants permission to list all Elasticsearch instance types that are supported for a given Elasticsearch version\. | List |  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listelasticsearchversions](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listelasticsearchversions) | Grants permission to list all supported Elasticsearch versions on Amazon ES\. | List |  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listtags](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listtags) | Grants permission to display all of the tags for an Amazon ES domain\. | Read | [domain\*](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listtags](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-listtags) | Grants permission to remove tags from Amazon ES domains\. | Tagging | [domain\*](#amazonelasticsearchservice-domain)  |  |  | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-updateelasticsearchdomainconfig](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-configuration-api.html#es-configuration-api-actions-updateelasticsearchdomainconfig) | Grants permission to modify the configuration of an Amazon ES domain, such as the instance type or number of instances\. | Write | [domain\*](#amazonelasticsearchservice-domain)  |  |  | 

## Resources Defined by Elasticsearch Service<a name="amazonelasticsearchservice-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonelasticsearchservice-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-gsg.html](http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-gsg.html) | arn:$\{Partition\}:es:$\{Region\}:$\{Account\}:domain/$\{DomainName\} |  | 

## Condition Keys for Amazon Elasticsearch Service<a name="amazonelasticsearchservice-policy-keys"></a>

Elasticsearch Service has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.