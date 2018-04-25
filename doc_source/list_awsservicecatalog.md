# Actions, Resources, and Condition Keys for AWS Service Catalog<a name="list_awsservicecatalog"></a>

AWS Service Catalog \(service prefix: `servicecatalog`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/servicecatalog/latest/adminguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/servicecatalog/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Service Catalog](#awsservicecatalog-actions-as-permissions)
+ [Resources Defined by Service Catalog](#awsservicecatalog-resources-for-iam-policies)
+ [Condition Keys for AWS Service Catalog](#awsservicecatalog-policy-keys)

## Actions Defined by AWS Service Catalog<a name="awsservicecatalog-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [AcceptPortfolioShare](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_AcceptPortfolioShare.html) | Accepts a portfolio that has been shared with you |   |  |  |  | 
| [AssociatePrincipalWithPortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociatePrincipalWithPortfolio.html) | Associates an IAM principal with a portfolio, giving the specified principal access to any products associated with the specified portfolio |   |  |  |  | 
| [AssociateProductWithPortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociateProductWithPortfolio.html) | Associates a product with a portfolio |   |  |  |  | 
| [CreateConstraint](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateConstraint.html) | Creates a constraint on an associated product and portfolio |   |  |  |  | 
| [CreatePortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreatePortfolio.html) | Creates a portfolio |   |  |  |  | 
| [CreatePortfolioShare](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreatePortfolioShare.html) | Shares a portfolio you own with another AWS account |   |  |  |  | 
| [CreateProduct](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateProduct.html) | Creates a product and that product's first provisioning artifact |   |  |  |  | 
| [CreateProvisioningArtifact](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateProvisioningArtifact.html) | Adds a new provisioning artifact to an existing product |   |  |  |  | 
| [DeleteConstraint](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteConstraint.html) | Removes and deletes an existing constraint from an associated product and portfolio |   |  |  |  | 
| [DeletePortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeletePortfolio.html) | Deletes a portfolio if all associations and shares have been removed from the portfolio |   |  |  |  | 
| [DeletePortfolioShare](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeletePortfolioShare.html) | Unshares a portfolio you own from an AWS account you previously shared the portfolio with |   |  |  |  | 
| [DeleteProduct](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteProduct.html) | Deletes a product if all associations have been removed from the product |   |  |  |  | 
| [DeleteProvisioningArtifact](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteProvisioningArtifact.html) | Deletes a provisioning artifact from a product |   |  |  |  | 
| [DescribeConstraint](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeConstraint.html) | Describes a constraint |   |  |  |  | 
| [DescribePortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribePortfolio.html) | Describes a portfolio |   |  |  |  | 
| [DescribeProduct](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProduct.html) | Describes a product as an end\-user |   |  |  |  | 
| [DescribeProductAsAdmin](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProductAsAdmin.html) | Describes a product as an admin |   |  |  |  | 
| [DescribeProductView](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProductView.html) | Describes a product as an end\-user |   |  |  |  | 
| [DescribeProvisioningArtifact](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProvisioningArtifact.html) | Describes a provisioning artifact |   |  |  |  | 
| [DescribeProvisioningParameters](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProvisioningParameters.html) | Describes the parameters that you need to specify to successfully provision a specified provisioning artifact |   |  |  |  | 
| [DescribeRecord](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeRecord.html) | Describes a record and lists any outputs |   |  |  |  | 
| [DisassociatePrincipalFromPortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociatePrincipalFromPortfolio.html) | Disassociates an IAM principal from a portfolio |   |  |  |  | 
| [DisassociateProductFromPortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociateProductFromPortfolio.html) | Disassociates a product from a portfolio |   |  |  |  | 
| [ListAcceptedPortfolioShares](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListAcceptedPortfolioShares.html) | Lists the portfolios that have been shared with you and you have accepted |   |  |  |  | 
| [ListConstraintsForPortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListConstraintsForPortfolio.html) | Lists constraints associated with a given portfolio |   |  |  |  | 
| [ListLaunchPaths](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListLaunchPaths.html) | Lists the different ways to launch a given product as an end\-user |   |  |  |  | 
| [ListPortfolioAccess](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfolioAccess.html) | Lists the AWS accounts you have shared a given portfolio with |   |  |  |  | 
| [ListPortfolios](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfolios.html) | Lists the portfolios in your account |   |  |  |  | 
| [ListPortfoliosForProduct](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfoliosForProduct.html) | Lists the portfolios associated with a given product |   |  |  |  | 
| [ListPrincipalsForPortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPrincipalsForPortfolio.html) | Lists the IAM principals associated with a given portfolio |   |  |  |  | 
| [ListProvisioningArtifacts](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListProvisioningArtifacts.html) | Lists the provisioning artifacts associated with a given product |   |  |  |  | 
| [ListRecordHistory](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListRecordHistory.html) | Lists all the records in your account or all the records related to a given provisioned product |   |  |  |  | 
| [ProvisionProduct](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ProvisionProduct.html) | Provisions a product with a specified provisioning artifact and launch parameters |   |  |  |  | 
| [RejectPortfolioShare](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_RejectPortfolioShare.html) | Rejects a portfolio that has been shared with you that you previously accepted |   |  |  |  | 
| [ScanProvisionedProducts](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_ScanProvisionedProducts.html) | Lists all the provisioned products in your account |   |  |  |  | 
| [SearchProducts](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_SearchProducts.html) | Lists the products available to you as an end\-user |   |  |  |  | 
| [SearchProductsAsAdmin](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_SearchProductsAsAdmin.html) | Lists all the products in your account or all the products associated with a given portfolio |   |  |  |  | 
| [TerminateProvisionedProduct](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_TerminateProvisionedProduct.html) | Terminates an existing provisioned product |   |  |  |  | 
| [UpdateConstraint](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateConstraint.html) | Updates the metadata fields of an existing constraint |   |  |  |  | 
| [UpdatePortfolio](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdatePortfolio.html) | Updates the metadata fields and/or tags of an existing portfolio |   |  |  |  | 
| [UpdateProduct](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProduct.html) | Updates the metadata fields and/or tags of an existing product |   |  |  |  | 
| [UpdateProvisionedProduct](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProvisionedProduct.html) | Updates an existing provisioned product |   |  |  |  | 
| [UpdateProvisioningArtifact](http://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProvisioningArtifact.html) | Updates the metadata fields of an existing provisioning artifact |   |  |  |  | 

## Resources Defined by Service Catalog<a name="awsservicecatalog-resources-for-iam-policies"></a>

Service Catalog has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Service Catalog<a name="awsservicecatalog-policy-keys"></a>

AWS Service Catalog defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAMPolicy Reference*\.

For example policies that show how these condition keys can be used in an IAM policy, see [Example Access Policies for Provisioned Product Management](http://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions-examples.html) in the *AWS Service Catalog Administrator Guide*\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
| [servicecatalog:accountLevel](http://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions-examples.html) | Allows users to see and perform actions on resources created by anyone in the account\. | String | 
| [servicecatalog:roleLevel](http://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions-examples.html) | Allows users to see and perform actions on resources created either by them or by anyone federating into the same role as them\. | String | 
| [servicecatalog:userLevel](http://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions-examples.html) | Allows users to see and perform actions on only resources that they created\. | String | 