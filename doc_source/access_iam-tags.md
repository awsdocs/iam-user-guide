# Controlling Access Using IAM Tags<a name="access_iam-tags"></a>

With IAM tags, you can add custom attributes to a user or role in the form of a key–value pair\. For more information about IAM tags, see [Tagging IAM Entities](id_tags.md)\. You can use tags to control permissions in AWS\. That is, you can control what a user or role can do or what can be done to a user or role resource\.

To use tags to control access, you must understand how AWS grants access\. AWS is composed of collections of *resources*\. An IAM user is a resource\. An Amazon S3 bucket is a resource\. When you use the AWS API, the AWS CLI, or the AWS Management Console to perform an operation \(such as creating a user\), you send a *request* for that operation\. Your request specifies an action, a resource, a *principal entity* \(user or role\), a *principal account*, and any necessary request information\. All of this information provides *context*\.

AWS then checks that you \(the principal entity\) are authenticated \(signed in\) and authorized \(have permission\) to perform the specified action on the specified resource\. During authorization, AWS checks all the policies that apply to the context of your request\. Most policies are stored in AWS as [JSON documents](access_policies.md#access_policies-json) and specify the permissions for principal entities\. For more information about policy types and uses, see [Policies and Permissions](access_policies.md)\.

AWS authorizes the request only if each part of your request is allowed by the policies\. To view a diagram and learn more about the IAM infrastructure, see [Understanding How IAM Works](intro-structure.md)\. For details about how IAM determines whether a request is allowed, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.

Tags can complicate this process because tags can be attached to the *resource*, passed in the *request*, or attached to the *principal* that is making the request\. To control access based on tags, you provide tag information in the [condition element](reference_policies_elements_condition.md) of a policy\. 

When you create an IAM policy, you can use IAM tags and the associated tag condition key to control access to do any of the following:
+ **[Resource](#access_iam-tags_control-resources)** – Control access to users or roles based on the tags on those resources\. To do this, use the **iam:ResourceTag/*key\-name*** condition key to determine whether to allow access to the IAM resource based on the tags that are attached to the resource\.
+ **[Request](#access_iam-tags_control-requests)** – Control what tags can be passed in an IAM request\. To do this, use the **aws:RequestTag/*key\-name*** condition key to specify what tags can be added, changed, or removed from an IAM user or role\.
+ **[Principal](#access_iam-tags_control-principals)** – Control what the person making the request \(the principal\) is allowed to do based on the tags that are attached to that person's identity\. To do this, use the **aws:PrincipalTag/*key\-name*** condition key to specify what tags must be attached to the principal before the request is allowed\.
+ **[Any part of the authorization process](#access_iam-tags_control-tag-keys)** – Use the **aws:TagKeys** condition key to control whether specific tag keys can be used on a resource, in a request, or by a principal\. In this case, the value does not matter\. 

You can create an IAM policy visually, using JSON, or by importing an existing managed policy\. For details, see [Creating IAM Policies](access_policies_create.md)\.

## Controlling Access to Resources<a name="access_iam-tags_control-resources"></a>

You can use tags in your IAM policies to control access to IAM users and roles\. However, because IAM does not support tags for groups, you cannot use tags to control access to groups\.

This example shows how you might create a policy that allows deleting users with the **status=terminated** tag\. To use this policy, replace the red italicized text in the example policy with your own information\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "iam:DeleteUser",
        "Resource": "*",
        "Condition": {"StringLike": {"iam:ResourceTag/status": "terminated"}}
    }]
}
```

This example shows how you might create a policy that allows editing tags for all users with the **jobFunction = employee** tag\. To use this policy, replace the red italicized text in the example policy with your own information\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": [
                "iam:ListUserTags",
                "iam:TagUser", 
                "iam:UntagUser"
            ],
        "Resource": "*",
        "Condition": {"StringLike": {"iam:ResourceTag/jobFunction": "employee"}}
    }]
}
```

## Controlling Access to Requests<a name="access_iam-tags_control-requests"></a>

You can use tags in your IAM policies to control what tags can be added, changed, or removed from an IAM user or role\. 

This example shows how you might create a policy that allows tagging users only with a **department = HR** or **department = CS** tag\. To use this policy, replace the red italicized text in the example policy with your own information\. 

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "iam:TagUser",
        "Resource": "*",
        "Condition": {"StringLike": {"aws:RequestTag/department": [
            "HR",
            "CS"
        ]}}
    }]
}
```

## Controlling Access to Principals<a name="access_iam-tags_control-principals"></a>

You can use tags in your IAM policies to control what the person making the request \(the principal\) is allowed to do based on the tags attached to that person's identity\. 

This example shows how you might create a policy that allows users with the **tagManager=true** tag to manage IAM users, groups, or roles\. To use this policy, replace the red italicized text in the example policy with your own information\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "iam:*",
      "Resource": "*",
      "Condition": {"StringEquals": {"aws:PrincipalTag/tagManager": "true"}}
    }
  ]
}
```

## Controlling Access Using Tag Keys<a name="access_iam-tags_control-tag-keys"></a>

You can use tags in your IAM policies to control whether specific tag keys can be used on a resource, in a request, or by a principal\.

This example shows how you might create a policy that allows removing only the tag with the **project** key from users\. To use this policy, replace the red italicized text in the example policy with your own information\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "iam:UntagUser",
        "Resource": "*",
        "Condition": {"ForAllValues:StringEquals": {"aws:TagKeys": ["project"]}}
    }]
}
```