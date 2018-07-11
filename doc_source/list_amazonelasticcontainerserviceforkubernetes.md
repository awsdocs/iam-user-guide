# Actions, Resources, and Condition Keys for Amazon Elastic Container Service for Kubernetes<a name="list_amazonelasticcontainerserviceforkubernetes"></a>

Amazon Elastic Container Service for Kubernetes \(service prefix: `eks`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/eks/latest/userguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/eks/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/eks/latest/userguide/IAM_policies.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Elastic Container Service for Kubernetes](#amazonelasticcontainerserviceforkubernetes-actions-as-permissions)
+ [Resources Defined by EKS](#amazonelasticcontainerserviceforkubernetes-resources-for-iam-policies)
+ [Condition Keys for Amazon Elastic Container Service for Kubernetes](#amazonelasticcontainerserviceforkubernetes-policy-keys)

## Actions Defined by Amazon Elastic Container Service for Kubernetes<a name="amazonelasticcontainerserviceforkubernetes-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateCluster ](http://docs.aws.amazon.com/eks/latest/APIReference/API_CreateCluster.html)  | Creates an Amazon EKS cluster\. | Write |  |  |  | 
|   [ DeleteCluster ](http://docs.aws.amazon.com/eks/latest/APIReference/API_DeleteCluster.html)  | Deletes an Amazon EKS cluster\. | Write |   [ cluster\* ](#amazonelasticcontainerserviceforkubernetes-cluster)   |  |  | 
|   [ DescribeCluster ](http://docs.aws.amazon.com/eks/latest/APIReference/API_DescribeCluster.html)  | Returns descriptive information about an Amazon EKS cluster\. | Read |   [ cluster\* ](#amazonelasticcontainerserviceforkubernetes-cluster)   |  |  | 
|   [ ListClusters ](http://docs.aws.amazon.com/eks/latest/APIReference/API_ListClusters.html)  | Lists the Amazon EKS clusters in your AWS account \(in the specified or default region\)\. | List |  |  |  | 

## Resources Defined by EKS<a name="amazonelasticcontainerserviceforkubernetes-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonelasticcontainerserviceforkubernetes-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ cluster ](http://docs.aws.amazon.com/eks/latest/userguide/getting-started.html)  |  arn:$\{Partition\}:eks:$\{Region\}:$\{Account\}:cluster/$\{ClusterName\}  |  | 

## Condition Keys for Amazon Elastic Container Service for Kubernetes<a name="amazonelasticcontainerserviceforkubernetes-policy-keys"></a>

EKS has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.