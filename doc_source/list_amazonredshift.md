# Actions, Resources, and Condition Keys for Amazon Redshift<a name="list_amazonredshift"></a>

Amazon Redshift \(service prefix: `redshift`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/redshift/latest/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/redshift/latest/APIReference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-authentication-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Redshift](#amazonredshift-actions-as-permissions)
+ [Resource Types Defined by Amazon Redshift](#amazonredshift-resources-for-iam-policies)
+ [Condition Keys for Amazon Redshift](#amazonredshift-policy-keys)

## Actions Defined by Amazon Redshift<a name="amazonredshift-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonredshift.html)

## Resource Types Defined by Amazon Redshift<a name="amazonredshift-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonredshift-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ cluster ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:cluster:$\{ClusterName\}  |  | 
|   [ dbgroup ](https://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_GROUP.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbgroup:$\{ClusterName\}/$\{DbGroup\}  |  | 
|   [ dbname ](https://docs.aws.amazon.com/redshift/latest/dg/t_creating_database.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbname:$\{ClusterName\}/$\{DbName\}  |  | 
|   [ dbuser ](https://docs.aws.amazon.com/redshift/latest/dg/r_Users.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbuser:$\{ClusterName\}/$\{DbUser\}  |  | 
|   [ eventsubscription ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-events.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:eventsubscription:$\{EventSubscriptionName\}  |  | 
|   [ hsmclientcertificate ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#working-with-HSM)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:hsmclientcertificate:$\{HSMClientCertificateId\}  |  | 
|   [ hsmconfiguration ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#working-with-HSM)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:hsmconfiguration:$\{HSMConfigurationId\}  |  | 
|   [ parametergroup ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-parameter-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:parametergroup:$\{ParameterGroupName\}  |  | 
|   [ securitygroup ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroup:$\{SecurityGroupName\}/ec2securitygroup/$\{Owner\}/$\{Ec2SecurityGroupId\}  |  | 
|   [ securitygroupingress\-cidr ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroupingress:$\{SecurityGroupName\}/cidrip/$\{IpRange\}  |  | 
|   [ securitygroupingress\-ec2securitygroup ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroupingress:$\{SecurityGroupName\}/ec2securitygroup/$\{Owner\}/$\{Ece2SecuritygroupId\}  |  | 
|   [ snapshot ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-snapshots.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:snapshot:$\{ClusterName\}/$\{SnapshotName\}  |  | 
|   [ snapshotcopygrant ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#configure-snapshot-copy-grant)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:snapshotcopygrant:$\{SnapshotCopyGrantName\}  |  | 
|   [ snapshotschedule ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-snapshots.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:snapshotschedule:$\{ParameterGroupName\}  |  | 
|   [ subnetgroup ](https://docs.aws.amazon.com/redshift/latest/mgmt/working-with-cluster-subnet-groups.html)  |  arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:subnetgroup:$\{SubnetGroupName\}  |  | 

## Condition Keys for Amazon Redshift<a name="amazonredshift-policy-keys"></a>

Amazon Redshift defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ redshift:DbName ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters access by the database name | String | 
|   [ redshift:DbUser ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters access by the database user name | String | 
|   [ redshift:DurationSeconds ](https://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions)  | Filters access by the number of seconds until a temporary credential set expires | String | 