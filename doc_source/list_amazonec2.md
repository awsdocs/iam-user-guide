# Actions, Resources, and Condition Keys for Amazon EC2<a name="list_amazonec2"></a>

Amazon EC2 \(service prefix: `ec2`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AWSEC2/latest/APIReference/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/UsingIAM.html) permission policies\.

**Topics**
+ [Actions Defined by Amazon EC2](#amazonec2-actions-as-permissions)
+ [Resources Defined by EC2](#amazonec2-resources-for-iam-policies)
+ [Condition Keys for Amazon EC2](#amazonec2-policy-keys)

## Actions Defined by Amazon EC2<a name="amazonec2-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2.html)

## Resources Defined by EC2<a name="amazonec2-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#amazonec2-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ customer\-gateway ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:customer\-gateway/$\{CustomerGatewayId\}  |   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   | 
|   [ dhcp\-options ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:dhcp\-options/$\{DhcpOptionsId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   | 
|   [ elastic\-gpu ](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/elastic-gpus.html)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:elasticGpu/$\{ElasticGpuId\}  |  | 
|   [ fpga\-image ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}::fpga\-image/$\{FpgaImageId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Owner ](#amazonec2-ec2_Owner)   [ ec2:Public ](#amazonec2-ec2_Public)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   | 
|   [ image ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}::image/$\{ImageId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:ImageType ](#amazonec2-ec2_ImageType)   [ ec2:Owner ](#amazonec2-ec2_Owner)   [ ec2:Public ](#amazonec2-ec2_Public)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:RootDeviceType ](#amazonec2-ec2_RootDeviceType)   | 
|   [ instance ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:instance/$\{InstanceId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:AvailabilityZone ](#amazonec2-ec2_AvailabilityZone)   [ ec2:EbsOptimized ](#amazonec2-ec2_EbsOptimized)   [ ec2:InstanceProfile ](#amazonec2-ec2_InstanceProfile)   [ ec2:InstanceType ](#amazonec2-ec2_InstanceType)   [ ec2:PlacementGroup ](#amazonec2-ec2_PlacementGroup)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:RootDeviceType ](#amazonec2-ec2_RootDeviceType)   [ ec2:Tenancy ](#amazonec2-ec2_Tenancy)   | 
|   [ internet\-gateway ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:internet\-gateway/$\{InternetGatewayId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   | 
|   [ key\-pair ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:key\-pair/$\{KeyPairName\}  |   [ ec2:Region ](#amazonec2-ec2_Region)   | 
|   [ launch\-template ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:launch\-template/$\{LaunchTemplateId\}  |   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   | 
|   [ network\-acl ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:network\-acl/$\{NaclId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:Vpc ](#amazonec2-ec2_Vpc)   | 
|   [ network\-interface ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:network\-interface/$\{NetworkInterfaceId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:AuthorizedService ](#amazonec2-ec2_AuthorizedService)   [ ec2:AvailabilityZone ](#amazonec2-ec2_AvailabilityZone)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:Subnet ](#amazonec2-ec2_Subnet)   [ ec2:Vpc ](#amazonec2-ec2_Vpc)   | 
|   [ placement\-group ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:placement\-group/$\{PlacementGroupName\}  |   [ ec2:PlacementGroupStrategy ](#amazonec2-ec2_PlacementGroupStrategy)   [ ec2:Region ](#amazonec2-ec2_Region)   | 
|   [ reserved\-instances ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-reserved-instances.html)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:reserved\-instances/$\{ReservationId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:AvailabilityZone ](#amazonec2-ec2_AvailabilityZone)   [ ec2:InstanceType ](#amazonec2-ec2_InstanceType)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ReservedInstancesOfferingType ](#amazonec2-ec2_ReservedInstancesOfferingType)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:Tenancy ](#amazonec2-ec2_Tenancy)   | 
|   [ route\-table ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:route\-table/$\{RouteTableId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:Vpc ](#amazonec2-ec2_Vpc)   | 
|   [ security\-group ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:security\-group/$\{SecurityGroupId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:Vpc ](#amazonec2-ec2_Vpc)   | 
|   [ snapshot ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}::snapshot/$\{SnapshotId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Owner ](#amazonec2-ec2_Owner)   [ ec2:ParentVolume ](#amazonec2-ec2_ParentVolume)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:SnapshotTime ](#amazonec2-ec2_SnapshotTime)   [ ec2:VolumeSize ](#amazonec2-ec2_VolumeSize)   | 
|   [ spot\-instance\-request ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html)  |  arn:$\{Partition\}:ec2:$\{Region\}::spot\-instance\-request/$\{SpotInstanceRequestId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   | 
|   [ subnet ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:subnet/$\{SubnetId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:AvailabilityZone ](#amazonec2-ec2_AvailabilityZone)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:Vpc ](#amazonec2-ec2_Vpc)   | 
|   [ volume ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:volume/$\{VolumeId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:AvailabilityZone ](#amazonec2-ec2_AvailabilityZone)   [ ec2:Encrypted ](#amazonec2-ec2_Encrypted)   [ ec2:ParentSnapshot ](#amazonec2-ec2_ParentSnapshot)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:VolumeIops ](#amazonec2-ec2_VolumeIops)   [ ec2:VolumeSize ](#amazonec2-ec2_VolumeSize)   [ ec2:VolumeType ](#amazonec2-ec2_VolumeType)   | 
|   [ vpc ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:vpc/$\{VpcId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   [ ec2:Tenancy ](#amazonec2-ec2_Tenancy)   | 
|   [ vpc\-peering\-connection ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#EC2_ARN_Format)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:vpc\-peering\-connection/$\{VpcPeeringConnectionId\}  |   [ ec2:AccepterVpc ](#amazonec2-ec2_AccepterVpc)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:RequesterVpc ](#amazonec2-ec2_RequesterVpc)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   | 
|   [ vpn\-connection ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/VPC_VPN.html)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:vpn\-connection/$\{VpnConnectionId\}  |   [ aws:RequestTag/tag\-key ](#amazonec2-aws_RequestTag_tag-key)   [ aws:TagKeys ](#amazonec2-aws_TagKeys)   [ ec2:Region ](#amazonec2-ec2_Region)   [ ec2:ResourceTag/tag\-key ](#amazonec2-ec2_ResourceTag_tag-key)   | 
|   [ vpn\-gateway ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/VPC_VPN.html)  |  arn:$\{Partition\}:ec2:$\{Region\}:$\{Account\}:vpn\-gateway/$\{VpnGatewayId\}  |  | 

## Condition Keys for Amazon EC2<a name="amazonec2-policy-keys"></a>

Amazon EC2 defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
|   [ aws:RequestTag/tag\-key ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | A key that is present in the request the user makes to the EC2 service\. | String | 
|   [ aws:TagKeys ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The list of all the tag key names associated with the resource in the request\. | String | 
|   [ ec2:AccepterVpc ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of an accepter VPC in a VPC peering connection\. | String | 
|   [ ec2:AuthorizedService ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The AWS service that has permission to use a resource\. | String | 
|   [ ec2:AuthorizedUser ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The IAM principal that has permission to use a resource\. | String | 
|   [ ec2:AvailabilityZone ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of an Availability Zone in a region\. | String | 
|   [ ec2:CreateAction ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of a resource\-creating API action\.  | String | 
|   [ ec2:EbsOptimized ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | Whether the instance is enabled for EBS\-optimization\. | String | 
|   [ ec2:ElasticGpuType ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of the type of ElasticGpu\. | String | 
|   [ ec2:Encrypted ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | Whether the volume is encrypted\. | String | 
|   [ ec2:ImageType ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of the type of image\. | String | 
|   [ ec2:InstanceMarketType ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of the market type\. | String | 
|   [ ec2:InstanceProfile ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of the instance profile\. | String | 
|   [ ec2:InstanceType ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of the instance type\. | String | 
|   [ ec2:IsLaunchTemplateResource ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | Launch template resource flag\. | String | 
|   [ ec2:LaunchTemplate ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of the launch template\. | String | 
|   [ ec2:Owner ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name or account ID of the owner\. | String | 
|   [ ec2:ParentSnapshot ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of the parent snapshot\. | String | 
|   [ ec2:ParentVolume ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of the parent volume\. | String | 
|   [ ec2:Permission ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The type of permission for a resource\. | String | 
|   [ ec2:PlacementGroup ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of the placement group\. | String | 
|   [ ec2:PlacementGroupStrategy ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of the placement group strategy\. | String | 
|   [ ec2:ProductCode ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The product code of the product\. | String | 
|   [ ec2:Public ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | Whether the image is public\. | String | 
|   [ ec2:Region ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of the region\. | String | 
|   [ ec2:RequesterVpc ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of a requester VPC in a VPC peering connection\. | String | 
|   [ ec2:ReservedInstancesOfferingType ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-reserved-instances.html#ri-payment-options)  | The payment option for a Reserved Instance\. | String | 
|   [ ec2:ResourceTag/ ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The preface string for a tag key and value pair attached to a resource\. | String | 
|   [ ec2:ResourceTag/tag\-key ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | A tag key and value pair\. | String | 
|   [ ec2:RootDeviceType ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The root device type: ebs or instance\-store\. | String | 
|   [ ec2:SnapshotTime ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The snapshot creation time\. | String | 
|   [ ec2:SourceInstanceARN ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of the instance from which the request originated\. | ARN | 
|   [ ec2:Subnet ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of the subnet\. | String | 
|   [ ec2:Tenancy ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The tenancy of the instance or VPC\. | String | 
|   [ ec2:VolumeIops ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The number of input/output operations per second\. | Numeric | 
|   [ ec2:VolumeSize ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The size of the volume, in GiB\. | Numeric | 
|   [ ec2:VolumeType ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The name of the type of volume\. | String | 
|   [ ec2:Vpc ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html#amazon-ec2-keys)  | The ARN of the VPC\. | String | 