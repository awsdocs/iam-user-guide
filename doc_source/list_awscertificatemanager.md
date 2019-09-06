# Actions, Resources, and Condition Keys for AWS Certificate Manager<a name="list_awscertificatemanager"></a>

AWS Certificate Manager \(service prefix: `acm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/acm/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/acm/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/acm/latest/userguide/assets.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Certificate Manager](#awscertificatemanager-actions-as-permissions)
+ [Resources Defined by AWS Certificate Manager](#awscertificatemanager-resources-for-iam-policies)
+ [Condition Keys for AWS Certificate Manager](#awscertificatemanager-policy-keys)

## Actions Defined by AWS Certificate Manager<a name="awscertificatemanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AddTagsToCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_AddTagsToCertificate.html)  | Adds one or more tags to a certificate\. | Tagging |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ DeleteCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_DeleteCertificate.html)  | Deletes a certificate and its associated private key\. | Write |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ DescribeCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_DescribeCertificate.html)  | Returns a list of the fields contained in the specified certificate\. | Read |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ ExportCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_ExportCertificate.html)  | Exports a private certificate issued by a private certificate authority \(CA\) for use anywhere\. | Read |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ GetCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_GetCertificate.html)  | Retrieves a certificate and certificate chain for the certificate specified by an ARN\. | Read |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ ImportCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_ImportCertificate.html)  | Imports a 3rd party SSL/TLS certificate into AWS Certificate Manager \(ACM\)\. | Write |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ ListCertificates ](https://docs.aws.amazon.com/acm/latest/APIReference/API_ListCertificates.html)  | Retrieves a list of the certificate ARNs and the domain name for each ARN\. | List |  |  |  | 
|   [ ListTagsForCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_ListTagsForCertificate.html)  | Lists the tags that have been applied to the certificate\. | Read |  |  |  | 
|   [ RemoveTagsFromCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_RemoveTagsFromCertificate.html)  | Remove one or more tags from a certificate\. A tag consists of a key\-value pair | Tagging |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ RenewCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_RenewCertificate.html)  | Renews an eligable private certificate\. | Write |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ RequestCertificate ](https://docs.aws.amazon.com/acm/latest/APIReference/API_RequestCertificate.html)  | Requests a public or private certificate\. | Write |  |  |  | 
|   [ ResendValidationEmail ](https://docs.aws.amazon.com/acm/latest/APIReference/API_ResendValidationEmail.html)  | Resends an email to request domain ownership validation\. | Write |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 
|   [ UpdateCertificateOptions ](https://docs.aws.amazon.com/acm/latest/APIReference/API_UpdateCertificateOptions.html)  | Updates a certificate\. Use to specify whether to opt in to or out of certificate transparency logging\. | Write |   [ certificate\* ](#awscertificatemanager-certificate)   |  |  | 

## Resources Defined by AWS Certificate Manager<a name="awscertificatemanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscertificatemanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ certificate ](https://docs.aws.amazon.com/acm/latest/userguide/authen-overview.html#acm-resources-operations)  |  arn:$\{Partition\}:acm:$\{Region\}:$\{Account\}:certificate/$\{CertificateId\}  |  | 

## Condition Keys for AWS Certificate Manager<a name="awscertificatemanager-policy-keys"></a>

Certificate Manager has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.