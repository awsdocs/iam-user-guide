# Actions, Resources, and Condition Keys for AWS Certificate Manager Private Certificate Authority<a name="list_awscertificatemanagerprivatecertificateauthority"></a>

AWS Certificate Manager Private Certificate Authority \(service prefix: `acm-pca`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/acm-pca/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/acm-pca/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/acm-pca/latest/userguide/assets.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Certificate Manager Private Certificate Authority](#awscertificatemanagerprivatecertificateauthority-actions-as-permissions)
+ [Resources Defined by Certificate Manager Private Certificate Authority](#awscertificatemanagerprivatecertificateauthority-resources-for-iam-policies)
+ [Condition Keys for AWS Certificate Manager Private Certificate Authority](#awscertificatemanagerprivatecertificateauthority-policy-keys)

## Actions Defined by AWS Certificate Manager Private Certificate Authority<a name="awscertificatemanagerprivatecertificateauthority-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_CreateCertificateAuthority.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_CreateCertificateAuthority.html) | Creates an ACM Private CA and its associated private key and configuration\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_CreateCertificateAuthorityAuditReport.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_CreateCertificateAuthorityAuditReport.html) | Creates an audit report for an ACM Private CA\. | Write | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_DeleteCertificateAuthority.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_DeleteCertificateAuthority.html) | Deletes an ACM Private CA and its associated private key and configuration\. | Write | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_DescribeCertificateAuthority.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_DescribeCertificateAuthority.html) | Returns a list of the configuration and status fields contained in the specified ACM Private CA\. | Read | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_DescribeCertificateAuthorityAuditReport.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_DescribeCertificateAuthorityAuditReport.html) | Returns the status and information about an ACM Private CA audit report\. | Read | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_GetCertificate.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_GetCertificate.html) | Retrieves an ACM Private CA certificate and certificate chain for the certificate authority specified by an ARN\. | Read | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_GetCertificateAuthorityCertificate.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_GetCertificateAuthorityCertificate.html) | Retrieves an ACM Private CA certificate and certificate chain for the certificate authority specified by an ARN\. | Read | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_GetCertificateAuthorityCsr.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_GetCertificateAuthorityCsr.html) | Retrieves an ACM Private CA certificate signing request \(CSR\) for the certificate\-authority specified by an ARN\. | Read | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_ImportCertificateAuthorityCertificate.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_ImportCertificateAuthorityCertificate.html) | Imports an SSL/TLS certificate into ACM Private CA for use as the CA certificate of an ACM Private CA\. | Write | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_IssueCertificate.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_IssueCertificate.html) | Issues an ACM Private CA certificate\. | Write | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_ListCertificateAuthorities.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_ListCertificateAuthorities.html) | Retrieves a list of the ACM Private CA certificate authority ARNs, and a summary of the status of each CA in the calling account\. | List |  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_ListTags.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_ListTags.html) | Lists the tags that have been applied to the ACM Private CA certificate authority\. | Read | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_RevokeCertificate.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_RevokeCertificate.html) | Revokes a certificate issued by an ACM Private CA\. | Write | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_TagCertificateAuthority.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_TagCertificateAuthority.html) | Adds one or more tags to an ACM Private CA\. | Tagging | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_UntagCertificateAuthority.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_UntagCertificateAuthority.html) | Remove one or more tags from an ACM Private CA\. | Tagging | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 
| [http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_UpdateCertificateAuthority.html](http://docs.aws.amazon.com/acm-pca/latest/APIReference/API_UpdateCertificateAuthority.html) | Updates the configuration of an ACM Private CA\. | Write | [certificate\-authority\*](#awscertificatemanagerprivatecertificateauthority-certificate-authority)  |  |  | 

## Resources Defined by Certificate Manager Private Certificate Authority<a name="awscertificatemanagerprivatecertificateauthority-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscertificatemanagerprivatecertificateauthority-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/acm-pca/latest/userguide/authen-overview.html#acm-pca-resources-operations](http://docs.aws.amazon.com/acm-pca/latest/userguide/authen-overview.html#acm-pca-resources-operations) | arn:$\{Partition\}:acm\-pca:$\{Region\}:$\{Account\}:certificate\-authority/$\{CertificateAuthorityId\} |  | 

## Condition Keys for AWS Certificate Manager Private Certificate Authority<a name="awscertificatemanagerprivatecertificateauthority-policy-keys"></a>

Certificate Manager Private Certificate Authority has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.