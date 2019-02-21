# Actions, Resources, and Condition Keys for Amazon Managed Streaming for Kafka<a name="list_amazonmanagedstreamingforkafka"></a>

Amazon Managed Streaming for Kafka \(service prefix: `kafka`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/msk/latest/developerguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/msk/1.0/apireference/)\.

**Topics**
+ [Actions Defined by Amazon Managed Streaming for Kafka](#amazonmanagedstreamingforkafka-actions-as-permissions)
+ [Resources Defined by MSK](#amazonmanagedstreamingforkafka-resources-for-iam-policies)
+ [Condition Keys for Amazon Managed Streaming for Kafka](#amazonmanagedstreamingforkafka-policy-keys)

## Actions Defined by Amazon Managed Streaming for Kafka<a name="amazonmanagedstreamingforkafka-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateCluster ](https://docs.aws.amazon.com/msk/1.0/apireference/clusters.html#CreateCluster)  | Grants permission to create a cluster\. | Write |  |  |   ec2:DescribeSecurityGroups   ec2:DescribeSubnets   ec2:DescribeVpcs   iam:AttachRolePolicy   iam:CreateServiceLinkedRole   iam:PutRolePolicy   kms:CreateGrant   kms:DescribeKey   | 
|   [ DeleteCluster ](https://docs.aws.amazon.com/msk/1.0/apireference/clusters-clusterarn.html#DeleteCluster)  | Grants permission to delete a cluster\. | Write |  |  |  | 
|   [ DescribeCluster ](https://docs.aws.amazon.com/msk/1.0/apireference/clusters-clusterarn.html#DescribeCluster)  | Grants permission to describe a cluster\. | Read |  |  |  | 
|   [ GetBootstrapBrokers ](https://docs.aws.amazon.com/msk/1.0/apireference/clusters-clusterarn-bootstrap-brokers.html#GetBootstrapBrokers)  | Grants permission to get connection details for the broker nodes in a cluster\. | Read |  |  |  | 
|   [ ListClusters ](https://docs.aws.amazon.com/msk/1.0/apireference/clusters.html#ListClusters)  | Grants permission to return a list of all clusters in the current account\. | List |  |  |  | 
|   [ ListNodes ](https://docs.aws.amazon.com/msk/1.0/apireference/clusters-clusterarn-nodes.html#ListNodes)  | Grants permission to return a list of nodes in a cluster\. | List |  |  |  | 

## Resources Defined by MSK<a name="amazonmanagedstreamingforkafka-resources-for-iam-policies"></a>

Amazon Managed Streaming for Kafka has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Managed Streaming for Kafka<a name="amazonmanagedstreamingforkafka-policy-keys"></a>

MSK has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.