# Actions, Resources, and Condition Keys for AWS Certificate Manager<a name="list_awscertificatemanager"></a>

AWS Certificate Manager \(service prefix: `acm`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/acm/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/acm/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/acm/latest/userguide/assets.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Certificate Manager](#awscertificatemanager-actions-as-permissions)
+ [Resources Defined by Certificate Manager](#awscertificatemanager-resources-for-iam-policies)
+ [Condition Keys for AWS Certificate Manager](#awscertificatemanager-policy-keys)

## Actions Defined by AWS Certificate Manager<a name="awscertificatemanager-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_AddTagsToCertificate.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_AddTagsToCertificate.html) | Adds one or more tags to an ACM Certificate\. | Tagging | [certificate\*](#awscertificatemanager-certificate)  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_DeleteCertificate.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_DeleteCertificate.html) |  Deletes an ACM Certificate and its associated private key\. | Permissions management | [certificate\*](#awscertificatemanager-certificate)  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_DescribeCertificate.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_DescribeCertificate.html) | Returns a list of the fields contained in the specified ACM Certificate\. | Read | [certificate\*](#awscertificatemanager-certificate)  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_GetCertificate.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_GetCertificate.html) | Retrieves an ACM Certificate and certificate chain for the certificate specified by an ARN\. | Read | [certificate\*](#awscertificatemanager-certificate)  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_ImportCertificate.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_ImportCertificate.html) | Imports an SSL/TLS certificate into AWS Certificate Manager \(ACM\) to use with ACM's integrated AWS services | Write | [certificate\*](#awscertificatemanager-certificate)  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_ListCertificates.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_ListCertificates.html) | Retrieves a list of the ACM Certificate ARNs, and the domain name for each ARN, owned by the calling account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_ListTagsForCertificate.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_ListTagsForCertificate.html) | Lists the tags that have been applied to the ACM Certificate\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_RemoveTagsFromCertificate.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_RemoveTagsFromCertificate.html) | Remove one or more tags from an ACM Certificate\. A tag consists of a key\-value pair | Tagging | [certificate\*](#awscertificatemanager-certificate)  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_RequestCertificate.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_RequestCertificate.html) | Requests an ACM Certificate for use with other AWS services\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/acm/latest/APIReference/API_ResendValidationEmail.html](http://docs.aws.amazon.com/acm/latest/APIReference/API_ResendValidationEmail.html) | Resends the email that requests domain ownership validation\. | Permissions management | [certificate\*](#awscertificatemanager-certificate)  |  |  | 

## Resources Defined by Certificate Manager<a name="awscertificatemanager-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscertificatemanager-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/acm/latest/userguide/authen-overview.html#acm-resources-operations](http://docs.aws.amazon.com/acm/latest/userguide/authen-overview.html#acm-resources-operations) | arn:$\{Partition\}:acm:$\{Region\}:$\{Account\}:certificate/$\{CertificateId\} |  | 

## Condition Keys for AWS Certificate Manager<a name="awscertificatemanager-policy-keys"></a>

Certificate Manager has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.