# Actions, Resources, and Condition Keys for AWS IoT SiteWise<a name="list_awsiotsitewise"></a>

AWS IoT SiteWise \(service prefix: `iotsitewise`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/iotsitewise/latest/userguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/iotsitewise/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/iotsitewise/latest/userguide/authorization.html) permission policies\.

**Topics**
+ [Actions Defined by AWS IoT SiteWise](#awsiotsitewise-actions-as-permissions)
+ [Resources Defined by IoT SiteWise](#awsiotsitewise-resources-for-iam-policies)
+ [Condition Keys for AWS IoT SiteWise](#awsiotsitewise-policy-keys)

## Actions Defined by AWS IoT SiteWise<a name="awsiotsitewise-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsiotsitewise.html)

## Resources Defined by IoT SiteWise<a name="awsiotsitewise-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsiotsitewise-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ asset ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/asset.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:asset/$\{AssetId\}  |  | 
|   [ asset\-template ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/asset-template.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:asset\-template/$\{AssetTemplateId\}  |  | 
|   [ gateway ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/gateway.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:gateway/$\{GatewayId\}  |  | 
|   [ group ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/group.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:group/$\{GroupId\}  |  | 
|   [ measurement ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/measurement.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:measurement/$\{MeasurementId\}  |  | 
|   [ measurement\-data\-store ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/measurement-data-store.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:measurement\-data\-store/$\{MeasurementDataStoreId\}  |  | 
|   [ metric ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/metric.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:metric/$\{MetricId\}  |  | 
|   [ metric\-type ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/metric-type.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:metric\-type/$\{MetricTypeId\}  |  | 
|   [ view ](https://docs.aws.amazon.com/iotsitewise/latest/userguide/view.html)  |  arn:$\{Partition\}:iotsitewise:$\{Region\}:$\{Account\}:view/$\{ViewId\}  |  | 

## Condition Keys for AWS IoT SiteWise<a name="awsiotsitewise-policy-keys"></a>

IoT SiteWise has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.