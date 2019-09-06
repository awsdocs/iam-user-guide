# Actions, Resources, and Condition Keys for Amazon EC2 Instance Connect Service<a name="list_amazonec2instanceconnectservice"></a>

Amazon EC2 Instance Connect Service \(service prefix: `ec2-instance-connect`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ View a [list of the API operations available for this service](${APIDocRoot}APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](${UserDocRoot}UserGuide/ec2-instance-connect-set-up.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon EC2 Instance Connect Service](#amazonec2instanceconnectservice-actions-as-permissions)
+ [Resources Defined by Amazon EC2 Instance Connect Service](#amazonec2instanceconnectservice-resources-for-iam-policies)
+ [Condition Keys for Amazon EC2 Instance Connect Service](#amazonec2instanceconnectservice-policy-keys)

## Actions Defined by Amazon EC2 Instance Connect Service<a name="amazonec2instanceconnectservice-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ SendSSHPublicKey ](${APIDocRoot}APIReference/API_SendSSHPublicKey.html)  | Pushes the SSH public key to the instance where it remains for 60 seconds\. | Write |  |   [ ec2:osuser ](#amazonec2instanceconnectservice-ec2_osuser)   |  | 

## Resources Defined by Amazon EC2 Instance Connect Service<a name="amazonec2instanceconnectservice-resources-for-iam-policies"></a>

Amazon EC2 Instance Connect Service has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon EC2 Instance Connect Service<a name="amazonec2instanceconnectservice-policy-keys"></a>

Amazon EC2 Instance Connect Service defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ ec2:osuser ](${APIDocRoot}APIReference/API_SendSSHPublicKey.html)  | Specifies the OS user that can push the SSH public key to the instance\. | String | 