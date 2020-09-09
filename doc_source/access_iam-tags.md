# Controlling access to and for IAM users and roles using IAM resource tags<a name="access_iam-tags"></a>

Use the information in the following section to control who can access your IAM users and roles and what resources your users and roles can access\. For more general information and examples for controlling access to other AWS resources, see [Controlling access to AWS resources using resource tags](access_tags.md)\.

Tags can be attached to the IAM *resource*, passed in the *request*, or attached to the *principal* that is making the request\. An IAM user or role can be both a resource and principal\. For example, you can write a policy that allows a user to list the groups for a user\. This operation is allowed only if the user making the request \(the principal\) has the same `project=blue` tag as the user they're trying to view\. In this example, the user can view the group membership for any user, including themselves, as long as they are working on the same project\.

To control access based on tags, you provide tag information in the [condition element](reference_policies_elements_condition.md) of a policy\. When you create an IAM policy, you can use IAM tags and the associated tag condition key to control access to any of the following:
+ **[Resource](#access_iam-tags_control-resources)** – Control access to user or role resources based on their tags\. To do this, use the **iam:ResourceTag/*key\-name*** condition key to specify which tag key\-value pair must be attached to the resource\. A similar service\-specific key, such as `ec2:ResourceTag`, is used other AWS resources\. For more information, see [Controlling access to AWS resources](access_tags.md#access_tags_control-resources)\.
+ **[Request](#access_iam-tags_control-requests)** – Control what tags can be passed in an IAM request\. To do this, use the **aws:RequestTag/*key\-name*** condition key to specify what tags can be added, changed, or removed from an IAM user or role\. This key is used the same way for IAM resources and other AWS resources\. For more information, see [Controlling access during AWS requests](access_tags.md#access_tags_control-requests)\.
+ **[Principal](#access_iam-tags_control-principals)** – Control what the person making the request \(the principal\) is allowed to do based on the tags that are attached to that person's IAM user or role\. To do this, use the **aws:PrincipalTag/*key\-name*** condition key to specify what tags must be attached to the IAM user or role before the request is allowed\.
+ **[Any part of the authorization process](#access_iam-tags_control-tag-keys)** – Use the **aws:TagKeys** condition key to control whether specific tag keys can be used on a resource, in a request, or by a principal\. In this case, the key value does not matter\. This key behaves similarly for IAM resources and other AWS resources\. However, when you tag a user in IAM, this also controls whether the principal can make the request to any service\. For more information, see [Controlling access based on tag keys](access_tags.md#access_tags_control-tag-keys)\.

You can create an IAM policy using the visual editor, using JSON, or by importing an existing managed policy\. For details, see [Creating IAM policies](access_policies_create.md)\.

## Controlling access to IAM resources<a name="access_iam-tags_control-resources"></a>

You can use tags in your IAM policies to control access to IAM user and role resources\. However, because IAM does not support tags for groups, you cannot use tags to control access to groups\.

This example shows how you might create a policy that allows deleting users with the `status=terminated` tag\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

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

This example shows how you might create a policy that allows editing tags for all users with the `jobFunction = employee` tag\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

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

## Controlling access during IAM requests<a name="access_iam-tags_control-requests"></a>

You can use tags in your IAM policies to control what tags can be passed in the IAM request\. You can specify which tag key\-value pairs can be added, changed, or removed from an IAM user or role\. 

This example shows how you might create a policy that allows tagging users only with a `department = HR` or `department = CS` tag\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

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

## Controlling access for IAM principals<a name="access_iam-tags_control-principals"></a>

IAM tags enable you to control what the principal is allowed to do based on the tags attached to that person's identity\. 

This example shows how you might create a policy that allows a principal to start or stop an Amazon EC2 instance\. This operation is allowed only when the instance's resource tag and the principal's tag have the same value for the tag key `cost-center`\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "ec2:startInstances",
            "ec2:stopInstances"
        ],
        "Resource": "*",
        "Condition": {"StringEquals": 
            {"ec2:ResourceTag/cost-center": "${aws:PrincipalTag/cost-center}"}}
    }
}
```

## Controlling access based on tag keys<a name="access_iam-tags_control-tag-keys"></a>

You can use tags in your IAM policies to control whether specific tag keys can be used on a resource, in a request, or by a principal\.

This example shows how you might create a policy that allows removing only the tag with the `temporary` key from users\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "iam:UntagUser",
        "Resource": "*",
        "Condition": {"ForAllValues:StringEquals": {"aws:TagKeys": ["temporary"]}}
    }]
}
```