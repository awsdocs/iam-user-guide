# Actions, Resources, and Condition Keys for AWS Elemental MediaLive<a name="list_awselementalmedialive"></a>

AWS Elemental MediaLive \(service prefix: `medialive`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com//medialive/latest/ug/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com//medialive/latest/ug/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com//medialive/latest/ug/IAM_policies.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Elemental MediaLive](#awselementalmedialive-actions-as-permissions)
+ [Resources Defined by MediaLive](#awselementalmedialive-resources-for-iam-policies)
+ [Condition Keys for AWS Elemental MediaLive](#awselementalmedialive-policy-keys)

## Actions Defined by AWS Elemental MediaLive<a name="awselementalmedialive-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchUpdateSchedule ](https://docs.aws.amazon.com//medialive/latest/ug/batching-actions.html)  | Grants permission to add and remove actions from a channel's schedule\. | Write |  |  |  | 
|   [ CreateChannel ](https://docs.aws.amazon.com//medialive/latest/ug/creating-channel-scratch.html)  | Grants permission to create a channel | Write |  |  |  | 
|   [ CreateInput ](https://docs.aws.amazon.com//medialive/latest/ug/creating-input.html)  | Grants permission to create an input | Write |  |  |  | 
|   [ CreateInputSecurityGroup ](https://docs.aws.amazon.com//medialive/latest/ug/working-with-input-security-groups.html)  | Grants permission to create an input security group | Write |  |  |  | 
|   [ DeleteChannel ](https://docs.aws.amazon.com//medialive/latest/ug/editing-deleting-channel.html)  | Grants permission to delete a channel | Write |  |  |  | 
|   [ DeleteInput ](https://docs.aws.amazon.com//medialive/latest/ug/delete-input.html)  | Grants permission to delete an input | Write |  |  |  | 
|   [ DeleteInputSecurityGroup ](https://docs.aws.amazon.com//medialive/latest/ug/delete-input-security-group.html)  | Grants permission to delete an input security group | Write |  |  |  | 
|   [ DeleteReservation ](https://docs.aws.amazon.com//medialive/latest/ug/deleting-reservations.html)  | Grants permission to delete an expired reservation | Write |  |  |  | 
|   [ DescribeChannel ](https://docs.aws.amazon.com//medialive/latest/ug/viewing-channel-configuration.html)  | Grants permission to get details about a channel | Read |  |  |  | 
|   [ DescribeInput ](https://docs.aws.amazon.com//medialive/latest/ug/edit-input.html)  | Grants permission to describe an input | Read |  |  |  | 
|   [ DescribeInputSecurityGroup ](https://docs.aws.amazon.com//medialive/latest/ug/edit-input-security-group.html)  | Grants permission to describe an input security group | Read |  |  |  | 
|   [ DescribeOffering ](https://docs.aws.amazon.com//medialive/latest/ug/purchasing-reservations.html)  | Grants permission to get details about a reservation offering | Read |  |  |  | 
|   [ DescribeReservation ](https://docs.aws.amazon.com//medialive/latest/ug/view-reservations.html)  | Grants permission to get details about a reservation | Read |  |  |  | 
|   [ DescribeSchedule ](https://docs.aws.amazon.com//medialive/latest/ug/viewing-actions-schedule.html)  | Grants permission to view a list of actions scheduled on a channel\. | Read |  |  |  | 
|   [ ListChannels ](https://docs.aws.amazon.com//medialive/latest/ug/viewing-channel-configuration.html)  | Grants permission to list channels | List |  |  |  | 
|   [ ListInputSecurityGroups ](https://docs.aws.amazon.com//medialive/latest/ug/edit-input-security-group.html)  | Grants permission to list input security groups | List |  |  |  | 
|   [ ListInputs ](https://docs.aws.amazon.com//medialive/latest/ug/edit-input.html)  | Grants permission to list inputs | List |  |  |  | 
|   [ ListOfferings ](https://docs.aws.amazon.com//medialive/latest/ug/purchasing-reservations.html)  | Grants permission to list reservation offerings | List |  |  |  | 
|   [ ListReservations ](https://docs.aws.amazon.com//medialive/latest/ug/view-reservations.html)  | Grants permission to list reservations | List |  |  |  | 
|   [ PurchaseOffering ](https://docs.aws.amazon.com//medialive/latest/ug/purchasing-reservations.html)  | Grants permission to purchase a reservation offering | Write |  |  |  | 
|   [ StartChannel ](https://docs.aws.amazon.com//medialive/latest/ug/starting-stopping-deleting-a-channel.html)  | Grants permission to start a channel | Write |  |  |  | 
|   [ StopChannel ](https://docs.aws.amazon.com//medialive/latest/ug/starting-stopping-deleting-a-channel.html)  | Grants permission to stop a channel | Write |  |  |  | 
|   [ UpdateChannel ](https://docs.aws.amazon.com//medialive/latest/ug/editing-deleting-channel.html)  | Grants permission to update a channel | Write |  |  |  | 
|   [ UpdateInput ](https://docs.aws.amazon.com//medialive/latest/ug/edit-input.html)  | Grants permission to update an input | Write |  |  |  | 
|   [ UpdateInputSecurityGroup ](https://docs.aws.amazon.com//medialive/latest/ug/edit-input-security-group.html)  | Grants permission to update an input security group | Write |  |  |  | 

## Resources Defined by MediaLive<a name="awselementalmedialive-resources-for-iam-policies"></a>

AWS Elemental MediaLive has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Elemental MediaLive<a name="awselementalmedialive-policy-keys"></a>

MediaLive has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.