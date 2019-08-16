# Actions, Resources, and Condition Keys for AWS Service Catalog<a name="list_awsservicecatalog"></a>

AWS Service Catalog \(service prefix: `servicecatalog`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/servicecatalog/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/servicecatalog/latest/adminguide/permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Service Catalog](#awsservicecatalog-actions-as-permissions)
+ [Resources Defined by AWS Service Catalog](#awsservicecatalog-resources-for-iam-policies)
+ [Condition Keys for AWS Service Catalog](#awsservicecatalog-policy-keys)

## Actions Defined by AWS Service Catalog<a name="awsservicecatalog-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AcceptPortfolioShare ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AcceptPortfolioShare.html)  | Accepts a portfolio that has been shared with you | Write |  |  |  | 
|   [ AssociateBudgetWithResource ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociateBudgetWithResource.html)  | Associates a budget with a resource\. | Write |  |  |  | 
|   [ AssociatePrincipalWithPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociatePrincipalWithPortfolio.html)  | Associates an IAM principal with a portfolio, giving the specified principal access to any products associated with the specified portfolio | Write |  |  |  | 
|   [ AssociateProductWithPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociateProductWithPortfolio.html)  | Associates a product with a portfolio | Write |  |  |  | 
|   [ AssociateServiceActionWithProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociateServiceActionWithProvisioningArtifact.html)  | Associates an action with a provisioning artifact | Write |  |  |  | 
|   [ AssociateTagOptionWithResource ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_AssociateTagOptionWithResource.html)  | Associate the specified TagOption with the specified portfolio or product | Write |  |  |  | 
|   [ BatchAssociateServiceActionWithProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_BatchAssociateServiceActionWithProvisioningArtifact.html)  | Associates multiple self\-service actions with provisioning artifacts\. | Write |  |  |  | 
|   [ BatchDisassociateServiceActionFromProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_BatchDisassociateServiceActionFromProvisioningArtifact.html)  | Disassociates a batch of self\-service actions from the specified provisioning artifact\. | Write |  |  |  | 
|   [ CopyProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CopyProduct.html)  | Copies the specified source product to the specified target product or a new product\. | Write |  |  |  | 
|   [ CreateConstraint ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateConstraint.html)  | Creates a constraint on an associated product and portfolio | Write |  |  |  | 
|   [ CreatePortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreatePortfolio.html)  | Creates a portfolio | Write |  |  |  | 
|   [ CreatePortfolioShare ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreatePortfolioShare.html)  | Shares a portfolio you own with another AWS account | Permissions management |  |  |  | 
|   [ CreateProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateProduct.html)  | Creates a product and that product's first provisioning artifact | Write |  |  |  | 
|   [ CreateProvisionedProductPlan ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateProvisionedProductPlan.html)  | Adds a new provisioned product plan | Write |  |  |  | 
|   [ CreateProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateProvisioningArtifact.html)  | Adds a new provisioning artifact to an existing product | Write |  |  |  | 
|   [ CreateServiceAction ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateServiceAction.html)  | Creates a self\-service action\. | Write |  |  |  | 
|   [ CreateTagOption ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_CreateTagOption.html)  | Creates a TagOption\. | Write |  |  |  | 
|   [ DeleteConstraint ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteConstraint.html)  | Removes and deletes an existing constraint from an associated product and portfolio | Write |  |  |  | 
|   [ DeletePortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeletePortfolio.html)  | Deletes a portfolio if all associations and shares have been removed from the portfolio | Write |  |  |  | 
|   [ DeletePortfolioShare ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeletePortfolioShare.html)  | Unshares a portfolio you own from an AWS account you previously shared the portfolio with | Permissions management |  |  |  | 
|   [ DeleteProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteProduct.html)  | Deletes a product if all associations have been removed from the product | Write |  |  |  | 
|   [ DeleteProvisionedProductPlan ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteProvisionedProductPlan.html)  | Deletes a provisioned product plan | Write |  |  |  | 
|   [ DeleteProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteProvisioningArtifact.html)  | Deletes a provisioning artifact from a product | Write |  |  |  | 
|   [ DeleteServiceAction ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteServiceAction.html)  | Deletes a self\-service action\. | Write |  |  |  | 
|   [ DeleteTagOption ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DeleteTagOption.html)  | Deletes the specified TagOption\. | Write |  |  |  | 
|   [ DescribeConstraint ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeConstraint.html)  | Describes a constraint | Read |  |  |  | 
|   [ DescribeCopyProductStatus ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeCopyProductStatus.html)  | Gets the status of the specified copy product operation\. | Read |  |  |  | 
|   [ DescribePortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribePortfolio.html)  | Describes a portfolio | Read |  |  |  | 
|   [ DescribePortfolioShareStatus ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribePortfolioShareStatus.html)  | Gets the status of the specified portfolio share operation\. | Read |  |  |  | 
|   [ DescribeProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProduct.html)  | Describes a product as an end\-user | Read |  |  |  | 
|   [ DescribeProductAsAdmin ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProductAsAdmin.html)  | Describes a product as an admin | Read |  |  |  | 
|   [ DescribeProductView ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProductView.html)  | Describes a product as an end\-user | Read |  |  |  | 
|   [ DescribeProvisionedProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProvisionedProduct.html)  | Describes a provisioned product | Read |  |  |  | 
|   [ DescribeProvisionedProductPlan ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProvisionedProductPlan.html)  | Describes a provisioned product plan | Read |  |  |  | 
|   [ DescribeProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProvisioningArtifact.html)  | Describes a provisioning artifact | Read |  |  |  | 
|   [ DescribeProvisioningParameters ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeProvisioningParameters.html)  | Describes the parameters that you need to specify to successfully provision a specified provisioning artifact | Read |  |  |  | 
|   [ DescribeRecord ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeRecord.html)  | Describes a record and lists any outputs | Read |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ DescribeServiceAction ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeServiceAction.html)  | Describes a self\-service action\. | Read |  |  |  | 
|   [ DescribeServiceActionExecutionParameters ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeServiceActionExecutionParameters.html)  | Gets the default parameters if you executed the specified Service Action on the specified Provisioned Product\. | Read |  |  |  | 
|   [ DescribeTagOption ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DescribeTagOption.html)  | Gets information about the specified TagOption\. | Read |  |  |  | 
|   [ DisableAWSOrganizationsAccess ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisableAWSOrganizationsAccess.html)  | Disable portfolio sharing through AWS Organizations feature\. | Write |  |  |  | 
|   [ DisassociateBudgetFromResource ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociateBudgetFromResource.html)  | Disassociates a budget from a resource\. | Write |  |  |  | 
|   [ DisassociatePrincipalFromPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociatePrincipalFromPortfolio.html)  | Disassociates an IAM principal from a portfolio\. | Write |  |  |  | 
|   [ DisassociateProductFromPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociateProductFromPortfolio.html)  | Disassociates a product from a portfolio | Write |  |  |  | 
|   [ DisassociateServiceActionFromProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociateServiceActionFromProvisioningArtifact.html)  | Disassociates the specified self\-service action association from the specified provisioning artifact\. | Write |  |  |  | 
|   [ DisassociateTagOptionFromResource ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_DisassociateTagOptionFromResource.html)  | Disassociates the specified TagOption from the specified resource\. | Write |  |  |  | 
|   [ EnableAWSOrganizationsAccess ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_EnableAWSOrganizationsAccess.html)  | Enable portfolio sharing feature through AWS Organizations\. | Write |  |  |  | 
|   [ ExecuteProvisionedProductPlan ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ExecuteProvisionedProductPlan.html)  | Executes a provisioned product plan | Write |  |  |  | 
|   [ ExecuteProvisionedProductServiceAction ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ExecuteProvisionedProductServiceAction.html)  | Executes a provisioned product plan | Write |  |  |  | 
|   [ GetAWSOrganizationsAccessStatus ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_GetAWSOrganizationsAccessStatus.html)  | Get the Access Status for AWS Organization portfolio share feature\. | Read |  |  |  | 
|   [ ListAcceptedPortfolioShares ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListAcceptedPortfolioShares.html)  | Lists the portfolios that have been shared with you and you have accepted | List |  |  |  | 
|   [ ListBudgetsForResource ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListBudgetsForResource.html)  | Lists all the budgets associated to a resource\. | List |  |  |  | 
|   [ ListConstraintsForPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListConstraintsForPortfolio.html)  | Lists constraints associated with a given portfolio | List |  |  |  | 
|   [ ListLaunchPaths ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListLaunchPaths.html)  | Lists the different ways to launch a given product as an end\-user | List |  |  |  | 
|   [ ListOrganizationPortfolioAccess ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListOrganizationPortfolioAccess.html)  | Lists the organization nodes that have access to the specified portfolio\. | List |  |  |  | 
|   [ ListPortfolioAccess ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfolioAccess.html)  | Lists the AWS accounts you have shared a given portfolio with | List |  |  |  | 
|   [ ListPortfolios ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfolios.html)  | Lists the portfolios in your account | List |  |  |  | 
|   [ ListPortfoliosForProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPortfoliosForProduct.html)  | Lists the portfolios associated with a given product | List |  |  |  | 
|   [ ListPrincipalsForPortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListPrincipalsForPortfolio.html)  | Lists the IAM principals associated with a given portfolio | List |  |  |  | 
|   [ ListProvisionedProductPlans ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListProvisionedProductPlans.html)  | Lists the provisioned product plans | List |  |  |  | 
|   [ ListProvisioningArtifacts ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListProvisioningArtifacts.html)  | Lists the provisioning artifacts associated with a given product | List |  |  |  | 
|   [ ListProvisioningArtifactsForServiceAction ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListProvisioningArtifactsForServiceAction.html)  | Lists all provisioning artifacts for the specified self\-service action\. | List |  |  |  | 
|   [ ListRecordHistory ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListRecordHistory.html)  | Lists all the records in your account or all the records related to a given provisioned product | List |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ ListResourcesForTagOption ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListResourcesForTagOption.html)  | Lists the resources associated with the specified TagOption\. | List |  |  |  | 
|   [ ListServiceActions ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListServiceActions.html)  | Lists all self\-service actions\. | List |  |  |  | 
|   [ ListServiceActionsForProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListServiceActionsForProvisioningArtifact.html)  | Lists all the service actions in your account | List |  |  |  | 
|   [ ListStackInstancesForProvisionedProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListStackInstancesForProvisionedProduct.html)  | Lists account, region and status of each stack instances that are associated with a CFN\_STACKSET type provisioned product | List |  |  |  | 
|   [ ListTagOptions ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ListTagOptions.html)  | Lists the specified TagOptions or all TagOptions\. | List |  |  |  | 
|   [ ProvisionProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ProvisionProduct.html)  | Provisions a product with a specified provisioning artifact and launch parameters | Write |  |  |  | 
|   [ RejectPortfolioShare ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_RejectPortfolioShare.html)  | Rejects a portfolio that has been shared with you that you previously accepted | Write |  |  |  | 
|   [ ScanProvisionedProducts ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ScanProvisionedProducts.html)  | Lists all the provisioned products in your account | List |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ SearchProducts ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_SearchProducts.html)  | Lists the products available to you as an end\-user | List |  |  |  | 
|   [ SearchProductsAsAdmin ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_SearchProductsAsAdmin.html)  | Lists all the products in your account or all the products associated with a given portfolio | List |  |  |  | 
|   [ SearchProvisionedProducts ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_SearchProvisionedProducts.html)  | Lists all the provisioned products in your account | List |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ TerminateProvisionedProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_TerminateProvisionedProduct.html)  | Terminates an existing provisioned product | Write |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ UpdateConstraint ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateConstraint.html)  | Updates the metadata fields of an existing constraint | Write |  |  |  | 
|   [ UpdatePortfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdatePortfolio.html)  | Updates the metadata fields and/or tags of an existing portfolio | Write |  |  |  | 
|   [ UpdateProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProduct.html)  | Updates the metadata fields and/or tags of an existing product | Write |  |  |  | 
|   [ UpdateProvisionedProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProvisionedProduct.html)  | Updates an existing provisioned product | Write |  |   [ servicecatalog:accountLevel ](#awsservicecatalog-servicecatalog_accountLevel)   [ servicecatalog:roleLevel ](#awsservicecatalog-servicecatalog_roleLevel)   [ servicecatalog:userLevel ](#awsservicecatalog-servicecatalog_userLevel)   |  | 
|   [ UpdateProvisionedProductProperties ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProvisionedProductProperties.html)  | Updates the properties of an existing provisioned product | Write |  |  |  | 
|   [ UpdateProvisioningArtifact ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateProvisioningArtifact.html)  | Updates the metadata fields of an existing provisioning artifact | Write |  |  |  | 
|   [ UpdateServiceAction ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateServiceAction.html)  | Updates a self\-service action\. | Write |  |  |  | 
|   [ UpdateTagOption ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_UpdateTagOption.html)  | Updates the specified TagOption\. | Write |  |  |  | 

## Resources Defined by AWS Service Catalog<a name="awsservicecatalog-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsservicecatalog-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ Portfolio ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_PortfolioDetail.html)  |  arn:$\{Partition\}:catalog:$\{Region\}:$\{Account\}:portfolio/$\{PortfolioId\}  |  | 
|   [ Product ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ProductViewDetail.html)  |  arn:$\{Partition\}:catalog:$\{Region\}:$\{Account\}:product/$\{ProductId\}  |  | 
|   [ ProvisionedProduct ](https://docs.aws.amazon.com/servicecatalog/latest/dg/API_ProvisionedProductDetail.html)  |  arn:$\{Partition\}:servicecatalog:$\{Region\}:$\{Account\}:stack/$\{ProvisionedProductName\}/$\{ProvisionedProductId\}  |  | 

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