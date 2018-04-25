# Creating IAM Policies<a name="access_policies_create"></a>

A [policy](access_policies.md) is an entity that, when attached to an identity or resource, defines their permissions\. Policies are stored in AWS as JSON documents and are attached to principals as *identity\-based policies* in IAM\. You can attach an identity\-based policy to a principal \(or identity\), such as an IAM group, user, or role\. Identity\-based policies include AWS managed policies, customer managed policies, and [inline policies](access_policies_managed-vs-inline.md)\.

You can create a new IAM policy in the AWS Management Console using one of the following methods:
+ **Import** – You can import a managed policy within your account and then edit the policy to customize it to your specific requirements\. A managed policy can be an AWS managed policy, or a customer managed policy that you created previously\.
+ **Visual editor** – You can construct a new policy from scratch in the visual editor\. If you use the visual editor, you do not have to understand JSON syntax\.
+ **JSON** – In the **JSON** tab, you can create a policy using JSON syntax\. You can type a new JSON policy document or paste an [example policy](access_policies_examples.md)\.

You can create an inline policy in the AWS Management Console\. An inline policy is one that you create and embed directly to an IAM group, user, or role\. To learn more, see [Attaching IAM Policies \(Console\)](access_policies_manage-attach-detach.md#attach-managed-policy-console)\. You cannot create AWS managed policies\.

For information about policy size limitations and other quotas, see [Limitations on IAM Entities and Objects](reference_iam-limits.md)\.

**Topics**
+ [Create an IAM Policy \(Console\)](#access_policies_create-start)
+ [Import an Existing Managed Policy](#access_policies_create-copy)
+ [Create a Policy with the Visual Editor](#access_policies_create-visual-editor)
+ [Create a Policy on the JSON Tab](#access_policies_create-json-editor)
+ [Create IAM Policies \(AWS CLI or AWS API\)](#create-policies-cli-api)

## Create an IAM Policy \(Console\)<a name="access_policies_create-start"></a>

No matter which way you choose to create a policy, they all start the same way:

**To start creating a new policy \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane on the left, choose **Policies**\. 

   If this is your first time choosing **Policies**, the **Welcome to Managed Policies** page appears\. Choose **Get Started**\.

1. Choose **Create policy**\.

1. Choose one of the following ways to create the policy\. Then follow the steps in the corresponding procedure:
   + [Import an Existing Managed Policy](#access_policies_create-copy) 
   + [Create a Policy with the Visual Editor](#access_policies_create-visual-editor) 
   + [Create a Policy on the JSON Tab](#access_policies_create-json-editor) 

## Import an Existing Managed Policy<a name="access_policies_create-copy"></a>

An easy way to create a new policy is to import an existing managed policy within your account that has at least some of the permissions that you need\. You can then customize the policy to match it to your new requirements\.

You cannot import an inline policy\. To learn about the difference between managed and inline policies, see [Managed Policies and Inline Policies](access_policies_managed-vs-inline.md)\.

**To import an existing managed policy in the visual editor**

1. Start the **Create policy** wizard by following the steps in [Create an IAM Policy \(Console\)](#access_policies_create-start)\. Choose the **Visual editor** tab, and then on the right side of the page, choose **Import managed policy**\.

1. In the **Import managed policies** window, choose the managed policies that most closely match the policy that you want to include in your new policy\. You can use the **Filter** menu or type in the search box at the top to limit the results in the list of policies\.

1. Choose **Import**\.

   The imported policies are added in new permission blocks at the bottom of your policy\.

1. Use the **Visual editor** or choose **JSON** to customize your policy\. Then choose **Review policy**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy Restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review** page, type a **Name** and a **Description** \(optional\) for the policy that you are creating\. You cannot edit these fields later\. Review the policy **Summary** and then choose **Create policy** to save your work\.

**To import an existing managed policy in the **JSON** tab**

1. Start the **Create policy** wizard by following the steps in [Create an IAM Policy \(Console\)](#access_policies_create-start)\. Choose the **JSON** tab, and then on the right side of the page, choose **Import managed policy**\.

1. In the **Import managed policies** window, choose the managed policies that most closely match the policy that you want to include in your new policy\. You can use the **Filter** menu or type in the search box at the top to limit the results in the list of policies\.

1. Choose **Import**\.

   Statements from the imported policies are added to the bottom of your JSON policy\.

1. Customize your policy in JSON, or choose the **Visual editor**\. Then choose **Review policy**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy Restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review policy** page, type a **Name** and a **Description** \(optional\) for the policy that you are creating\. You cannot edit these later\. Review the policy **Summary** and then choose **Create policy** to save your work\.

After you create a policy, you can attach it to your groups, users, or roles\. For more information, see [Attaching and Detaching IAM Policies](access_policies_manage-attach-detach.md)\.

## Create a Policy with the Visual Editor<a name="access_policies_create-visual-editor"></a>

The visual editor in the IAM console guides you through creating a policy without having to write JSON syntax\. To view an example of using the visual editor to create a policy, see [Controlling Access to Identities](access_controlling.md#access_controlling-identities)\.

**To use the visual editor to create a policy**

1. Start the **Create Policy** wizard by following the steps in [Create an IAM Policy \(Console\)](#access_policies_create-start)\.

1. On the **Visual editor** tab, choose **Choose a service**\. Then choose an AWS service to add to the policy\. You can use the search box at the top to limit the results in the list of services\. You can choose only one service within a visual editor permission block\. To grant access to more than one service, add multiple permission blocks by choosing **Add additional permissions**\.

1. Choose **Select actions** and then choose the actions to add to the policy\. The visual editor shows the actions available in the service that you selected in the previous step\.

   You can choose actions in the following ways:
   + Use check boxes to select all actions for the service or all actions in one of the predefined **Access level** groups\.
   + Expand each of the **Access level** groups to choose individual actions\.
   + Choose **add actions** to type a specific action or use wildcards \(`*`\) to specify multiple actions\.

   By default, the policy that you are creating allows the actions that you choose\. To deny the chosen actions instead, choose **Switch to deny permissions**\. Because [IAM denies by default](reference_policies_evaluation-logic.md), we recommend as a security best practice that you allow permissions to only those actions and resources that a user needs\. This is sometimes called "whitelisting\." You should create a JSON statement to deny permissions \("blacklisting"\) only if you want to override a permission separately allowed by another statement or policy\. We recommend that you limit the number of deny permissions to a minimum because they can increase the difficulty of troubleshooting permissions\.

1. If the selected service and the actions that you selected in the previous steps do not support choosing [specific resources](access_controlling.md#access_controlling-resources), then **All resources** is selected for you\. In that case, you cannot edit this section\. 

   If you chose one or more actions that support [resource\-level permissions](access_controlling.md#access_controlling-resources), then the visual editor lists those resources You can then choose **Resources** to specify resources for your policy\. 

   You can choose resources in the following ways:
   + Choose **Add ARN** to provide the details about your resource\. Instead of typing a value, you can also choose **Any** to provide permissions for any value for the specified setting\. For example, if you selected the Amazon EC2 **Read** access level group, then the actions in your policy support the `instance` resource type\. You must provide the **Region**, **Account**, and **InstanceId** values for your resource\. If you provide your account ID but choose **Any** for the region and instance ID, then the policy grants permissions to any instance in your account\.
   + Choose **Add ARN** to specify resources by their [Amazon Resource Name \(ARN\)](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html)\. You can include a wildcard \(**\***\) in any field of the ARN \(between each pair of colons\)\. For more information, see [IAM JSON Policy Elements: Resource](reference_policies_elements_resource.md)\.
   + Choose **Any** from the far right of the resource section to grant permissions to any resources of a particular type\.
   + Choose **All resources** to choose all resources for that service\. 

1. \(Optional\) Choose **Specify request conditions \(optional\)** to add conditions to the policy that you are creating\. Conditions limit a JSON policy statement's effect\. For example, you can specify that a user is allowed to perform the actions on the resources only when that user's request happens within a certain time range\. You can also use commonly used conditions to limit whether a user must be authenticated using a multi\-factor authentication \(MFA\) device, or if the request must originate from within a certain range of IP addresses\. For lists of all of the context keys that you can use in a policy condition, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.md)\.

   You can choose conditions in the following ways:
   + Use check boxes to select commonly used conditions\.
   + Choose **Add condition** to specify other conditions\. Choose the condition's **Condition Key**, **Qualifier**, and **Operator**, and then type a **Value**\. To add more than one value, choose **Add new value**\. You can consider the values as being connected by a logical "OR" operator\. When you are finished, choose **Add**\.

   To add more than one condition, choose **Add condition** again\. Repeat as needed\. Each condition applies only to this one visual editor permission block\. All the conditions must be true for the permission block to be considered a match\. In other words, consider the conditions to be connected by a logical "AND" operator\.

   For more information about the **Condition** element, see [IAM JSON Policy Elements: Condition](reference_policies_elements_condition.md) in the [IAM JSON Policy Reference](reference_policies.md)\.

1. To add more permission blocks, choose **Add additional permissions**\. For each block, repeat steps 2 through 5\.

1. When you are finished, choose **Review policy**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy Restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review policy** page, type a **Name** and a **Description** \(optional\) for the policy that you are creating\. Review the policy summary to make sure that you have granted the intended permissions, and then choose **Create policy** to save your new policy\.

After you create a policy, you can attach it to your groups, users, or roles\. For more information, see [Attaching and Detaching IAM Policies](access_policies_manage-attach-detach.md)\.

## Create a Policy on the JSON Tab<a name="access_policies_create-json-editor"></a>

You can type or paste policies in JSON by choosing the **JSON** tab\. This method is useful for copying an [example policy](access_policies_examples.md) to use in your account\. Or, you can type your own JSON policy document in the JSON editor\. You can also use the **JSON** tab to toggle between the visual editor and JSON to compare the views\.

A JSON [policy](access_policies.md) document consists of one or more statements\. Each statement should contain all the actions that share the same effect \(`Allow` or `Deny`\) and support the same resources and conditions\. If one action requires you to specify all resources \(`"*"`\) and another action supports the [Amazon Resource Name \(ARN\)](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of a specific resource, they must be in two separate JSON statements\. For general information about IAM policies, see [IAM Policies](access_policies.md)\. For information about the IAM policy language, see [IAM JSON Policy Reference](reference_policies.md)\.

**To use the JSON policy editor to create a policy**

1. Start the **Create Policy** wizard by following the steps in [Create an IAM Policy \(Console\)](#access_policies_create-start)\.

1. Choose the **JSON** tab\.

1. Type or paste a JSON policy document\. For details about the IAM policy language, see [IAM JSON Policy Reference](reference_policies.md)\.

1. When you are finished, choose **Review policy**\. The [Policy Validator](access_policies_policy-validator.md) reports any syntax errors\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy Restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review policy** page, type a **Name** and a **Description** \(optional\) for the policy that you are creating\. Review the policy **Summary** to see the permissions that are granted by your policy\. Then choose **Create policy** to save your work\.

After you create a policy, you can attach it to your groups, users, or roles\. For more information, see [Attaching and Detaching IAM Policies](access_policies_manage-attach-detach.md)\.

## Create IAM Policies \(AWS CLI or AWS API\)<a name="create-policies-cli-api"></a>

You can create an IAM policy or an inline policy using the AWS Command Line Interface \(AWS CLI\) or the AWS API\.

**To create a customer managed policy \(AWS CLI or API\)**
+ AWS CLI: [create\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/create-policy.html)
+ IAM API: [CreatePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicy.html)

**To create an inline policy for a principal entity \(group, user, or role\) \(AWS CLI or API\)**
+ AWS CLI:
  + [put\-group\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-group-policy.html)
  + [put\-role\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-role-policy.html)
  + [put\-user\-policy](http://docs.aws.amazon.com/cli/latest/reference/iam/put-user-policy.html)
+ IAM API:
  + [PutGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutGroupPolicy.html)
  + [PutRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutRolePolicy.html)
  + [PutUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_PutUserPolicy.html)

**Note**  
You can embed an inline policy for a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)* only in the service that depends on the role\. See the [AWS documentation](http://docs.aws.amazon.com/) for your service to see whether it supports this feature\.