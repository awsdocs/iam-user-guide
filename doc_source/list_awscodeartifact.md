# Actions, resources, and condition keys for AWS CodeArtifact<a name="list_awscodeartifact"></a>

AWS CodeArtifact \(service prefix: `codeartifact`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/codeartifact/latest/userguide/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/codeartifact/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/codeartifact/latest/userguide/auth-and-access-control.html) permission policies\.

**Topics**
+ [Actions defined by AWS CodeArtifact](#awscodeartifact-actions-as-permissions)
+ [Resource types defined by AWS CodeArtifact](#awscodeartifact-resources-for-iam-policies)
+ [Condition keys for AWS CodeArtifact](#awscodeartifact-policy-keys)

## Actions defined by AWS CodeArtifact<a name="awscodeartifact-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access level | Resource types \(\*required\) | Condition keys | Dependent actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateExternalConnection ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_AssociateExternalConnection.html)  | Grants permission to add an external connection to a repository | Write |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ AssociateWithDownstreamRepository ](https://docs.aws.amazon.com/codeartifact/latest/userguide/repos-upstream.html)  | Grants permission to associate an existing repository as an upstream repository to another repository | Write |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ CopyPackageVersions ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_CopyPackageVersions.html)  | Grants permission to copy package versions from one repository to another repository in the same domain\. | Write |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ CreateDomain ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_CreateDomain.html)  | Grants permission to create a new domain | Write |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ CreateRepository ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_CreateRepository.html)  | Grants permission to create a new repository | Write |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ DeleteDomain ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DeleteDomain.html)  | Grants permission to delete a domain | Write |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ DeleteDomainPermissionsPolicy ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DeleteDomainPermissionsPolicy.html)  | Grants permission to delete the resource policy set on a domain | Permissions management |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ DeletePackageVersions ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DeletePackageVersions.html)  | Grants permission to delete package versions | Write |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ DeleteRepository ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DeleteRepository.html)  | Grants permission to delete a repository | Write |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ DeleteRepositoryPermissionsPolicy ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DeleteRepositoryPermissionsPolicy.html)  | Grants permission to delete the resource policy set on a repository | Permissions management |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ DescribeDomain ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DescribeDomain.html)  | Grants permission to return information about a domain | Read |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ DescribePackageVersion ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DescribePackageVersion.html)  | Grants permission to return information about a package version | Read |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ DescribeRepository ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DescribeRepository.html)  | Grants permission to return detailed information about a repository | Read |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ DisassociateExternalConnection ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DisassociateExternalConnection.html)  | Grants permission to disassociate an external connection from a repository | Write |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ DisposePackageVersions ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_DisposePackageVersions.html)  | Grants permission to set the status of package versions to Disposed and delete their assets | Write |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ GetAuthorizationToken ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_GetAuthorizationToken.html)  | Grants permission to generate a temporary authentication token for accessing repositories in a domain | Read |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ GetDomainPermissionsPolicy ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_GetDomainPermissionsPolicy.html)  | Grants permission to return a domain's resource policy | Read |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ GetPackageVersionAsset ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_GetPackageVersionAsset.html)  | Grants permission to return an asset \(or file\) that is part of a package version | Read |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ GetPackageVersionReadme ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_GetPackageVersionReadme.html)  | Grants permission to return a package version's readme file | Read |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ GetRepositoryEndpoint ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_GetRepositoryEndpoint.html)  | Grants permission to return an endpoint for a repository | Read |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ GetRepositoryPermissionsPolicy ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_GetRepositoryPermissionsPolicy.html)  | Grants permission to return a repository's resource policy | Read |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ ListDomains ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_ListDomains.html)  | Grants permission to list the domains in the current user's AWS account | List |  |  |  | 
|   [ ListPackageVersionAssets ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_ListPackageVersionAssets.html)  | Grants permission to list a package version's assets | List |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ ListPackageVersionDependencies ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_ListPackageVersionDependencies.html)  | Grants permission to list the direct dependencies of a package version | List |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ ListPackageVersions ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_ListPackageVersions.html)  | Grants permission to list a package's versions | List |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ ListPackages ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_ListPackages.html)  | Grants permission to list the packages in a repository | List |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ ListRepositories ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_ListRepositories.html)  | Grants permission to list the repositories administered by the calling account | List |  |  |  | 
|   [ ListRepositoriesInDomain ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_ListRepositoriesInDomain.html)  | Grants permission to list the repositories in a domain | List |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ PublishPackageVersion ](https://docs.aws.amazon.com/codeartifact/latest/userguide/repo-policies.html)  | Grants permission to publish assets and metadata to a repository endpoint | Write |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ PutDomainPermissionsPolicy ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_PutDomainPermissionsPolicy.html)  | Grants permission to attach a resource policy to a domain | Write |   [ domain\* ](#awscodeartifact-domain)   |  |  | 
|   [ PutPackageMetadata ](https://docs.aws.amazon.com/codeartifact/latest/userguide/repo-policies.html)  | Grants permission to add, modify or remove package metadata using a repository endpoint | Write |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ PutRepositoryPermissionsPolicy ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_PutRepositoryPermissionsPolicy.html)  | Grants permission to attach a resource policy to a repository | Write |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ ReadFromRepository ](https://docs.aws.amazon.com/codeartifact/latest/userguide/repo-policies.html)  | Grants permission to return package assets and metadata from a repository endpoint | Read |   [ repository\* ](#awscodeartifact-repository)   |  |  | 
|   [ UpdatePackageVersionsStatus ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_UpdatePackageVersionsStatus.html)  | Grants permission to modify the status of one or more versions of a package | Write |   [ package\* ](#awscodeartifact-package)   |  |  | 
|   [ UpdateRepository ](https://docs.aws.amazon.com/codeartifact/latest/APIReference/API_UpdateRepository.html)  | Grants permission to modify the properties of a repository | Write |   [ repository\* ](#awscodeartifact-repository)   |  |  | 

## Resource types defined by AWS CodeArtifact<a name="awscodeartifact-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awscodeartifact-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ domain ](https://docs.aws.amazon.com/codeartifact/latest/userguide/auth-and-access-control-iam-access-control-identity-based.html#arn-formats)  |  arn:$\{Partition\}:codeartifact:$\{Region\}:$\{Account\}:domain/$\{DomainName\}  |  | 
|   [ repository ](https://docs.aws.amazon.com/codeartifact/latest/userguide/repo-policies.html)  |  arn:$\{Partition\}:codeartifact:$\{Region\}:$\{Account\}:repository/$\{DomainName\}/$\{RepositoryName\}  |  | 
|   [ package ](https://docs.aws.amazon.com/codeartifact/latest/userguide/repo-policies.html)  |  arn:$\{Partition\}:codeartifact:$\{Region\}:$\{Account\}:package/$\{DomainName\}/$\{RepositoryName\}/$\{PackageFormat\}/$\{PackageNamespace\}/$\{PackageName\}  |  | 

## Condition keys for AWS CodeArtifact<a name="awscodeartifact-policy-keys"></a>

CodeArtifact has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available keys for conditions](reference_policies_condition-keys.html#AvailableKeys)\.