# Actions, resources, and condition keys for Amazon EC2 Instance Connect<a name="list_amazonec2instanceconnect"></a>

Amazon EC2 Instance Connect \(service prefix: `ec2-instance-connect`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Connect-using-EC2-Instance-Connect.html)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/ec2-instance-connect/latest/APIReference/Welcome.html)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-set-up.html) permission policies\.

**Topics**
+ [Actions defined by Amazon EC2 Instance Connect](#amazonec2instanceconnect-actions-as-permissions)
+ [Resource types defined by Amazon EC2 Instance Connect](#amazonec2instanceconnect-resources-for-iam-policies)
+ [Condition keys for Amazon EC2 Instance Connect](#amazonec2instanceconnect-policy-keys)

## Actions defined by Amazon EC2 Instance Connect<a name="amazonec2instanceconnect-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The actions table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2instanceconnect.html)

## Resource types defined by Amazon EC2 Instance Connect<a name="amazonec2instanceconnect-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonec2instanceconnect-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The resource types table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource types | ARN | Condition keys | 
| --- | --- | --- | 
|   [ instance ](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}  |   [ aws:ResourceTag/$\{TagKey\} ](#amazonec2instanceconnect-aws_ResourceTag___TagKey_)   [ ec2:ResourceTag/$\{TagKey\} ](#amazonec2instanceconnect-ec2_ResourceTag___TagKey_)   | 

## Condition keys for Amazon EC2 Instance Connect<a name="amazonec2instanceconnect-policy-keys"></a>

Amazon EC2 Instance Connect defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The condition keys table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available global condition keys](reference_policies_condition-keys.html#AvailableKeys)\.


****  

| Condition keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on the tags associated with the resource | String | 
|   [ ec2:ResourceTag/$\{TagKey\} ](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-resourcetag)  | Filters actions based on the tags associated with the resource | String | 
|   [ ec2:osuser ](https://docs.aws.amazon.com/ec2-instance-connect/latest/APIReference/API_SendSSHPublicKey.html)  | Filters access by specifying the default user name for the AMI that you used to launch your instance | String | 