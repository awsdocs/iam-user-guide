# Creating IAM policies \(console\)<a name="access_policies_create-console"></a>

A [policy](access_policies.md) is an entity that, when attached to an identity or resource, defines their permissions\. You can use the AWS Management Console to create *customer managed policies* in IAM\. Customer managed policies are standalone policies that you administer in your own AWS account\. You can then attach the policies to identities \(users, groups, and roles\) in your AWS account\.

**Topics**
+ [Creating IAM policies \(console\)](#access_policies_create-start)
+ [Creating policies on the JSON tab](#access_policies_create-json-editor)
+ [Creating policies with the visual editor](#access_policies_create-visual-editor)
+ [Importing existing managed policies](#access_policies_create-copy)

## Creating IAM policies \(console\)<a name="access_policies_create-start"></a>

You can create a customer managed policy in the AWS Management Console using one of the following methods:
+ **[JSON](#access_policies_create-json-editor)** — Paste and customize a published [example identity\-based policy](access_policies_examples.md)\.
+ **[Visual editor](#access_policies_create-visual-editor)** — Construct a new policy from scratch in the visual editor\. If you use the visual editor, you do not have to understand JSON syntax\.
+ **[Import](#access_policies_create-copy)** — Import and customize a managed policy from within your account\. You can import an AWS managed policy or a customer managed policy that you previously created\.

The number and size of IAM resources in an AWS account are limited\. For more information, see [IAM and STS quotas](reference_iam-quotas.md)\.

## Creating policies on the JSON tab<a name="access_policies_create-json-editor"></a>

You can type or paste policies in JSON by choosing the **JSON** tab\. This method is useful for copying an [example policy](access_policies_examples.md) to use in your account\. Or, you can type your own JSON policy document in the JSON editor\. You can also use the **JSON** tab to toggle between the visual editor and JSON to compare the views\.

A JSON [policy](access_policies.md) document consists of one or more statements\. Each statement should contain all the actions that share the same effect \(`Allow` or `Deny`\) and support the same resources and conditions\. If one action requires you to specify all resources \(`"*"`\) and another action supports the Amazon Resource Name \(ARN\) of a specific resource, they must be in two separate JSON statements\. For details about ARN formats, see [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) in the *AWS General Reference Guide*\. For general information about IAM policies, see [Policies and permissions in IAM](access_policies.md)\. For information about the IAM policy language, see [IAM JSON policy reference](reference_policies.md)\.

**To use the JSON policy editor to create a policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane on the left, choose **Policies**\. 

1. Choose **Create policy**\.

1. Choose the **JSON** tab\.

1. Type or paste a JSON policy document\. For details about the IAM policy language, see [IAM JSON policy reference](reference_policies.md)\.

1. When you are finished, choose **Review policy**\. The [Policy Validator](access_policies_policy-validator.md) reports any syntax errors\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs anytime\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review policy** page, type a **Name** and a **Description** \(optional\) for the policy that you are creating\. Review the policy **Summary** to see the permissions that are granted by your policy\. Then choose **Create policy** to save your work\.

After you create a policy, you can attach it to your groups, users, or roles\. For more information, see [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md)\.

## Creating policies with the visual editor<a name="access_policies_create-visual-editor"></a>

The visual editor in the IAM console guides you through creating a policy without having to write JSON syntax\. To view an example of using the visual editor to create a policy, see [Controlling access to identities](access_controlling.md#access_controlling-identities)\.

**To use the visual editor to create a policy**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane on the left, choose **Policies**\. 

1. Choose **Create policy**\.

1. On the **Visual editor** tab, choose **Choose a service** and then choose an AWS service\. You can use the search box at the top to limit the results in the list of services\. You can choose only one service within a visual editor permission block\. To grant access to more than one service, add multiple permission blocks by choosing **Add additional permissions**\.

1. For **Actions**, choose the actions to add to the policy\. You can choose actions in the following ways:
   + Select the check box for all actions\.
   + Choose **add actions** to type the name of a specific action\. You can use wildcards \(`*`\) to specify multiple actions\.
   + Select one of the **Access level** groups to choose all actions for the access level \(for example, **Read**, **Write**, or **List**\)\.
   + Expand each of the **Access level** groups to choose individual actions\.

   By default, the policy that you are creating allows the actions that you choose\. To deny the chosen actions instead, choose **Switch to deny permissions**\. Because [IAM denies by default](reference_policies_evaluation-logic.md), we recommend as a security best practice that you allow permissions to only those actions and resources that a user needs\. You should create a JSON statement to deny permissions only if you want to override a permission separately allowed by another statement or policy\. We recommend that you limit the number of deny permissions to a minimum because they can increase the difficulty of troubleshooting permissions\.

1. For **Resources**, if the service and actions that you selected in the previous steps do not support choosing [specific resources](access_controlling.md#access_controlling-resources), all resources are allowed and you cannot edit this section\. 

   If you chose one or more actions that support [resource\-level permissions](access_controlling.md#access_controlling-resources), then the visual editor lists those resources\. You can then expand **Resources** to specify resources for your policy\. 

   You can specify resources in the following ways:
   + Choose **Add ARN** to specify resources by their Amazon Resource Names \(ARN\)\. You can use the visual ARN editor or list ARNs manually\. For more information about ARN syntax, see [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) in the *AWS General Reference Guide*\. For information about using ARNs in the `Resource` element of a policy, see [IAM JSON policy elements: Resource](reference_policies_elements_resource.md)\.
   + Choose **Any** next to a resource to grant permissions to any resources of that type\.
   + Choose **All resources** to choose all resources for the service\. 

1. \(Optional\) Choose **Specify request conditions \(optional\)** to add conditions to the policy that you are creating\. Conditions limit a JSON policy statement's effect\. For example, you can specify that a user is allowed to perform the actions on the resources only when that user's request happens within a certain time range\. You can also use commonly used conditions to limit whether a user must be authenticated using a multi\-factor authentication \(MFA\) device\. Or you can require that the request originate from within a certain range of IP addresses\. For lists of all of the context keys that you can use in a policy condition, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

   You can choose conditions in the following ways:
   + Use check boxes to select commonly used conditions\.
   + Choose **Add condition** to specify other conditions\. Choose the condition's **Condition Key**, **Qualifier**, and **Operator**, and then type a **Value**\. To add more than one value, choose **Add new value**\. You can consider the values as being connected by a logical "OR" operator\. When you are finished, choose **Add**\.

   To add more than one condition, choose **Add condition** again\. Repeat as needed\. Each condition applies only to this one visual editor permission block\. All the conditions must be true for the permission block to be considered a match\. In other words, consider the conditions to be connected by a logical "AND" operator\.

   For more information about the **Condition** element, see [IAM JSON policy elements: Condition](reference_policies_elements_condition.md) in the [IAM JSON policy reference](reference_policies.md)\.

1. To add more permission blocks, choose **Add additional permissions**\. For each block, repeat steps 2 through 5\.

1. When you are finished, choose **Review policy**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs anytime\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review policy** page, type a **Name** and a **Description** \(optional\) for the policy that you are creating\. Review the policy summary to make sure that you have granted the intended permissions, and then choose **Create policy** to save your new policy\.

After you create a policy, you can attach it to your groups, users, or roles\. For more information, see [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md)\.

## Importing existing managed policies<a name="access_policies_create-copy"></a>

An easy way to create a new policy is to import an existing managed policy within your account that has at least some of the permissions that you need\. You can then customize the policy to match it to your new requirements\.

You cannot import an inline policy\. To learn about the difference between managed and inline policies, see [Managed policies and inline policies](access_policies_managed-vs-inline.md)\.

**To import an existing managed policy in the visual editor**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane on the left, choose **Policies**\. 

1. Choose **Create policy**\.

1. Choose the **Visual editor** tab, and then on the right side of the page, choose **Import managed policy**\.

1. In the **Import managed policies** window, choose the managed policies that most closely match the policy that you want to include in your new policy\. You can use the **Filter** menu or type in the search box at the top to limit the results in the list of policies\.

1. Choose **Import**\.

   The imported policies are added in new permission blocks at the bottom of your policy\.

1. Use the **Visual editor** or choose **JSON** to customize your policy\. Then choose **Review policy**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs anytime\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review** page, type a **Name** and a **Description** \(optional\) for the policy that you are creating\. You cannot edit these settings later\. Review the policy **Summary** and then choose **Create policy** to save your work\.

**To import an existing managed policy in the **JSON** tab**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane on the left, choose **Policies**\. 

1. Choose **Create policy**\.

1. Choose the **JSON** tab, and then on the right side of the page, choose **Import managed policy**\.

1. In the **Import managed policies** window, choose the managed policies that most closely match the policy that you want to include in your new policy\. You can use the **Filter** menu or type in the search box at the top to limit the results in the list of policies\.

1. Choose **Import**\.

   Statements from the imported policies are added to the bottom of your JSON policy\.

1. Customize your policy in JSON, or choose the **Visual editor**\. Then choose **Review policy**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs anytime\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review policy** page, type a **Name** and a **Description** \(optional\) for the policy that you are creating\. You cannot edit these later\. Review the policy **Summary** and then choose **Create policy** to save your work\.

After you create a policy, you can attach it to your groups, users, or roles\. For more information, see [Adding and removing IAM identity permissions](access_policies_manage-attach-detach.md)\.