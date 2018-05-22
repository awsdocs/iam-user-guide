# Controlling Access Using Policies<a name="access_controlling"></a>

You can use a policy to control access to resources within IAM or all of AWS\. 

To use a [policy](access_policies.md) to control access in AWS, you must understand how IAM grants access\. AWS is composed of collections of *resources*\. An IAM user is a resource\. An Amazon S3 bucket is a resource\. When you use the AWS API, the AWS CLI, or the AWS Management Console to take an action \(such as creating a user\), you send a *request* for that action\. Your request specifies an action, a resource, a *principal* \(group, user, or role\), a *principal account*, and any necessary request information\. All of this information provides *context*\.

IAM then checks that you \(the principal\) are authenticated \(signed in\) and authorized \(have permission\) to perform the specified action on the specified resource\. During authorization, IAM checks all the policies attached to your user or role and the policies attached to the resource that you are trying to access\. These checks are based on the context of your request\. AWS authorizes the request only if each part of your request is allowed by the policies\.

To view a diagram of this process, see [Understanding How IAM Works](intro-structure.md)\. For details about how IAM determines whether a request is allowed, see [IAM JSON Policy Evaluation Logic](reference_policies_evaluation-logic.md)\. 

When you write an IAM policy, you can control access to the following:
+ **[AWS for Principals](#access_controlling-principals)** – Control what the person making the request \(the [principal](intro-structure.md#intro-structure-principal) \) is allowed to do\. 
+ **[IAM Identities](#access_controlling-identities)** – Control which IAM identities \(groups, users, and roles\) can be accessed and how\.
+ **[IAM Policies](#access_controlling-policies)** – Control who can create, edit, and delete customer managed policies, and who can attach and detach all managed policies\.
+ **[AWS Resources](#access_controlling-resources)** – Control who has access to resources using an identity\-based policy or a resource\-based policy\.
+ **[AWS Accounts](#access_controlling-principal-accounts)** – Control whether a request is allowed only for members of a specific account\.

Policies let you specify who has access to AWS resources, and what actions they can perform on those resources\. Every IAM user starts with no permissions\. In other words, by default, users can do nothing, not even view their own access keys\. To give a user permission to do something, you can add the permission to the user \(that is, attach a policy to the user\)\. Or you can add the user to a group that has the desired permission\.

For example, you might grant a user permission to list his or her own access keys\. You might also expand that permission and also let each user create, update, and delete their own keys\. 

When you give permissions to a group, all users in that group get those permissions\. For example, you can give the Admins group permission to perform any of the IAM actions on any of the AWS account resources\. Another example: You can give the Managers group permission to describe the AWS account's Amazon EC2 instances\.

For information about how to delegate basic permissions to your users, groups, and roles, see [Permissions Required to Access IAM Resources](access_permissions-required.md)\. For additional examples of policies that illustrate basic permissions, see [Example Policies for Administering IAM Resources](id_credentials_delegate-permissions_examples.md)\.

## Controlling Access for Principals<a name="access_controlling-principals"></a>

You can use identity\-based policies to control what the person making the request \(the principal\) is allowed to do\. To do this, you must attach a policy to that person's identity \(group, user, or role\)\. 

For example, assume that you want the user Zhang Wei to have full access to Amazon EC2, read\-only access to Amazon S3, and the ability to change his own password in the AWS Management Console\. You can create three different policies so that you can later break them up if you need one set of permissions for a different user\. Or you can put all the permissions together in a single policy, and then attach that policy to the IAM user that is named Zhang Wei\. You could also attach a policy to a group to which Zhang Wei belongs, or a role that Zhang Wei can assume\. As a result, when Zhang views the contents of an S3 bucket or starts a new EC2 instance, his requests are allowed\. If he tries to create a new S3 bucket or change the contents of an existing bucket, his request is denied because he doesn't have permission\. 

For more information, refer to these resources:
+ To learn more about creating an IAM policy that you can attach to a principal, see [Creating IAM Policies](access_policies_create.md)\.
+ To learn how to attach an IAM policy to a principal, see [Attaching IAM Policies \(Console\)](access_policies_manage-attach-detach.md#attach-managed-policy-console)\.
+ To see an example policy for granting full access to EC2, see [Amazon EC2: Allows Full EC2 Access Within a Specific Region, Programmatically and in the Console](reference_policies_examples_ec2_region.md)\.
+ To allow read\-only access to an S3 bucket, use the first two statements of the following example policy: [Amazon S3: Allows Read and Write Access to a Specific S3 Bucket, Programmatically and in the Console](reference_policies_examples_s3_rw-bucket-console.md)\.
+ To see an example policy for allowing users to rotate their credentials, see [IAM: Allows IAM Users to Rotate Their Own Credentials Programmatically and in the Console](reference_policies_examples_iam_credentials_console.md)\.

## Controlling Access to Identities<a name="access_controlling-identities"></a>

You can use IAM policies to control what all your users can do to an identity by creating a policy that you attach to all users through the use of a group\. To do this, create a policy that limits what can be done to an identity, or who can access it\.

For example, you can create a group named **AllUsers**, and then attach that group to all users\. When you create the group, you might give all your users access to rotate their credentials as described in the previous section\. You can then create a policy that denies access to change the group unless the user name is included in the condition of the policy\. But that part of the policy only denies access to anyone except those users listed\. You also have to include permissions to allow all the group management actions for everyone in the group\. Finally, you attach this policy to the group so that it is applied to all users\. As a result, when a user not specified in the policy tries to make changes to the group, the request is denied\. 

**To create this policy with the visual editor**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane on the left, choose **Policies**\. 

   If this is your first time choosing **Policies**, the **Welcome to Managed Policies** page appears\. Choose **Get Started**\.

1. Choose **Create policy**\.

1. On the **Visual editor** tab, choose **Choose a service** to get started\. Then choose **IAM**\.

1. Choose **Select actions** and then type **group** in the search box\. The visual editor shows all the IAM actions that contain the word `group`\. Select all of the check boxes\.

1. Choose **Resources** to specify resources for your policy\. Based on the actions you chose, you should see **group**, **group\-path**, and **user** resource types\.
   + **group** – Choose **Add ARN**\. For **Resource**, select the check box next to **Any**\. For **Group Name With Path**, type the group name **AllUsers**\. Then choose **Add**\.
   + **group\-path** – Select the check box next to **Any**\.
   + **user** – Select the check box next to **Any**\.

   One of the actions that you chose, `ListGroups`, does not support using specific resources\. You do not have to choose **All resources** for that action\. When you save your policy or view the policy on the **JSON** tab, you can see that IAM automatically creates a new permission block granting this action permission on all resources\.

1. To add another permission block, choose **Add additional permissions**\.

1. Choose **Choose a service** and then choose **IAM**\.

1. Choose **Select actions** and then choose **Switch to deny permissions**\. When you do that, the entire block is used to deny permissions\.

1. Type **group** in the search box\. The visual editor shows you all the IAM actions that contain the word `group`\. Select the check boxes next to the following actions:
   + **CreateGroup**
   + **DeleteGroup**
   + **RemoveUserFromGroup**
   + **AttachGroupPolicy**
   + **DeleteGroupPolicy**
   + **DetachGroupPolicy**
   + **PutGroupPolicy**
   + **UpdateGroup**

1. Choose **Resources** to specify the resources for your policy\. Based on the actions that you chose, you should see the **group** resource type\. Choose **Add ARN**\. For **Resource**, select the check box next to **Any**\. For **Group Name With Path**, type the group name **AllUsers**\. Then choose **Add**\.

1. Choose **Specify request conditions \(optional\)** and then choose **Add condition**\. Complete the form with the following values:
   + **Key** – Choose **aws:username**
   + **Qualifier** – Choose **For any value in request**
   + **Operator** – Choose **StringNotEquals**
   + **Value** – Type **srodriguez** and then choose **Add another condition value**\. Type **mjackson** and then choose **Add another condition value**\. Type **adesai** and then choose **Add**\.

   This condition ensures that access will be denied to the specified group management actions when the user making the call is not included in the list\. Because this explicitly denies permission, it overrides the previous block that allowed those users to call the actions\. Users on the list are not denied access, and they are granted permission in the first permission block, so they can fully manage the group\.

1. When you are finished, choose **Review policy**\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy Restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. On the **Review policy** page, for the **Name**, type **LimitAllUserGroupManagement**\. For the **Description**, type **Allows all users Read\-only access to a specific group, and allows only specific users access to make changes to the group**\. Review the policy summary to make sure that you have granted the intended permissions\. Then choose **Create policy** to save your new policy\.

1. Attach the policy to your group\. For more information, see [Attaching and Detaching IAM Policies](access_policies_manage-attach-detach.md)\.

Alternatively, you can create the same policy using this example JSON policy document\. For more information, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

**Example Example policy that allows all users Read\-only access to a specific group, and allows only specific users access to make changes to the group**  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowAllUsersToListAllGroups",
            "Effect": "Allow",
            "Action": "iam:ListGroups",
            "Resource": "arn:aws:iam::*:*"
        },
        {
            "Sid": "AllowAllUsersToViewAndManageThisGroup",
            "Effect": "Allow",
            "Action": [
                "iam:CreateGroup",
                "iam:DeleteGroup",
                "iam:ListGroupPolicies",
                "iam:UpdateGroup",
                "iam:GetGroup",
                "iam:RemoveUserFromGroup",
                "iam:AddUserToGroup",
                "iam:ListGroupsForUser",
                "iam:AttachGroupPolicy",
                "iam:DetachGroupPolicy",
                "iam:ListAttachedGroupPolicies",
                "iam:GetGroupPolicy",
                "iam:DeleteGroupPolicy",
                "iam:PutGroupPolicy"
            ],
            "Resource": [
                "arn:aws:iam::*:user/*",
                "arn:aws:iam::*:group/AllUsers"
            ]
        },
        {
            "Sid": "LimitGroupManagementAccessToSpecificUsers",
            "Effect": "Deny",
            "Action": [
                "iam:CreateGroup",
                "iam:RemoveUserFromGroup",
                "iam:DeleteGroup",
                "iam:AttachGroupPolicy",
                "iam:UpdateGroup",
                "iam:DetachGroupPolicy",
                "iam:DeleteGroupPolicy",
                "iam:PutGroupPolicy"
            ],
            "Resource": "arn:aws:iam::*:group/AllUsers",
            "Condition": {
                "ForAnyValue:StringNotEquals": {
                    "aws:username": [
                        "srodriguez",
                        "mjackson",
                        "adesai"
                    ]
                }
            }
        }
    ]
}
```

## Controlling Access to Policies<a name="access_controlling-policies"></a>

You can control how your users can apply AWS managed policies\. To do this, attach this policy to all your users\. Ideally, you can do this using a group\.

For example, you might create a policy that allows users to attach only the [IAMUserChangePassword](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/IAMUserChangePassword) and [PowerUserAccess](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/job-function/PowerUserAccess) AWS managed policies to a new IAM user, group, or role\.

For customer managed policies, you can control who can create, update, and delete these policies\. You can control who can attach and detach policies to and from principal entities \(groups, users, and roles\)\. You can also control which policies a user can attach or detach, and to and from which entities\. 

For example, you can give permissions to an account administrator to create, update, and delete policies\. Then you give permissions to a team leader or other limited administrator to attach and detach these policies to and from principal entities that the limited administrator manages\.

For more information, refer to these resources:
+ To learn more about creating an IAM policy that you can attach to a principal, see [Creating IAM Policies](access_policies_create.md)\.
+ To learn how to attach an IAM policy to a principal, see [Attaching IAM Policies \(Console\)](access_policies_manage-attach-detach.md#attach-managed-policy-console)\.
+ To see an example policy for limiting the use of managed policies, see [IAM: Limits Managed Policies That Can Be Applied to a New IAM User, Group, or Role](reference_policies_examples_iam_limit-managed.md)\.

### Controlling Permissions for Creating, Updating, and Deleting Customer Managed Policies<a name="policies-controlling-access-create-update-delete"></a>

You can use [IAM policies](access_policies.md) to control who is allowed to create, update, and delete customer managed policies in your AWS account\. The following list contains API operations that pertain directly to creating, updating, and deleting policies or policy versions: 
+ [CreatePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicy.html)
+ [CreatePolicyVersion](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreatePolicyVersion.html)
+ [DeletePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeletePolicy.html)
+ [DeletePolicyVersion](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeletePolicyVersion.html)
+ [SetDefaultPolicyVersion](http://docs.aws.amazon.com/IAM/latest/APIReference/API_SetDefaultPolicyVersion.html)

The API operations in the preceding list correspond to actions that you can allow or deny—that is, permissions that you can grant—using an IAM policy\. 

The following example shows a policy that allows a user to create, update \(that is, create a new policy version\), delete, and set a default version for all customer managed policies in the AWS account\. The example policy also allows the user to list policies and get policies\. To learn how to create a policy using this example JSON policy document, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

**Example policy that allows creating, updating, deleting, listing, getting, and setting the default version for all policies**  

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:CreatePolicy",
      "iam:CreatePolicyVersion",
      "iam:DeletePolicy",
      "iam:DeletePolicyVersion",
      "iam:GetPolicy",
      "iam:GetPolicyVersion",
      "iam:ListPolicies",
      "iam:ListPolicyVersions",
      "iam:SetDefaultPolicyVersion"
    ],
    "Resource": "*"
  }
}
```

You can create policies that limit the use of these API operations to affect only the managed policies that you specify\. For example, you might want to allow a user to set the default version and delete policy versions, but only for specific customer managed policies\. You do this by specifying the policy ARN in the `Resource` element of the policy that grants these permissions\. 

The following example shows a policy that allows a user to delete policy versions and set the default version, but only for the customer managed policies that include the path /TEAM\-A/\. The customer managed policy ARN is specified in the `Resource` element of the policy \(in this example the ARN includes a path and a wildcard and thus matches all customer managed policies that include the path /TEAM\-A/\)\. To learn how to create a policy using this example JSON policy document, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

For more information about using paths in the names of customer managed policies, see [Friendly Names and Paths](reference_identifiers.md#identifiers-friendly-names)\. 

**Example policy that allows deleting policy versions and setting the default version for only specific policies**  

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:DeletePolicyVersion",
      "iam:SetDefaultPolicyVersion"
    ],
    "Resource": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:policy/TEAM-A/*"
  }
}
```

### Controlling Permissions for Attaching and Detaching Managed Policies<a name="policies-controlling-access-attach-detach"></a>

You can also use IAM policies to allow users to work with only specific managed policies\. In effect, you can control which permissions a user is allowed to grant to other principal entities\. 

The following list shows API operations that pertain directly to attaching and detaching managed policies to and from principal entities:
+  [AttachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachGroupPolicy.html)
+ [AttachRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachRolePolicy.html)
+ [AttachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AttachUserPolicy.html)
+ [DetachGroupPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachGroupPolicy.html)
+ [DetachRolePolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachRolePolicy.html)
+ [DetachUserPolicy](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DetachUserPolicy.html)

You can create policies that limit the use of these API operations to affect only the specific managed policies and/or principal entities that you specify\. For example, you might want to allow a user to attach managed policies, but only the managed policies that you specify\. Or, you might want to allow a user to attach managed policies, but only to the principal entities that you specify\. 

The following example policy allows a user to attach managed policies to only the groups and roles that include the path /TEAM\-A/\. The group and role ARNs are specified in the `Resource` element of the policy\. \(In this example the ARNs include a path and a wildcard character and thus match all groups and roles that include the path /TEAM\-A/\)\. To learn how to create a policy using this example JSON policy document, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

**Example policy that allows attaching managed policies to only specific groups or roles**  

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:AttachGroupPolicy",
      "iam:AttachRolePolicy"
    ],
    "Resource": [
      "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:group/TEAM-A/*",
      "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:role/TEAM-A/*"
    ]
  }
}
```

You can further limit the actions in the preceding example to affect only specific policies—that is, you can control which permissions a user is allowed to attach to other principal entities—by adding a condition to the policy\. 

In the following example, the condition ensures that the `AttachGroupPolicy` and `AttachRolePolicy` permissions are allowed only when the policy being attached matches one of the specified policies\. The condition uses the `iam:PolicyARN` [condition key](reference_policies_elements_condition.md) to determine which policy or policies are allowed to be attached\. The following example policy expands on the previous example by allowing a user to attach only the managed policies that include the path /TEAM\-A/ to only the groups and roles that include the path /TEAM\-A/\. To learn how to create a policy using this example JSON policy document, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": [
      "iam:AttachGroupPolicy",
      "iam:AttachRolePolicy"
    ],
    "Resource": [
      "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:group/TEAM-A/*",
      "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:role/TEAM-A/*"
    ],
    "Condition": {"ArnLike": 
      {"iam:PolicyARN": "arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:policy/TEAM-A/*"}
    }
  }
}
```

This policy uses the `ArnLike` condition operator because the ARN includes a wildcard character\. For a specific ARN, use the `ArnEquals` condition operator\. For more information about `ArnLike` and `ArnEquals`, see [Amazon Resource Name \(ARN\) Condition Operators](reference_policies_elements_condition_operators.md#Conditions_ARN) in the *Condition Types* section of the *Policy Element Reference*\. 

For example, you can limit the use of actions to involve only the managed policies that you specify\. You do this by specifying the policy ARN in the `Condition` element of the policy that grants these permissions\. For example, to specify the ARN of a customer managed policy:

```
"Condition": {"ArnEquals": 
  {"iam:PolicyARN": "arn:aws:iam::123456789012:policy/POLICY-NAME"}
}
```

You can also specify the ARN of an AWS managed policy in a policy's `Condition` element\. The ARN of an AWS managed policy uses the special alias `aws` in the policy ARN instead of an account ID, as in this example:

```
"Condition": {"ArnEquals": 
  {"iam:PolicyARN": "arn:aws:iam::aws:policy/AmazonEC2FullAccess"}
}
```

## Controlling Access to Resources<a name="access_controlling-resources"></a>

You can control access to resources using an identity\-based policy or a resource\-based policy\. In an identity\-based policy, you attach the policy to an identity and specify what resources that identity can access\. In a resource\-based policy, you attach a policy to the resource that you want to control\. In the policy, you specify which principals can access that resource\. For more information about both types of policies, see [Identity\-Based Policies and Resource\-Based Policies](access_policies_identity-vs-resource.md)\.

For more information, refer to these resources:
+ To learn more about creating an IAM policy that you can attach to a principal, see [Creating IAM Policies](access_policies_create.md)\.
+ To learn how to attach an IAM policy to a principal, see [Attaching IAM Policies \(Console\)](access_policies_manage-attach-detach.md#attach-managed-policy-console)\.
+ Amazon S3 supports using resource\-based policies on their buckets\. For more information, see [Bucket Policy Examples](http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html)\.
<a name="NoDefaultPermissions"></a>
**Resource Creators Do Not Automatically Have Permissions**  
If you sign in using the AWS account root user credentials, you have permission to perform any action on resources that belong to the account\. However, this isn't true for IAM users\. An IAM user might be granted access to create a resource, but the user's permissions, even for that resource, are limited to what's been explicitly granted\. This means that just because you create a resource, such as an IAM role, you do not automatically have permission to edit or delete that role\. Additionally, your permission can be revoked at any time by the account owner or by another user who has been granted access to manage your permissions\.

## Controlling Access to Principals in a Specific Account<a name="access_controlling-principal-accounts"></a>

You can directly grant IAM users in your own account access to your resources\. If users from another account need access to your resources, you can create an IAM role, which is an entity that includes permissions but that isn't associated with a specific user\. Users from other accounts can then assume the role and access resources according to the permissions you've assigned to the role\. For more information, see [Providing Access to an IAM User in Another AWS Account That You Own](id_roles_common-scenarios_aws-accounts.md)\.

**Note**  
For services that support resource\-based policies as described in [Identity\-Based Policies and Resource\-Based Policies](access_policies_identity-vs-resource.md) \(such as Amazon S3, Amazon SNS, and Amazon SQS\), an alternative to using roles is to attach a policy to the resource \(bucket, topic, or queue\) that you want to share\. The resource\-based policy can specify the AWS account that has permissions to access the resource\.