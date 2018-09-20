# Actions, Resources, and Condition Keys for AWS Service Catalog<a name="list_awsservicecatalog"></a>

AWS Service Catalog \(service prefix: `servicecatalog`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/servicecatalog/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Service Catalog](#awsservicecatalog-actions-as-permissions)
+ [Resources Defined by Service Catalog](#awsservicecatalog-resources-for-iam-policies)
+ [Condition Keys for AWS Service Catalog](#awsservicecatalog-policy-keys)

## Actions Defined by AWS Service Catalog<a name="awsservicecatalog-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AcceptPortfolioShare ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AcceptPortfolioShare.html)  | Accepts a portfolio that has been shared with you | Write |  |  |  | 
|   [ AssociatePrincipalWithPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociatePrincipalWithPortfolio.html)  | Associates an IAM principal with a portfolio, giving the specified principal access to any products associated with the specified portfolio | Write |  |  |  | 
|   [ AssociateProductWithPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociateProductWithPortfolio.html)  | Associates a product with a portfolio | Write |  |  |  | 
|   [ CreateConstraint ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateConstraint.html)  | Creates a constraint on an associated product and portfolio | Write |  |  |  | 
|   [ CreatePortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreatePortfolio.html)  | Creates a portfolio | Tagging |  |  |  | 
|   [ CreatePortfolioShare ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreatePortfolioShare.html)  | Shares a portfolio you own with another AWS account | Permissions management |  |  |  | 
|   [ CreateProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateProduct.html)  | Creates a product and that product's first provisioning artifact | Tagging |  |  |  | 
|   [ CreateProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateProvisioningArtifact.html)  | Adds a new provisioning artifact to an existing product | Write |  |  |  | 
|   [ DeleteConstraint ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteConstraint.html)  | Removes and deletes an existing constraint from an associated product and portfolio | Write |  |  |  | 
|   [ DeletePortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeletePortfolio.html)  | Deletes a portfolio if all associations and shares have been removed from the portfolio | Write |  |  |  | 
|   [ DeletePortfolioShare ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeletePortfolioShare.html)  | Unshares a portfolio you own from an AWS account you previously shared the portfolio with | Permissions management |  |  |  | 
|   [ DeleteProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteProduct.html)  | Deletes a product if all associations have been removed from the product | Write |  |  |  | 
|   [ DeleteProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteProvisioningArtifact.html)  | Deletes a provisioning artifact from a product | Write |  |  |  | 
|   [ DescribeConstraint ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeConstraint.html)  | Describes a constraint | Read |  |  |  | 
|   [ DescribePortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribePortfolio.html)  | Describes a portfolio | Read |  |  |  | 
|   [ DescribeProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProduct.html)  | Describes a product as an end\-user | Read |  |  |  | 
|   [ DescribeProductAsAdmin ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProductAsAdmin.html)  | Describes a product as an admin | Read |  |  |  | 
|   [ DescribeProductView ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProductView.html)  | Describes a product as an end\-user | Read |  |  |  | 
|   [ DescribeProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProvisioningArtifact.html)  | Describes a provisioning artifact | Read |  |  |  | 
|   [ DescribeProvisioningParameters ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProvisioningParameters.html)  | Describes the parameters that you need to specify to successfully provision a specified provisioning artifact | Read |  |  |  | 
|   [ DescribeRecord ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeRecord.html)  | Describes a record and lists any outputs | Read |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ DisassociatePrincipalFromPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociatePrincipalFromPortfolio.html)  | Disassociates an IAM principal from a portfolio | Write |  |  |  | 
|   [ DisassociateProductFromPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociateProductFromPortfolio.html)  | Disassociates a product from a portfolio | Write |  |  |  | 
|   [ ListAcceptedPortfolioShares ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListAcceptedPortfolioShares.html)  | Lists the portfolios that have been shared with you and you have accepted | List |  |  |  | 
|   [ ListConstraintsForPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListConstraintsForPortfolio.html)  | Lists constraints associated with a given portfolio | List |  |  |  | 
|   [ ListLaunchPaths ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListLaunchPaths.html)  | Lists the different ways to launch a given product as an end\-user | List |  |  |  | 
|   [ ListPortfolioAccess ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfolioAccess.html)  | Lists the AWS accounts you have shared a given portfolio with | List |  |  |  | 
|   [ ListPortfolios ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfolios.html)  | Lists the portfolios in your account | List |  |  |  | 
|   [ ListPortfoliosForProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfoliosForProduct.html)  | Lists the portfolios associated with a given product | List |  |  |  | 
|   [ ListPrincipalsForPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPrincipalsForPortfolio.html)  | Lists the IAM principals associated with a given portfolio | List |  |  |  | 
|   [ ListProvisioningArtifacts ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListProvisioningArtifacts.html)  | Lists the provisioning artifacts associated with a given product | List |  |  |  | 
|   [ ListRecordHistory ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListRecordHistory.html)  | Lists all the records in your account or all the records related to a given provisioned product | List |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ ProvisionProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ProvisionProduct.html)  | Provisions a product with a specified provisioning artifact and launch parameters | Tagging |  |  |  | 
|   [ RejectPortfolioShare ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_RejectPortfolioShare.html)  | Rejects a portfolio that has been shared with you that you previously accepted | Write |  |  |  | 
|   [ ScanProvisionedProducts ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ScanProvisionedProducts.html)  | Lists all the provisioned products in your account | List |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ SearchProducts ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_SearchProducts.html)  | Lists the products available to you as an end\-user | List |  |  |  | 
|   [ SearchProductsAsAdmin ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_SearchProductsAsAdmin.html)  | Lists all the products in your account or all the products associated with a given portfolio | List |  |  |  | 
|   [ TerminateProvisionedProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_TerminateProvisionedProduct.html)  | Terminates an existing provisioned product | Write |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ UpdateConstraint ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateConstraint.html)  | Updates the metadata fields of an existing constraint | Write |  |  |  | 
|   [ UpdatePortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdatePortfolio.html)  | Updates the metadata fields and/or tags of an existing portfolio | Tagging |  |  |  | 
|   [ UpdateProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProduct.html)  | Updates the metadata fields and/or tags of an existing product | Tagging |  |  |  | 
|   [ UpdateProvisionedProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProvisionedProduct.html)  | Updates an existing provisioned product | Write |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ UpdateProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProvisioningArtifact.html)  | Updates the metadata fields of an existing provisioning artifact | Write |  |  |  | 

## Resources Defined by Service Catalog<a name="awsservicecatalog-resources-for-iam-policies"></a>

AWS Service Catalog has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Service Catalog<a name="awsservicecatalog-policy-keys"></a>

AWS Service Catalog defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.

For example policies that show how these condition keys can be used in an IAM policy, see [Example Access Policies for Provisioned Product Management](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions-examples.html) in the *AWS Service Catalog Administrator Guide*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ servicecatalog:accountLevel ](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions-examples.html)  | Allows users to see and perform actions on resources created by anyone in the account\. | String | 
|   [ servicecatalog:roleLevel ](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions-examples.html)  | Allows users to see and perform actions on resources created either by them or by anyone federating into the same role as them\. | String | 
|   [ servicecatalog:userLevel ](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions-examples.html)  | Allows users to see and perform actions on only resources that they created\. | String | 