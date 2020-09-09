# Troubleshooting IAM policies<a name="troubleshoot_policies"></a>

A [policy](access_policies.md) is an entity in AWS that, when attached to an identity or resource, defines their permissions\. AWS evaluates these policies when a principal, such as a user, makes a request\. Permissions in the policies determine whether the request is allowed or denied\. Policies are stored in AWS as JSON documents that are attached to principals as *identity\-based policies* or to resources as *resource\-based policies*\. You can attach an identity\-based policy to a principal \(or identity\), such as an IAM group, user, or role\. Identity\-based policies include AWS managed policies, customer managed policies, and inline policies\. You can create and edit customer managed policies in the AWS Management Console using the **Visual editor** tab or the **JSON** tab\. When you view a policy in the AWS Management Console, you can see a summary of the permissions that are granted by that policy\. You can use the visual editor and policy summaries to help you diagnose and fix common errors encountered while managing IAM policies\.

Keep in mind that all IAM policies are stored using syntax that begins with the rules of [JavaScript Object Notation](http://www.json.org) \(JSON\)\. You do not have to understand this syntax to create or manage your policies\. You can create and edit a policy using the visual editor in the AWS Management Console\. To learn more about JSON syntax in IAM policies, see [Grammar of the IAM JSON policy language ](reference_policies_grammar.md)\.

**Troubleshooting IAM Policy Topics**
+ [Troubleshoot using the visual editor](#troubleshoot_policies-viseditor)
  + [Policy restructuring](#troubleshoot_viseditor-restructure)
  + [Choosing a resource ARN in the visual editor](#troubleshoot_policies-resource-arn)
  + [Denying permissions in the visual editor](#troubleshoot_policies-switch-deny)
  + [Specifying multiple services in the visual editor](#troubleshoot_policies-multiple-services)
  + [Reducing the size of your policy in the visual editor](#troubleshoot_policy-size)
  + [Fixing unrecognized services, actions, or resource types in the visual editor](#troubleshoot_policies-unrecognized-visual)
+ [Troubleshoot using policy summaries](#troubleshoot_policies-polsum)
  + [Missing policy summary](#missing-policy-summary)
  + [Policy summary includes unrecognized services, actions, or resource types](#unrecognized-services-actions)
  + [Service does not support IAM policy summaries](#unsupported-services-actions)
  + [My policy does not grant the expected permissions](#policy-summary-not-grant-permissions)
+ [Troubleshoot policy management](#troubleshoot_policies-policy-manage)
  + [Attaching or detaching a policy in an IAM account](#troubleshoot_roles_cant-attach-detach-policy)
  + [Changing policies for your IAM identities based on their activity](#troubleshoot_change-policies-based-on-activity)
+ [Troubleshoot JSON policy documents](#troubleshoot_policies-json)
  + [More than one JSON policy object](#morethanonepolicyblock)
  + [More than one JSON statement element](#morethanonestatement)
  + [More than one effect, action, or resource element in a JSON statement element](#duplicateelement)
  + [Missing JSON version element](#missing-version)

## Troubleshoot using the visual editor<a name="troubleshoot_policies-viseditor"></a>

When you create or edit a customer managed policy, you can use information in the **Visual editor** tab to help you troubleshoot errors in your policy\. To view an example of using the visual editor to create a policy, see [Controlling access to identities](access_controlling.md#access_controlling-identities)\.

### Policy restructuring<a name="troubleshoot_viseditor-restructure"></a>

When you create a policy, AWS validates, processes, and transforms the policy before storing it\. When AWS returns the policy in response to a user query or displays it in the console, AWS transforms the policy back into a human\-readable format without changing the permissions granted by the policy\. This can result in differences in what you see in the policy visual editor or **JSON** tab: Visual editor permission blocks can be added, removed, or reordered, and content within a block can be optimized\. In the **JSON** tab, insignificant white space can be removed, and elements within JSON maps can be reordered\. In addition, AWS account IDs within the principal elements can be replaced by the ARN of the AWS account root user\. Because of these possible changes, you should not compare JSON policy documents as strings\. 

When you create a customer managed policy in the AWS Management Console, you can choose to work entirely in the **JSON** tab\. If you never make any changes in the **Visual editor** tab and choose **Review policy** from the **JSON** tab, the policy is less likely to be restructured\. However, if you create a policy and use the **Visual editor** tab to make any modifications, or if you choose **Review policy** from the **Visual editor** tab, then IAM might restructure the policy to optimize its appearance in the visual editor\. 

This restructuring exists only in your editing session and is not saved automatically\.

If your policy is restructured in your editing session, IAM determines whether to save the restructuring based on the following situations:


| On this tab | If you edit your policy | And then choose ***Review policy*** from this tab | When you choose ***Save changes*** | 
| --- | --- | --- | --- | 
| Visual editor | Edited | Visual editor | The policy is restructured | 
| Visual editor | Edited | JSON | The policy is restructured | 
| Visual editor | Not Edited | Visual editor | The policy is restructured | 
| JSON | Edited | Visual editor | The policy is restructured | 
| JSON | Edited | JSON | The policy structure is not changed | 
| JSON | Not Edited | JSON | The policy structure is not changed | 

IAM might restructure complex policies or policies that have permission blocks or statements that allow multiple services, resource types, or condition keys\.

### Choosing a resource ARN in the visual editor<a name="troubleshoot_policies-resource-arn"></a>

When you create or edit a policy using the visual editor, you must first choose a service, and then choose actions from that service\. If the service and actions that you selected support choosing [specific resources](access_controlling.md#access_controlling-resources), then the visual editor lists the supported resource types\. You can then choose **Add ARN** to provide the details about your resource\. You can choose from the following options for adding an ARN for a resource type\.
+ **Use the ARN builder** – Based on the resource type, you might see different fields to build your ARN\. You can also choose **Any** to provide permissions for any value for the specified setting\. For example, if you selected the Amazon EC2 **Read** access level group, then the actions in your policy support the `instance` resource type\. You must provide the **Region**, **Account**, and **InstanceId** values for your resource\. If you provide your account ID but choose **Any** for the Region and instance ID, then the policy grants permissions to any instance in your account\.
+ **Type or paste the ARN** – You can specify resources by their [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns)\. You can include a wildcard character \(**\***\) in any field of the ARN \(between each pair of colons\)\. For more information, see [IAM JSON policy elements: Resource](reference_policies_elements_resource.md)\.

### Denying permissions in the visual editor<a name="troubleshoot_policies-switch-deny"></a>

By default, the policy that you create using the visual editor allows the actions that you choose\. To deny the chosen actions instead, choose **Switch to deny permissions**\. Because requests are *denied by default*, we recommend as a security best practice that you allow permissions to only those actions and resources that a user needs\. This is sometimes called "whitelisting\." You should create a statement to deny permissions \("blacklisting"\) only if you want to override a permission separately that is allowed by another statement or policy\. We recommend that you limit the number of deny permissions to a minimum because they can increase the difficulty of troubleshooting permissions\. For more information about how IAM evaluates policy logic, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.

**Note**  
By default, only the AWS account root user has access to all the resources in that account\. So if you are not signed in as the root user, you must have permissions granted by a policy\.

### Specifying multiple services in the visual editor<a name="troubleshoot_policies-multiple-services"></a>

When you use the visual editor to construct a policy, you can select only one service at a time\. This is a best practice because the visual editor then allows you to choose from the actions for that one service\. You then choose from the resources supported by that service and the selected actions\. This makes it easier to create and troubleshoot your policy\. 

If you are familiar with the JSON syntax, you can also use a wildcard character \(\*\) to manually specify multiple services\. For example, type **Code\*** to provide permissions for all services beginning with `Code`, such as `CodeBuild` and `CodeCommit`\. However, you must then type the actions and resource ARNs to complete your policy\. Additionally, when you save your policy, it might be [restructured](#troubleshoot_viseditor-restructure) to include each service in a separate permission block\.

Alternatively, to use JSON syntax \(such as wildcards\) for services, create, edit, and save your policy using the **JSON** tab\.

### Reducing the size of your policy in the visual editor<a name="troubleshoot_policy-size"></a>

When you use the visual editor to create a policy, IAM creates a JSON document to store your policy\. You can view this document by switching to the **JSON** tab\. If this JSON document exceeds the size limit of a policy, the visual editor displays an error message and does not allow you to review and save your policy\. To view the IAM limitation on the size of a managed policy, see [IAM and STS character quotas](reference_iam-quotas.md#reference_iam-quotas-entity-length)\. 

To reduce the size of your policy in the visual editor, edit your policy or move permission blocks to another policy\. The error message includes the number of characters that your policy document contains, and you can use this information to help you reduce the size of your policy\.

### Fixing unrecognized services, actions, or resource types in the visual editor<a name="troubleshoot_policies-unrecognized-visual"></a>

When you create or edit a policy in the visual editor, you might see a warning that your policy includes an unrecognized service, action, or resource type\.

**Note**  
IAM reviews service names, actions, and resource types for services that support policy summaries\. However, your policy summary might include a resource value or condition that does not exist\. Always test your policies with the [policy simulator](access_policies_testing-policies.md)\.

If your policy includes unrecognized services, actions or resource types, one of the following errors has occurred:
+ **Preview service** – Services that are in preview do not support the visual editor\. If you are participating in the preview, you can ignore the warning and continue, though you must manually type the actions and resource ARNs to complete your policy\. Alternatively, you can choose the **JSON** tab to type or paste a JSON policy document\.
+ **Custom service** – Custom services do not support the visual editor\. If you are using a custom service, you can ignore the warning and continue, though you must manually type the actions and resource ARNs to complete your policy\. Alternatively, you can choose the **JSON** tab to type or paste a JSON policy document\.
+ **Service does not support the visual editor** – If your policy includes a generally available \(GA\) service that does not support the visual editor, you can ignore the warning and continue, though you must manually type the actions and resource ARNs to complete your policy\. Alternatively, you can choose the **JSON** tab to type or paste a JSON policy document\. 

  Generally available services are services that are released publicly and are not preview or custom services\. If an unrecognized service is generally available and the name is spelled correctly, then the service does not support the visual editor\. To learn how to request visual editor or policy summary support for a GA service, see [Service does not support IAM policy summaries](#unsupported-services-actions)\.
+ **Action does not support the visual editor** – If your policy includes a supported service with an unsupported action, you can ignore the warning and continue, though you must manually type the resource ARNs to complete your policy\. Alternatively, you can choose the **JSON** tab to type or paste a JSON policy document\.

  If your policy includes a supported service with an unsupported action, then the service does not fully support the visual editor\. To learn how to request visual editor or policy summary support for a GA service, see [Service does not support IAM policy summaries](#unsupported-services-actions)\.
+ **Resource type does not support the visual editor** – If your policy includes a supported action with an unsupported resource type, you can ignore the warning and continue\. However, IAM cannot confirm that you have included resources for all of your selected actions, and you might see additional warnings\.
+ **Typo** – When you manually type a service, action, or resource in the visual editor, you can create a policy that includes a typo\. As a best practice, use the visual editor by selecting from the list of services and actions, and then complete the resource section according to the prompts\. However, if a service does not fully support the visual editor, you might have to manually type parts of your policy\. 

  If you are certain that your policy contains none of the errors above, then your policy might include a typo\. Check for misspelled service, action, and resource type names\. For example, you might use `s2` instead of `s3` and `ListMyBuckets` instead of `ListAllMyBuckets`\. Another common action typo is the inclusion of unnecessary text in ARNs, such as `arn:aws:s3: : :*`, or missing colons in actions, such as `iam.CreateUser`\. You can evaluate a policy that might include typos by choosing **Review policy** to review the policy summary and confirm whether the policy provides the permissions you intended\.

## Troubleshoot using policy summaries<a name="troubleshoot_policies-polsum"></a>

You can diagnose and resolve issues related to policy summaries\.

### Missing policy summary<a name="missing-policy-summary"></a>

The IAM console includes *policy summary* tables that describe the access level, resources, and conditions that are allowed or denied for each service in a policy\. Policies are summarized in three tables: the [policy summary](access_policies_understand-policy-summary.md), the [service summary](access_policies_understand-service-summary.md), and the [action summary](access_policies_understand-action-summary.md)\. The *policy summary* table includes a list of services and summaries of the permissions that are defined by the chosen policy\. You can view the [policy summary](access_policies_understand.md) for any policies that are attached to a user on the **Users** page\. You can view the policy summary for managed policies on the **Policies** page\. If AWS is unable to render a summary for a policy, then you see the JSON policy document instead of the summary, and receive the following error:

**A summary for this policy cannot be generated\. You can still view or edit the JSON policy document\.**

If your policy does not include a summary, one of the following errors has occurred:
+ **Unsupported policy element** – IAM does not support generating policy summaries for policies that include one of the following [policy elements](reference_policies_elements.md):
  + `Principal`
  + `NotPrincipal`
  + `NotResource`
+ **No policy permissions** – If a policy does not provide any effective permissions, then the policy summary cannot be generated\. For example, if a policy includes a single statement with the element `"NotAction": "*"`, then it grants access to all actions except "all actions" \(\*\)\. This means it grants `Deny` or `Allow` access to nothing\.
**Note**  
You must be careful when using these policy elements such as `NotPrincipal`, `NotAction`, and `NotResource`\. For information about using policy elements, see [IAM JSON policy elements reference](reference_policies_elements.md)\.

  You can create a policy that does not provide effective permissions if you provide mismatched services and resources\. This can occur if you specify actions in one service and resources from another service\. In this case, the policy summary does appear\. The only indication that there is a problem is that the resource column in the summary can include a resource from a different service\. If this column includes a mismatched resource, then you should review your policy for errors\. To better understand your policies, always test them with the [policy simulator](access_policies_testing-policies.md)\.

### Policy summary includes unrecognized services, actions, or resource types<a name="unrecognized-services-actions"></a>

In the IAM console, if a [policy summary](access_policies_understand.md) includes a warning symbol \(![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png)\), then the policy might include an unrecognized service, action or resource type\. To learn about warnings within a policy summary, see [Policy summary \(list of services\)](access_policies_understand-policy-summary.md)\. 

**Note**  
IAM reviews service names, actions, and resource types for services that support policy summaries\. However, your policy summary might include a resource value or condition that does not exist\. Always test your policies with the [policy simulator](access_policies_testing-policies.md)\.

If your policy includes unrecognized services, actions or resource types, one of the following errors has occurred:
+ **Preview service** – Services that are in preview do not support policy summaries\.
+ **Custom service** – Custom services do not support policy summaries\.
+ **Service does not support summaries** – If your policy includes a generally available \(GA\) service that does not support policy summaries, then the service is included in the **Unrecognized services** section of the policy summary table\. Generally available services are services that are released publicly and are not preview or custom services\. If an unrecognized service is generally available and the name is spelled correctly, then the service does not support IAM policy summaries\. To learn how to request policy summary support for a GA service, see [Service does not support IAM policy summaries](#unsupported-services-actions)\.
+ **Action does not support summaries** – If your policy includes a supported service with an unsupported action, then the action is included in the **Unrecognized actions** section of the service summary table\. To learn about warnings within a service summary, see [Service summary \(list of actions\)](access_policies_understand-service-summary.md)\.
+ **Resource type does not support summaries** – If your policy includes a supported action with an unsupported resource type, then the resource is included in the **Unrecognized resource types** section of the service summary table\. To learn about warnings within a service summary, see [Service summary \(list of actions\)](access_policies_understand-service-summary.md)\.
+ **Typo** – Because the policy validator in AWS checks only that the JSON is syntactically correct, you can create a policy that includes a typo\. If you are certain that your policy contains none of the errors above, then your policy might include a typo\. Check for misspelled service, action, and resource type names\. For example, you might use `s2` instead of `s3` and `ListMyBuckets` instead of `ListAllMyBuckets`\. Another common action typo is the inclusion of unnecessary text in ARNs, such as `arn:aws:s3: : :*`, or missing colons in actions, such as `iam.CreateUser`\. You can evaluate a policy that might include typos by using the [policy simulator](access_policies_testing-policies.md) to confirm whether the policy provides the permissions you intended\.

### Service does not support IAM policy summaries<a name="unsupported-services-actions"></a>

When a generally available \(GA\) service or action is not recognized by IAM policy summaries or the visual editor, it is possible that the service does not support these features\. Generally available services are services that are released publicly and are not previewed or custom services\. If an unrecognized service is generally available and the name is spelled correctly, then the service does not support these features\. If your policy includes a supported service with an unsupported action, then the service does not fully support IAM policy summaries\.

**To request that a service add IAM policy summary or visual editor support**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Locate the policy that includes the unsupported service:
   + If the policy is a managed policy, choose **Policies** in the navigation pane\. In the list of policies, choose the name of the policy that you want to view\.
   + If the policy is an inline policy attached to the user, choose **Users** in the navigation pane\. In the list of users, choose the name of the user whose policy you want to view\. In the table of policies for the user, expand the header for the policy summary that you want to view\.

1. In the left side on the AWS Management Console footer, choose **Feedback**\. In the **Tell us about your experience:** box, type **I request that the <ServiceName> service add support for IAM policy summaries and the visual editor**\. If you want more than one service to support summaries, type **I request that the <ServiceName1>, <ServiceName2>, and <ServiceName3> services add support for IAM policy summaries and the visual editor**\.

**To request that a service add IAM policy summary support for a missing action**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Locate the policy that includes the unsupported service:
   + If the policy is a managed policy, choose **Policies** in the navigation pane\. In the list of policies, choose the name of the policy that you want to view\.
   + If the policy is an inline policy attached to the user, choose **Users** in the navigation pane\. In the list of users, choose the name of the user whose policy you want to view\. In the table of policies for the user, choose the name of the policy that you want to view to expand the policy summary\.

1. In the policy summary, choose the name of the service that includes an unsupported action\.

1. In the left side on the AWS Management Console footer, choose **Feedback**\. In the **Tell us about your experience:** box, type **I request that the <ServiceName> service add IAM policy summary and the visual editor support for the <ActionName> action**\. If you want to report more than one unsupported action, type **I request that the <ServiceName> service add IAM policy summary and the visual editor support for the <ActionName1>, <ActionName2>, and <ActionName3> actions**\. 

To request that a different service includes missing actions, repeat the last three steps\.

### My policy does not grant the expected permissions<a name="policy-summary-not-grant-permissions"></a>

To assign permissions to a user, group, role, or resource, you create a *policy*, which is a document that defines permissions\. The policy document includes the following elements:
+ **Effect** – whether the policy allows or denies access
+ **Action** – the list of actions that are allowed or denied by the policy
+ **Resource** – the list of resources on which the actions can occur
+ **Condition** \(Optional\) – the circumstances under which the policy grants permission

To learn about these and other policy elements, see [IAM JSON policy elements reference](reference_policies_elements.md)\. 

To grant access, your policy must define an action with a supported resource\. If your policy also includes a condition, that condition must include a [global condition key](reference_policies_condition-keys.md) or must apply to the action\. To learn which resources are supported by an action, see the [AWS documentation](http://docs.aws.amazon.com/) for your service\. To learn which conditions are supported by an action, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html)\.

To learn whether your policy defines an action, resource, or condition that does not grant permissions, you can view the [policy summary](access_policies_understand-policy-summary.md) for your policy using the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\. You can use policy summaries to identify and correct problems in your policy\.

There are several reasons why an element might not grant permissions despite being defined in the IAM policy:
+ [**An action is defined without an applicable resource**](#mismatch_action-no-resource)
+ [**A resource is defined without an applicable action**](#mismatch_resource-no-action)
+ [**A condition is defined without an applicable action**](#mismatch_condition-no-match)

To view examples of policy summaries that include warnings, see [Policy summary \(list of services\)](access_policies_understand-policy-summary.md)\.

#### An action is defined without an applicable resource<a name="mismatch_action-no-resource"></a>

The policy below defines all `ec2:Describe*` actions and defines a specific resource\. None of the `ec2:Describe` actions are granted because none of these actions support resource\-level permissions\. Resource\-level permissions mean that the action supports resources using [ARNs](reference_identifiers.md#identifiers-arns) in the policy's [`Resource`](reference_policies_elements_resource.md) element\. If an action does not support resource\-level permissions, then that statement in the policy must use a wildcard \(`*`\) in the `Resource` element\. To learn which services support resource\-level permissions, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "ec2:Describe*",
        "Resource": "arn:aws:ec2:us-east-2:ACCOUNT-ID:instance/*"
    }]
}
```

This policy does not provide any permissions, and the policy summary includes the following error:

`This policy does not grant any permissions. To grant access, policies must have an action that has an applicable resource or condition.`

To fix this policy, you must use `*` in the `Resource` element\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "ec2:Describe*",
        "Resource": "*"
    }]
}
```

#### A resource is defined without an applicable action<a name="mismatch_resource-no-action"></a>

The policy below defines an Amazon S3 bucket resource but does not include an S3 action that can be performed on that resource\. This policy also grants full access to all Amazon CloudFront actions\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "cloudfront:*",
        "Resource": [
            "arn:aws:cloudfront:*",
            "arn:aws:s3:::examplebucket"
        ]
    }]
}
```

This policy provides permissions for all CloudFront actions\. But because the policy defines the S3 `examplebucket` resource without defining any S3 actions, the policy summary includes the following warning:

`This policy defines some actions, resources, or conditions that do not provide permissions. To grant access, policies must have an action that has an applicable resource or condition.`

To fix this policy to provide S3 bucket permissions, you must define S3 actions that can be performed on a bucket resource\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": [
            "cloudfront:*",
            "s3:CreateBucket",
            "s3:ListBucket*",
            "s3:PutBucket*",
            "s3:GetBucket*"
        ],
        "Resource": [
            "arn:aws:cloudfront:*",
            "arn:aws:s3:::examplebucket"
        ]
    }]
}
```

Alternately, to fix this policy to provide only CloudFront permissions, remove the S3 resource\.

#### A condition is defined without an applicable action<a name="mismatch_condition-no-match"></a>

The policy below defines two Amazon S3 actions for all S3 resources, if the S3 prefix equals `custom` and the version ID equals `1234`\. However, the `s3:VersionId` condition key is used for object version tagging and is not supported by the defined bucket actions\. To learn which conditions are supported by an action, see [Actions, Resources, and Condition Keys for AWS Services](reference_policies_actions-resources-contextkeys.html) and follow the link to the service documentation for condition keys\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucketVersions",
                "s3:ListBucket"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "s3:prefix": [
                        "custom"
                    ],
                    "s3:VersionId": [
                        "1234"
                    ]
                }
            }
        }
    ]
}
```

This policy provides permissions for the `s3:ListBucketVersions` action and the `s3:ListBucket` action if the bucket name includes the `custom` prefix\. But because the `s3:VersionId` condition is not supported by any of the defined actions, the policy summary includes the following error:

`This policy does not grant any permissions. To grant access, policies must have an action that has an applicable resource or condition.`

To fix this policy to use S3 object version tagging, you must define an S3 action that supports the `s3:VersionId` condition key\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucketVersions",
                "s3:ListBucket",
                "s3:GetObjectVersion"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "s3:prefix": [
                        "custom"
                    ],
                    "s3:VersionId": [
                        "1234"
                    ]
                }
            }
        }
    ]
}
```

This policy provides permissions for every action and condition in the policy\. However, the policy still does not provide any permissions because there is no case where a single action matches both conditions\. Instead, you must create two separate statements that each include only actions with the conditions to which they apply\.

To fix this policy, create two statements\. The first statement includes the actions that support the `s3:prefix` condition, and the second statement includes the actions that support the `s3:VersionId` condition\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucketVersions",
                "s3:ListBucket"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "s3:prefix": "custom"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "s3:GetObjectVersion",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "s3:VersionId": "1234"
                }
            }
        }
    ]
}
```

## Troubleshoot policy management<a name="troubleshoot_policies-policy-manage"></a>

You can diagnose and resolve issues relating to policy management\.

### Attaching or detaching a policy in an IAM account<a name="troubleshoot_roles_cant-attach-detach-policy"></a>

Some AWS managed policies are linked to a service\. These policies are used only with a [service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role) for that service\. In the IAM console, when you view the **Summary** page for a policy, the page includes a banner to indicate that the policy is linked to a service\. You cannot attach this policy to a user, group, or role within IAM\. When you create a service\-linked role for the service, this policy is automatically attached to your new role\. Because the policy is required, you cannot detach the policy from the service\-linked role\. 

### Changing policies for your IAM identities based on their activity<a name="troubleshoot_change-policies-based-on-activity"></a>

You can update policies for your IAM identities \(users, groups, and roles\) based on their activity\. To do this, view your account's events in CloudTrail **Event history**\. CloudTrail event logs include detailed event information that you can use to change the policy's permissions\. You might find that a user or role is attempting to perform an action in AWS and that request is denied\. In that case, you can consider whether the user or role should have permission to perform the action\. If so, you can add the action and even the ARN of the resource that they attempted to access to their policy\. Alternatively, if the user or role has permissions that they are not using, you might consider removing those permissions from their policy\. Make sure that your policies grant the [least privilege](best-practices.md#grant-least-privilege) that is needed to perform only the necessary actions\. For more information about using CloudTrail, see [Viewing CloudTrail Events in the CloudTrail Console](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events-console.html) in the *AWS CloudTrail User Guide*\.

## Troubleshoot JSON policy documents<a name="troubleshoot_policies-json"></a>

You can diagnose and resolve issues relating to JSON policy documents\.

### More than one JSON policy object<a name="morethanonepolicyblock"></a>

An IAM policy must consist of one and only one JSON object\. You denote an object by placing \{ \} braces around it\. Although you can nest other objects within a JSON object by embedding additional \{ \} braces within the outer pair, a policy can contain only one outermost pair of \{ \} braces\. The following example is incorrect because it contains two objects at the top level \(called out in *red*\):

```
{
      "Version": "2012-10-17",
      "Statement": 
      {
         "Effect":"Allow",
         "Action":"ec2:Describe*",
         "Resource":"*"
      }
    }
    { 
      "Statement": {
         "Effect": "Allow",
         "Action": "s3:*",
         "Resource": "arn:aws:s3:::my-bucket/*"
      }
    }
```

You can, however, meet the intention of the previous example with the use of correct policy grammar\. Instead of including two complete policy objects each with its own `Statement` element, you can combine the two blocks into a single `Statement` element\. The `Statement` element has an array of two objects as its value, as shown in the following example \(called out in **bold**\): 

```
{
      "Version": "2012-10-17",
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "ec2:Describe*",
          "Resource":" *"
        },
        {
          "Effect": "Allow",
          "Action": "s3:*",
          "Resource": "arn:aws:s3:::my-bucket/*"
        }
      ]
    }
```

### More than one JSON statement element<a name="morethanonestatement"></a>

This error might at first appear to be a variation on the previous section\. However, syntactically it is a different type of error\. The following example has only one policy object as denoted by a single pair of \{ \} braces at the top level\. However, that object contains two `Statement` elements within it\.

 An IAM policy must contain only one `Statement` element, consisting of the name \(`Statement`\) appearing to the left of a colon, followed by its value on the right\. The value of a `Statement` element must be an object, denoted by \{ \} braces, containing one `Effect` element, one `Action` element, and one `Resource` element\. The following example is incorrect because it contains two `Statement` elements in the policy object \(called out in *red*\):

```
{
      "Version": "2012-10-17",
      "Statement": {
        "Effect": "Allow",
        "Action": "ec2:Describe*",
        "Resource": "*"
      },
      "Statement": {
        "Effect": "Allow",
        "Action": "s3:*",
        "Resource": "arn:aws:s3:::my-bucket/*"
      }
    }
```

A value object can be an array of multiple value objects\. To solve this problem, combine the two `Statement` elements into one element with an object array, as shown in the following example \(called out in **bold**\):

```
{
      "Version": "2012-10-17",
      "Statement": [    {
          "Effect": "Allow",
          "Action": "ec2:Describe*",
          "Resource":"*"
        },
        {
          "Effect": "Allow",
          "Action": "s3:*",
          "Resource": "arn:aws:s3:::my-bucket/*"
        }
     ]
    }
```

The value of the `Statement` element is an object array\. The array in this example consists of two objects, each of which is by itself is a correct value for a `Statement` element\. Each object in the array is separated by commas\.

### More than one effect, action, or resource element in a JSON statement element<a name="duplicateelement"></a>

On the value side of the `Statement` name/value pair, the object must consist of only one `Effect` element, one `Action` element, and one `Resource` element\. The following policy is incorrect because it has two `Effect` elements in the value object of the `Statement`:

```
{
      "Version": "2012-10-17",
      "Statement": {
        "Effect": "Deny",
        "Effect": "Allow",     
        "Action": "ec2:* ",
        "Resource": "*"
      }
    }
```

**Note**  
The policy engine does not allow such errors in new or edited policies\. However, the policy engine continues to permit policies that were saved before the engine was updated\. The behavior of existing policies with the error is as follows:  
Multiple `Effect` elements: only the last `Effect` element is observed\. The others are ignored\.
Multiple `Action` elements: all `Action` elements are combined internally and treated as if they were a single list\.
Multiple `Resource` elements: all `Resource` elements are combined internally and treated as if they were a single list\.
The policy engine does not allow you to save any policy with syntax errors\. You must correct the errors in the policy before you can save it\. The [Policy Validator](access_policies_policy-validator.md) tool can help you to find all older policies with errors and can recommend corrections for them\.

 In each case, the solution is to remove the incorrect extra element\. For `Effect` elements, this is straightforward: if you want the previous example to *deny* permissions to Amazon EC2 instances, then you must remove the line `"Effect": "Allow",` from the policy, as follows:

```
{
      "Version": "2012-10-17",
      "Statement": {
        "Efect": "Deny",
        "Action": "ec2:* ",
        "Resource": "*"
      }
    }
```

However, if the duplicate element is `Action` or `Resource`, then the resolution can be more complicated\. You might have multiple actions that you want to allow \(or deny\) permission to, or you might want to control access to multiple resources\. For example, the following example is incorrect because it has multiple `Resource` elements \(called out in *red*\):

```
{
      "Version": "2012-10-17",
      "Statement": {
        "Effect": "Allow",
        "Action": "s3:*",
        "Resource": "arn:aws:s3:::my-bucket",
        "Resource": "arn:aws:s3:::my-bucket/*"
      }
    }
```

Each of the required elements in a `Statement` element's value object can be present only once\. The solution is to place each value in an array\. The following example illustrates this by making the two separate resource elements into one `Resource` element with an array as the value object \(called out in **bold**\):

```
{	
      "Version": "2012-10-17",
      "Statement": {
        "Effect": "Allow",
        "Action": "s3:*",
        "Resource": [
          "arn:aws:s3:::my-bucket",
          "arn:aws:s3:::my-bucket/*"
        ]
      }
    }
```

### Missing JSON version element<a name="missing-version"></a>

A `Version` policy element is different from a policy version\. The `Version` policy element is used within a policy and defines the version of the policy language\. A policy version, on the other hand, is created when you make changes to a customer managed policy in IAM\. The changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new version of the managed policy\. To learn more about the `Version` policy element see [IAM JSON policy elements: Version](reference_policies_elements_version.md)\. To learn more about policy versions, see [Versioning IAM policies](access_policies_managed-versioning.md)\.

As AWS features evolve, new capabilities are added to IAM policies to support those features\. Sometimes, an update to the policy syntax includes a new version number\. If you use newer features of the policy grammar in your policy, then you must tell the policy parsing engine which version you are using\. The default policy version is "2008\-10\-17\." If you want to use any policy feature that was introduced later, then you must specify the version number that supports the feature you want\. We recommend that you *always* include the latest policy syntax version number, which is currently `"Version": "2012-10-17"`\. For example, the following policy is incorrect because it uses a policy variable `${...}` in the ARN for a resource\. But it fails to specify a policy syntax version that supports policy variables \(called out in *red*\):

```
{
  "Statement": 
  {
    "Action": "iam:*AccessKey*",
    "Effect": "Allow",
    "Resource": "arn:aws:iam::123456789012:user/${aws:username}"
  }
}
```

Adding a `Version` element at the top of the policy with the value `2012-10-17`, the first IAM API version that supports policy variables, solves this problem \(called out in **bold**\):

```
{
  "Version": "2012-10-17",
  "Statement": 
  {
    "Action": "iam:*AccessKey*",
    "Effect": "Allow",
    "Resource": "arn:aws:iam::123456789012:user/${aws:username}"
  }
}
```