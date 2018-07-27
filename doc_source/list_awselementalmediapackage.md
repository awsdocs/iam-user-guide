# Actions, Resources, and Condition Keys for AWS Elemental MediaPackage<a name="list_awselementalmediapackage"></a>

AWS Elemental MediaPackage \(service prefix: `mediapackage`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/mediapackage/latest/ug/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/mediapackage/latest/apireference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/mediapackage/latest/ug/setting-up.html#setting-up-create-iam-user) permission policies\.

**Topics**
+ [Actions Defined by AWS Elemental MediaPackage](#awselementalmediapackage-actions-as-permissions)
+ [Resources Defined by MediaPackage](#awselementalmediapackage-resources-for-iam-policies)
+ [Condition Keys for AWS Elemental MediaPackage](#awselementalmediapackage-policy-keys)

## Actions Defined by AWS Elemental MediaPackage<a name="awselementalmediapackage-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateChannel ](http://docs.aws.amazon.com/mediapackage/latest/apireference/channels.html#channelspost)  | Grants permission to create a channel in AWS Elemental MediaPackage\. | Write |  |  |  | 
|   [ CreateOriginEndpoint ](http://docs.aws.amazon.com/mediapackage/latest/apireference/origin_endpoints.html#origin_endpointspost)  | Grants permission to create an endpoint in AWS Elemental MediaPackage\. | Write |  |  |  | 
|   [ DeleteChannel ](http://docs.aws.amazon.com/mediapackage/latest/apireference/channels-id.html#channels-iddelete)  | Grants permission to delete a channel in AWS Elemental MediaPackage\. | Write |  |  |  | 
|   [ DeleteOriginEndpoint ](http://docs.aws.amazon.com/mediapackage/latest/apireference/origin_endpoints-id.html#origin_endpoints-iddelete)  | Grants permission to delete an endpoint in AWS Elemental MediaPackage\. | Write |  |  |  | 
|   [ DescribeChannel ](http://docs.aws.amazon.com/mediapackage/latest/apireference/channels-id.html#channels-idget)  | Grants permission to view the details of a channel in AWS Elemental MediaPackage\. | Read |  |  |  | 
|   [ DescribeOriginEndpoint ](http://docs.aws.amazon.com/mediapackage/latest/apireference/origin_endpoints-id.html#origin_endpoints-idget)  | Grants permission to view the details of an endpoint in AWS Elemental MediaPackage\. | Read |  |  |  | 
|   [ ListChannels ](http://docs.aws.amazon.com/mediapackage/latest/apireference/channels.html#channelsget)  | Grants permission to view a list of channels in AWS Elemental MediaPackage\. | Read |  |  |  | 
|   [ ListOriginEndpoints ](http://docs.aws.amazon.com/mediapackage/latest/apireference/origin_endpoints.html#origin_endpointsget)  | Grants permission to view a list of endpoints in AWS Elemental MediaPackage\. | Read |  |  |  | 
|   [ UpdateChannel ](http://docs.aws.amazon.com/mediapackage/latest/apireference/channels-id.html#channels-idput)  | Grants permission to make changes to a channel in AWS Elemental MediaPackage\. | Write |  |  |  | 
|   [ UpdateOriginEndpoint ](http://docs.aws.amazon.com/mediapackage/latest/apireference/origin_endpoints-id.html#origin_endpoints-idput)  | Grants permission to make changes to an endpoint in AWS Elemental MediaPackage\. | Write |  |  |  | 

## Resources Defined by MediaPackage<a name="awselementalmediapackage-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awselementalmediapackage-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ channels ](http://docs.aws.amazon.com/mediapackage/latest/ug/channels.html)  |  arn:$\{Partition\}:mediapackage:$\{Region\}:$\{Account\}:channels/$\{ChannelIdentifier\}  |  | 
|   [ origin\_endpoints ](http://docs.aws.amazon.com/mediapackage/latest/ug/endpoints.html)  |  arn:$\{Partition\}:mediapackage:$\{Region\}:$\{Account\}:origin\_endpoints/$\{OriginEndpointIdentifier\}  |  | 

## Condition Keys for AWS Elemental MediaPackage<a name="awselementalmediapackage-policy-keys"></a>

MediaPackage has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.