# Actions, Resources, and Condition Keys for AWS Elemental MediaPackage VOD<a name="list_awselementalmediapackagevod"></a>

AWS Elemental MediaPackage VOD \(service prefix: `mediapackage-vod`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/mediapackage/latest/ug/)\.
+ View a list of the [API operations available for this service](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/)\.
+ Learn how to secure this service and its resources by [using IAM](https://docs.aws.amazon.com/mediapackage/latest/ug/setting-up.html#setting-up-create-iam-user) permission policies\.

**Topics**
+ [Actions Defined by AWS Elemental MediaPackage VOD](#awselementalmediapackagevod-actions-as-permissions)
+ [Resource Types Defined by AWS Elemental MediaPackage VOD](#awselementalmediapackagevod-resources-for-iam-policies)
+ [Condition Keys for AWS Elemental MediaPackage VOD](#awselementalmediapackagevod-policy-keys)

## Actions Defined by AWS Elemental MediaPackage VOD<a name="awselementalmediapackagevod-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource Types** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ CreateAsset ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/assets.html#assetspost)  | Grants permission to create an asset in AWS Elemental MediaPackage | Write |  |  |  | 
|   [ CreatePackagingConfiguration ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_configurations.html#packaging_configurationspost)  | Grants permission to create a packaging configuration in AWS Elemental MediaPackage | Write |  |  |  | 
|   [ CreatePackagingGroup ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_groups.html#packaging_groupspost)  | Grants permission to create a packaging group in AWS Elemental MediaPackage | Write |  |  |  | 
|   [ DeleteAsset ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/assets-id.html#assets-iddelete)  | Grants permission to delete an asset in AWS Elemental MediaPackage | Write |   [ assets\* ](#awselementalmediapackagevod-assets)   |  |  | 
|   [ DeletePackagingConfiguration ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_configurations-id.html#packaging_configurations-iddelete)  | Grants permission to delete a packaging configuration in AWS Elemental MediaPackage | Write |   [ packaging\-configurations\* ](#awselementalmediapackagevod-packaging-configurations)   |  |  | 
|   [ DeletePackagingGroup ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_groups-id.html#packaging_groups-iddelete)  | Grants permission to delete a packaging group in AWS Elemental MediaPackage | Write |   [ packaging\-groups\* ](#awselementalmediapackagevod-packaging-groups)   |  |  | 
|   [ DescribeAsset ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/assets-id.html#assets-idget)  | Grants permission to view the details of an asset in AWS Elemental MediaPackage | Read |   [ assets\* ](#awselementalmediapackagevod-assets)   |  |  | 
|   [ DescribePackagingConfiguration ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_configurations-id.html#packaging_configurations-idget)  | Grants permission to view the details of a packaging configuration in AWS Elemental MediaPackage | Read |   [ packaging\-configurations\* ](#awselementalmediapackagevod-packaging-configurations)   |  |  | 
|   [ DescribePackagingGroup ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_groups-id.html#packaging_groups-idget)  | Grants permission to view the details of a packaging group in AWS Elemental MediaPackage | Read |   [ packaging\-groups\* ](#awselementalmediapackagevod-packaging-groups)   |  |  | 
|   [ ListAssets ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/assets.html#assetsget)  | Grants permission to view a list of assets in AWS Elemental MediaPackage | List |  |  |  | 
|   [ ListPackagingConfigurations ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_configurations.html#packaging_configurationsget)  | Grants permission to view a list of packaging configurations in AWS Elemental MediaPackage | List |  |  |  | 
|   [ ListPackagingGroups ](https://docs.aws.amazon.com/mediapackage-vod/latest/apireference/packaging_groups.html#packaging_groupsget)  | Grants permission to view a list of packaging groups in AWS Elemental MediaPackage | List |  |  |  | 

## Resource Types Defined by AWS Elemental MediaPackage VOD<a name="awselementalmediapackagevod-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awselementalmediapackagevod-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ assets ](https://docs.aws.amazon.com/mediapackage/latest/ug/asset.html)  |  arn:$\{Partition\}:mediapackage\-vod:$\{Region\}:$\{Account\}:assets/$\{AssetIdentifier\}  |  | 
|   [ packaging\-configurations ](https://docs.aws.amazon.com/mediapackage/latest/ug/pkg-cfig.html)  |  arn:$\{Partition\}:mediapackage\-vod:$\{Region\}:$\{Account\}:packaging\-configurations/$\{PackagingConfigurationIdentifier\}  |  | 
|   [ packaging\-groups ](https://docs.aws.amazon.com/mediapackage/latest/ug/pkg-group.html)  |  arn:$\{Partition\}:mediapackage\-vod:$\{Region\}:$\{Account\}:packaging\-groups/$\{PackagingGroupIdentifier\}  |  | 

## Condition Keys for AWS Elemental MediaPackage VOD<a name="awselementalmediapackagevod-policy-keys"></a>

MediaPackage VOD has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.