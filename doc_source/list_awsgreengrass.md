# Actions, Resources, and Condition Keys for AWS Greengrass<a name="list_awsgreengrass"></a>

AWS Greengrass \(service prefix: `greengrass`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/greengrass/latest/developerguide/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/greengrass/latest/apireference/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/greengrass/latest/developerguide/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Greengrass](#awsgreengrass-actions-as-permissions)
+ [Resources Defined by Greengrass](#awsgreengrass-resources-for-iam-policies)
+ [Condition Keys for AWS Greengrass](#awsgreengrass-policy-keys)

## Actions Defined by AWS Greengrass<a name="awsgreengrass-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ AssociateRoleToGroup ](https://docs.aws.amazon.com/greengrass/latest/apireference/associateroletogroup-put.html)  | Associates a role with a group | Write |  |  |  | 
|   [ AssociateServiceRoleToAccount ](https://docs.aws.amazon.com/greengrass/latest/apireference/associateserviceroletoaccount-put.html)  | Associates a role with the account\. AWS Greengrass uses the role to access your Lambda functions and AWS IoT resources\. | Permissions management |  |  |  | 
|   [ CreateCoreDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/createcoredefinition-post.html)  | Creates a core definition\. | Write |  |  |  | 
|   [ CreateCoreDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/createcoredefinitionversion-post.html)  | Creates a version of a core definition that has already been defined\. AWS Greengrass Groups must each contain exactly 1 AWS Greengrass Core\. | Write |  |  |  | 
|   [ CreateDeployment ](https://docs.aws.amazon.com/greengrass/latest/apireference/createdeployment-post.html)  | Creates a deployment\. | Write |  |  |  | 
|   [ CreateDeviceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/createdevicedefinition-post.html)  | Creates a device definition\. | Write |  |  |  | 
|   [ CreateDeviceDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/createdevicedefinitionversion-post.html)  | Creates a version of a device definition that has already been defined\. | Write |  |  |  | 
|   [ CreateFunctionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/createfunctiondefinition-post.html)  | Creates a Lambda function definition which contains a list of Lambda functions and their configurations to be used in a group\.  | Write |  |  |  | 
|   [ CreateFunctionDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/createfunctiondefinitionversion-post.html)  | Create a version of a Lambda function definition that has already been defined\. | Write |  |  |  | 
|   [ CreateGroup ](https://docs.aws.amazon.com/greengrass/latest/apireference/creategroup-post.html)  | Creates a group\. You may provide the group configuration data now or use CreateGroupVersion later | Write |  |  |  | 
|   [ CreateGroupCertificateAuthority ](https://docs.aws.amazon.com/greengrass/latest/apireference/creategroupcertificateauthority-post.html)  | Creates a CA for the group\. If a CA already exists, it will rotate the existing CA\. | Write |  |  |  | 
|   [ CreateGroupVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/creategroupversion-post.html)  | Creates a version of a group which has already been defined\. | Write |  |  |  | 
|   [ CreateLoggerDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/createloggerdefinition-post.html)  | Creates a logger definition\. | Write |  |  |  | 
|   [ CreateLoggerDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/createloggerdefinitionversion-post.html)  | Creates a version of a logger definition that has already been defined\. | Write |  |  |  | 
|   [ CreateResourceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/createresourcedefinition-post.html)  | Creates a resource definition which contains a list of resources to be used in a group\. You can create an initial version of the definition by providing a list of resources now, or use ``CreateResourceDefinitionVersion`` later\. | Write |  |  |  | 
|   [ CreateResourceDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/createresourcedefinitionversion-post.html)  | Create a version of a resource definition that has already been defined\. | Write |  |  |  | 
|   [ CreateSoftwareUpdateJob ](https://docs.aws.amazon.com/greengrass/latest/apireference/createsoftwareupdatejob-post.html)  | Creates an Iot Job that will trigger your Greengrass Cores to update the software they are running\. | Write |  |  |  | 
|   [ CreateSubscriptionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/createsubscriptiondefinition-post.html)  | Creates a subscription definition\. | Write |  |  |  | 
|   [ CreateSubscriptionDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/createsubscriptiondefinitionversion-post.html)  | Creates a version of a subscription definition which has already been defined\. | Write |  |  |  | 
|   [ DeleteCoreDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/deletecoredefinition-delete.html)  | Deletes a core definition\. The core definition must not have been used in a deployment\. | Write |  |  |  | 
|   [ DeleteDeviceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/deletedevicedefinition-delete.html)  | Deletes a device definition\. The device definition must not have been used in a deployment\. | Write |  |  |  | 
|   [ DeleteFunctionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/deletefunctiondefinition-delete.html)  | Deletes a Lambda function definition\. The Lambda function definition must not have been used in a deployment\. | Write |  |  |  | 
|   [ DeleteGroup ](https://docs.aws.amazon.com/greengrass/latest/apireference/deletegroup-delete.html)  | Deletes a group\. The group must not have been used in deployment\. | Write |  |  |  | 
|   [ DeleteLoggerDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/deleteloggerdefinition-delete.html)  | Deletes a logger definition\. The logger definition must not have been used in a deployment\. | Write |  |  |  | 
|   [ DeleteResourceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/deleteresourcedefinition-delete.html)  | Deletes a resource definition\. | Write |  |  |  | 
|   [ DeleteSubscriptionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/deletesubscriptiondefinition-delete.html)  | Deletes a subscription definition\. The subscription definition must not have been used in a deployment\. | Write |  |  |  | 
|   [ DisassociateRoleFromGroup ](https://docs.aws.amazon.com/greengrass/latest/apireference/disassociaterolefromgroup-delete.html)  | Disassociates the role from a group\. | Write |  |  |  | 
|   [ DisassociateServiceRoleFromAccount ](https://docs.aws.amazon.com/greengrass/latest/apireference/disassociateservicerolefromaccount-delete.html)  | Disassociates the service role from the account\. Without a service role, deployments will not work\. | Write |  |  |  | 
|   [ GetAssociatedRole ](https://docs.aws.amazon.com/greengrass/latest/apireference/getassociatedrole-get.html)  | Retrieves the role associated with a particular group\. | Read |  |  |  | 
|   [ GetConnectivityInfo ](https://docs.aws.amazon.com/greengrass/latest/apireference/getconnectivityinfo-get.html)  | Retrieves the connectivity information for a core\. | Read |  |  |  | 
|   [ GetCoreDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/getcoredefinition-get.html)  | Retrieves information about a core definition version\. | Read |  |  |  | 
|   [ GetCoreDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/getcoredefinitionversion-get.html)  | Retrieves information about a core definition version\. | Read |  |  |  | 
|   [ GetDeploymentStatus ](https://docs.aws.amazon.com/greengrass/latest/apireference/getdeploymentstatus-get.html)  | Returns the status of a deployment\. | Read |  |  |  | 
|   [ GetDeviceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/getdevicedefinition-get.html)  | Retrieves information about a device definition\. | Read |  |  |  | 
|   [ GetDeviceDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/getdevicedefinitionversion-get.html)  | Retrieves information about a device definition\. | Read |  |  |  | 
|   [ GetFunctionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/getfunctiondefinition-get.html)  | Retrieves information about a Lambda function definition, such as its creation time and latest version\. | Read |  |  |  | 
|   [ GetFunctionDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/getfunctiondefinitionversion-get.html)  | Retrieves information about a Lambda function definition version, such as which Lambda functions are included in the version and their configurations\. | Read |  |  |  | 
|   [ GetGroup ](https://docs.aws.amazon.com/greengrass/latest/apireference/getgroup-get.html)  | Retrieves information about a group\. | Read |  |  |  | 
|   [ GetGroupCertificateAuthority ](https://docs.aws.amazon.com/greengrass/latest/apireference/getgroupcertificateauthority-get.html)  | Retreives the CA associated with a group\. Returns the public key of the CA\. | Read |  |  |  | 
|   [ GetGroupCertificateConfiguration ](https://docs.aws.amazon.com/greengrass/latest/apireference/getgroupcertificateconfiguration-get.html)  | Retrieves the current configuration for the CA used by the group\. | Read |  |  |  | 
|   [ GetGroupVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/getgroupversion-get.html)  | Retrieves information about a group version\. | Read |  |  |  | 
|   [ GetLoggerDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/getloggerdefinition-get.html)  | Retrieves information about a logger definition\. | Read |  |  |  | 
|   [ GetLoggerDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/getloggerdefinitionversion-get.html)  | Retrieves information about a logger definition version | Read |  |  |  | 
|   [ GetResourceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/getresourcedefinition-get.html)  | Retrieves information about a resource definition, such as its creation time and latest version\. | Read |  |  |  | 
|   [ GetResourceDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/getresourcedefinitionversion-get.html)  | Retrieves information about a resource definition version, such as which resources are included in the version\. | Read |  |  |  | 
|   [ GetServiceRoleForAccount ](https://docs.aws.amazon.com/greengrass/latest/apireference/getserviceroleforaccount-get.html)  | Retrieves the service role that is attached to the account\. | Read |  |  |  | 
|   [ GetSubscriptionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/getsubscriptiondefinition-get.html)  | Retrieves information about a subscription definition\. | Read |  |  |  | 
|   [ GetSubscriptionDefinitionVersion ](https://docs.aws.amazon.com/greengrass/latest/apireference/getsubscriptiondefinitionversion-get.html)  | Retrieves information about a subscription definition version\. | Read |  |  |  | 
|   [ ListCoreDefinitionVersions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listcoredefinitionversions-get.html)  | Lists versions of a core definition\. | List |  |  |  | 
|   [ ListCoreDefinitions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listcoredefinitions-get.html)  | Retrieves a list of core definitions\. | List |  |  |  | 
|   [ ListDeployments ](https://docs.aws.amazon.com/greengrass/latest/apireference/listdeployments-get.html)  | Returns a history of deployments for the group\. | List |  |  |  | 
|   [ ListDeviceDefinitionVersions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listdevicedefinitionversions-get.html)  | Lists the versions of a device definition\. | List |  |  |  | 
|   [ ListDeviceDefinitions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listdevicedefinitions-get.html)  | Retrieves a list of device definitions\. | List |  |  |  | 
|   [ ListFunctionDefinitionVersions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listfunctiondefinitionversions-get.html)  | Lists the versions of a Lambda function definition\. | List |  |  |  | 
|   [ ListFunctionDefinitions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listfunctiondefinitions-get.html)  | Retrieves a list of Lambda function definitions\. | List |  |  |  | 
|   [ ListGroupCertificateAuthorities ](https://docs.aws.amazon.com/greengrass/latest/apireference/listgroupcertificateauthorities-get.html)  | Retrieves the current CAs for a group\. | List |  |  |  | 
|   [ ListGroupVersions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listgroupversions-get.html)  | Lists the versions of a group\. | List |  |  |  | 
|   [ ListGroups ](https://docs.aws.amazon.com/greengrass/latest/apireference/listgroups-get.html)  | Retrieves a list of groups\. | List |  |  |  | 
|   [ ListLoggerDefinitionVersions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listloggerdefinitionversions-get.html)  | Lists the versions of a logger definition\. | List |  |  |  | 
|   [ ListLoggerDefinitions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listloggerdefinitions-get.html)  | Retrieves a list of logger definitions\. | List |  |  |  | 
|   [ ListResourceDefinitionVersions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listresourcedefinitionversions-get.html)  | Lists the versions of a resource definition\. | List |  |  |  | 
|   [ ListResourceDefinitions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listresourcedefinitions-get.html)  | Retrieves a list of resource definitions\. | List |  |  |  | 
|   [ ListSubscriptionDefinitionVersions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listsubscriptiondefinitionversions-get.html)  | Lists the versions of a subscription definition\. | List |  |  |  | 
|   [ ListSubscriptionDefinitions ](https://docs.aws.amazon.com/greengrass/latest/apireference/listsubscriptiondefinitions-get.html)  | Retrieves a list of subscription definitions\. | List |  |  |  | 
|   [ ResetDeployments ](https://docs.aws.amazon.com/greengrass/latest/apireference/resetdeployments-post.html)  | Resets a group's deployments\. | Write |  |  |  | 
|   [ UpdateConnectivityInfo ](https://docs.aws.amazon.com/greengrass/latest/apireference/updateconnectivityinfo-put.html)  | Updates the connectivity information for the core\. Any devices that belong to the group which has this core will receive this information in order to find the location of the core and connect to it\. | Write |  |  |  | 
|   [ UpdateCoreDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/updatecoredefinition-put.html)  | Updates a core definition\. | Write |  |  |  | 
|   [ UpdateDeviceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/updatedevicedefinition-put.html)  | Updates a device definition\. | Write |  |  |  | 
|   [ UpdateFunctionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/updatefunctiondefinition-put.html)  | Updates a Lambda function definition\. | Write |  |  |  | 
|   [ UpdateGroup ](https://docs.aws.amazon.com/greengrass/latest/apireference/updategroup-put.html)  | Updates a group\. | Write |  |  |  | 
|   [ UpdateGroupCertificateConfiguration ](https://docs.aws.amazon.com/greengrass/latest/apireference/updategroupcertificateconfiguration-put.html)  | Updates the Certificate expiry time for a group\. | Write |  |  |  | 
|   [ UpdateLoggerDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/updateloggerdefinition-put.html)  | Updates a logger definition\. | Write |  |  |  | 
|   [ UpdateResourceDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/updateresourcedefinition-put.html)  | Updates a resource definition\. | Write |  |  |  | 
|   [ UpdateSubscriptionDefinition ](https://docs.aws.amazon.com/greengrass/latest/apireference/updatesubscriptiondefinition-put.html)  | Updates a subscription definition\. | Write |  |  |  | 

## Resources Defined by Greengrass<a name="awsgreengrass-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsgreengrass-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   artifact  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}/deployments/$\{DeploymentId\}/artifacts/lambda/$\{ArtifactId\}  |  | 
|   [ certficateAuthority ](https://docs.aws.amazon.com/greengrass/latest/developerguide/gg-sec.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}/certificateauthorities/$\{CertificateAuthorityId\}  |  | 
|   definition  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/$\{DefinitionName\}/$\{DefinitionId\}  |  | 
|   definitionVersion  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/$\{DefinitionName\}/$\{DefinitionId\}/versions/$\{VersionId\}  |  | 
|   [ deployment ](https://docs.aws.amazon.com/greengrass/latest/developerguide/create-deployment.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}/deployments/$\{DeploymentId\}  |  | 
|   [ group ](https://docs.aws.amazon.com/greengrass/latest/developerguide/create-gg-group.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}  |  | 
|   [ groupVersion ](https://docs.aws.amazon.com/greengrass/latest/developerguide/update-group.html)  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/groups/$\{GroupId\}/versions/$\{VersionId\}  |  | 
|   resourceDefinition  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/resources/$\{ResourceDefinitionId\}  |  | 
|   resourceDefinitionVersion  |  arn:$\{Partition\}:greengrass:$\{Region\}:$\{Account\}:/greengrass/definition/resources/$\{ResourceDefinitionId\}/versions/$\{VersionId\}  |  | 

## Condition Keys for AWS Greengrass<a name="awsgreengrass-policy-keys"></a>

Greengrass has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.