# Actions, Resources, and Condition Keys for Amazon Redshift<a name="list_amazonredshift"></a>

Amazon Redshift \(service prefix: `redshift`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/redshift/latest/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/redshift/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-authentication-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon Redshift](#amazonredshift-actions-as-permissions)
+ [Resources Defined by Redshift](#amazonredshift-resources-for-iam-policies)
+ [Condition Keys for Amazon Redshift](#amazonredshift-policy-keys)

## Actions Defined by Amazon Redshift<a name="amazonredshift-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonredshift.html)

## Resources Defined by Redshift<a name="amazonredshift-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonredshift-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:cluster:$\{ClusterName\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_GROUP.html](http://docs.aws.amazon.com/redshift/latest/dg/r_CREATE_GROUP.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbgroup:$\{ClusterName\}/$\{DbGroup\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/dg/t_creating_database.html](http://docs.aws.amazon.com/redshift/latest/dg/t_creating_database.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbname:$\{ClusterName\}/$\{DbName\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/dg/r_Users.html](http://docs.aws.amazon.com/redshift/latest/dg/r_Users.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:dbuser:$\{ClusterName\}/$\{DbUser\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-events.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-events.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:eventsubscription:$\{EventSubscriptionName\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#working-with-HSM](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#working-with-HSM) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:hsmclientcertificate:$\{HSMClientCertificateId\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#working-with-HSM](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#working-with-HSM) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:hsmconfiguration:$\{HSMConfigurationId\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-parameter-groups.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-parameter-groups.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:parametergroup:$\{ParameterGroupName\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroup:$\{SecurityGroupName\}/ec2securitygroup/$\{Owner\}/$\{Ec2SecurityGroupId\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroupingress:$\{SecurityGroupName\}/cidrip/$\{IpRange\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-security-groups.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:securitygroupingress:$\{SecurityGroupName\}/ec2securitygroup/$\{Owner\}/$\{Ece2SecuritygroupId\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-snapshots.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-snapshots.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:$\{ClusterName\}/$\{SnapshotName\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#configure-snapshot-copy-grant](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html#configure-snapshot-copy-grant) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:snapshotcopygrant:$\{SnapshotCopyGrantName\} |  | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-cluster-subnet-groups.html](http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-cluster-subnet-groups.html) | arn:$\{Partition\}:redshift:$\{Region\}:$\{Account\}:subnetgroup:$\{SubnetGroupName\} |  | 

## Condition Keys for Amazon Redshift<a name="amazonredshift-policy-keys"></a>

Amazon Redshift defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions](http://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions) | Control access based on the database name\. | String | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions](http://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions) | Control access based on the database user name\. | String | 
| [http://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions](http://docs.aws.amazon.com/redshift/latest/mgmt/redshift-iam-access-control-overview.html#redshift-policy-resources.conditions) | Control access based on the number of seconds until a temporary credential set expires\. | String | 