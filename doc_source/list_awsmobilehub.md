# Actions, Resources, and Condition Keys for AWS Mobile Hub<a name="list_awsmobilehub"></a>

AWS Mobile Hub \(service prefix: `mobilehub`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/reference-mobile-hub-iam-auth-access.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Mobile Hub](#awsmobilehub-actions-as-permissions)
+ [Resources Defined by Mobile Hub](#awsmobilehub-resources-for-iam-policies)
+ [Condition Keys for AWS Mobile Hub](#awsmobilehub-policy-keys)

## Actions Defined by AWS Mobile Hub<a name="awsmobilehub-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Create a project | Write |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Enable AWS Mobile Hub in the account by creating the required service role | Write |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Delete the specified project | Write | [project\*](#awsmobilehub-project)  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Delete a saved snapshot of project configuration | Write |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Deploy changes to the specified stage | Write |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Describe the download bundle | Read |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Export the download bundle | Read |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Export the project configuration | Read | [project\*](#awsmobilehub-project)  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Generate project parameters required for code generation | Write | [project\*](#awsmobilehub-project)  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Get project configuration and resources | Read | [project\*](#awsmobilehub-project)  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Fetch the previously exported project configuration snapshot | Read |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Create a new project from the previously exported project configuration | Write |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Install a bundle in the project deployments S3 bucket | Write |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | List the available SaaS \(Software as a Service\) connectors | List |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | List available features | List |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | List available regions for projects | List |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | List the available download bundles | List |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | List saved snapshots of project configuration | List |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | List projects | List |  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Synchronize state of resources into project | Write | [project\*](#awsmobilehub-project)  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Update project | Write | [project\*](#awsmobilehub-project)  |  |  | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/managed-policies.html) | Verify AWS Mobile Hub is enabled in the account | Read |  |  |  | 

## Resources Defined by Mobile Hub<a name="awsmobilehub-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsmobilehub-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/mobile-hub/latest/developerguide/reference-mobile-hub-iam-managed-policies.html](http://docs.aws.amazon.com/mobile-hub/latest/developerguide/reference-mobile-hub-iam-managed-policies.html) | arn:$\{Partition\}:mobilehub:$\{Region\}:$\{Account\}:project/$\{ProjectId\} |  | 

## Condition Keys for AWS Mobile Hub<a name="awsmobilehub-policy-keys"></a>

Mobile Hub has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.