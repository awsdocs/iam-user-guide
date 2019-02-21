# Actions, Resources, and Condition Keys for AWS Amplify<a name="list_awsamplify"></a>

AWS Amplify \(service prefix: `amplify`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/amplify/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/amplify/latest/userguide/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/amplify/latest/userguide/iam-auth.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Amplify](#awsamplify-actions-as-permissions)
+ [Resources Defined by Amplify](#awsamplify-resources-for-iam-policies)
+ [Condition Keys for AWS Amplify](#awsamplify-policy-keys)

## Actions Defined by AWS Amplify<a name="awsamplify-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateApp ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Creates a new Amplify App\. | Write |  |  |  | 
|   [ CreateBranch ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Creates a new Branch for an Amplify App\. | Write |   [ apps\* ](#awsamplify-apps)   |  |  | 
|   [ CreateDomainAssociation ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Create a new DomainAssociation on an App | Write |   [ apps\* ](#awsamplify-apps)   |  |  | 
|   [ DeleteApp ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Delete an existing Amplify App by appId\. | Write |   [ apps\* ](#awsamplify-apps)   |  |  | 
|   [ DeleteBranch ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Deletes a branch for an Amplify App\. | Write |   [ branches\* ](#awsamplify-branches)   |  |  | 
|   [ DeleteDomainAssociation ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Deletes a DomainAssociation\. | Write |   [ domains\* ](#awsamplify-domains)   |  |  | 
|   [ DeleteJob ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Delete a job, for an Amplify branch, part of Amplify App\. | Write |   [ jobs\* ](#awsamplify-jobs)   |  |  | 
|   [ GetApp ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Retrieves an existing Amplify App by appId\. | Read |   [ apps\* ](#awsamplify-apps)   |  |  | 
|   [ GetBranch ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Retrieves a branch for an Amplify App\. | Read |   [ branches\* ](#awsamplify-branches)   |  |  | 
|   [ GetDomainAssociation ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Retrieves domain info that corresponds to an appId and domainName\. | Read |   [ domains\* ](#awsamplify-domains)   |  |  | 
|   [ GetJob ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Get a job for a branch, part of an Amplify App\. | Read |   [ jobs\* ](#awsamplify-jobs)   |  |  | 
|   [ ListApps ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Lists existing Amplify Apps\. | List |  |  |  | 
|   [ ListBranches ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Lists branches for an Amplify App\. | List |   [ apps\* ](#awsamplify-apps)   |  |  | 
|   [ ListDomainAssociations ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | List domains with an app | List |   [ apps\* ](#awsamplify-apps)   |  |  | 
|   [ ListJobs ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | List Jobs for a branch, part of an Amplify App\. | List |   [ branches\* ](#awsamplify-branches)   |  |  | 
|   [ StartJob ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Starts a new job for a branch, part of an Amplify App\. | Write |   [ jobs\* ](#awsamplify-jobs)   |  |  | 
|   [ StopJob ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Stop a job that is in progress, for an Amplify branch, part of Amplify App\. | Write |   [ jobs\* ](#awsamplify-jobs)   |  |  | 
|   [ UpdateApp ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Updates an existing Amplify App\. | Write |   [ apps\* ](#awsamplify-apps)   |  |  | 
|   [ UpdateBranch ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Updates a branch for an Amplify App\. | Write |   [ branches\* ](#awsamplify-branches)   |  |  | 
|   [ UpdateDomainAssociation ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  | Update a DomainAssociation on an App\. | Write |   [ domains\* ](#awsamplify-domains)   |  |  | 

## Resources Defined by Amplify<a name="awsamplify-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsamplify-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ apps ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  |  arn:$\{Partition\}:amplify:$\{Region\}:$\{Account\}:apps/$\{AppId\}  |  | 
|   [ branches ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  |  arn:$\{Partition\}:amplify:$\{Region\}:$\{Account\}:apps/$\{AppId\}/branches/$\{BranchName\}  |  | 
|   [ jobs ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  |  arn:$\{Partition\}:amplify:$\{Region\}:$\{Account\}:apps/$\{AppId\}/branches/$\{BranchName\}/jobs/$\{JobId\}  |  | 
|   [ domains ](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html)  |  arn:$\{Partition\}:amplify:$\{Region\}:$\{Account\}:apps/$\{AppId\}/domains/$\{DomainName\}  |  | 

## Condition Keys for AWS Amplify<a name="awsamplify-policy-keys"></a>

Amplify has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.