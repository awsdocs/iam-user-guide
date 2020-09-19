# Actions, resources, and condition keys for Amazon Redshift<a name="list_amazonredshift"></a>

Amazon Redshift \(service prefix: `redshift`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/redshift/latest/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/redshift/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-authentication-access-control.html) permission policies\.

**Topics**
+ [Actions defined by Amazon Redshift](#amazonredshift-actions-as-permissions)
+ [Resource types defined by Amazon Redshift](#amazonredshift-resources-for-iam-policies)
+ [Condition keys for Amazon Redshift](#amazonredshift-policy-keys)

## Actions defined by Amazon Redshift<a name="amazonredshift-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonredshift.html)

## Resource types defined by Amazon Redshift<a name="amazonredshift-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonredshift-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ cluster ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:cluster:$\{ClusterName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ dbgroup ](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_GROUP.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbgroup:$\{ClusterName\}/$\{DbGroup\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ dbname ](https://docs.aws.amazon.com/redshift/latest/dg/t_creating_database.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbname:$\{ClusterName\}/$\{DbName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ dbuser ](https://docs.aws.amazon.com/redshift/latest/dg/r_Users.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbuser:$\{ClusterName\}/$\{DbUser\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ eventsubscription ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-events.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:eventsubscription:$\{EventSubscriptionName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ hsmclientcertificate ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#working-with-HSM)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:hsmclientcertificate:$\{HSMClientCertificateId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ hsmconfiguration ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#working-with-HSM)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:hsmconfiguration:$\{HSMConfigurationId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ parametergroup ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-parameter-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:parametergroup:$\{ParameterGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ securitygroup ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroup:$\{SecurityGroupName\}/ec2securitygroup/$\{Owner\}/$\{Ec2SecurityGroupId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ securitygroupingress\-cidr ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroupingress:$\{SecurityGroupName\}/cidrip/$\{IpRange\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ securitygroupingress\-ec2securitygroup ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroupingress:$\{SecurityGroupName\}/ec2securitygroup/$\{Owner\}/$\{Ece2SecuritygroupId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ snapshot ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-snapshots.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:snapshot:$\{ClusterName\}/$\{SnapshotName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ snapshotcopygrant ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#configure-snapshot-copy-grant)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:snapshotcopygrant:$\{SnapshotCopyGrantName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ snapshotschedule ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-snapshots.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:snapshotschedule:$\{ParameterGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 
|   [ subnetgroup ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-cluster-subnet-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:subnetgroup:$\{SubnetGroupName\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonredshift-aws_ResourceTag___TagKey_)   | 

## Condition keys for Amazon Redshift<a name="amazonredshift-policy-keys"></a>

Amazon Redshift defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/$\{TagKey\} ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters actions based on the allowed set of values for each of the tags | String | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters actions based on tag\-value associated with the resource | String | 
|   [ aws:TagKeys ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters actions based on the presence of mandatory tags in the request | String | 
|   [ redshift:DbName ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters access by the database name | String | 
|   [ redshift:DbUser ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters access by the database user name | String | 
|   [ redshift:DurationSeconds ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters access by the number of seconds until a temporary credential set expires | String | 