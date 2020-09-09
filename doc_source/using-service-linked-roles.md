# Using service\-linked roles<a name="using-service-linked-roles"></a>

A service\-linked role is a unique type of IAM role that is linked directly to an AWS service\. Service\-linked roles are predefined by the service and include all the permissions that the service requires to call other AWS services on your behalf\. The linked service also defines how you create, modify, and delete a service\-linked role\. A service might automatically create or delete the role\. It might allow you to create, modify, or delete the role as part of a wizard or process in the service\. Or it might require that you use IAM to create or delete the role\. Regardless of the method, service\-linked roles make setting up a service easier because you don't have to manually add the necessary permissions for the service to complete actions on your behalf\.

The linked service defines the permissions of its service\-linked roles, and unless defined otherwise, only that service can assume the roles\. The defined permissions include the trust policy and the permissions policy, and that permissions policy cannot be attached to any other IAM entity\.

You can delete the roles only after first deleting their related resources\. This protects your resources because you can't inadvertently remove permission to access the resources\. 

**Tip**  
For information about which services support using service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

## Service\-linked role permissions<a name="service-linked-role-permissions"></a>

You must configure permissions for an IAM entity \(user or role\) to allow the user or role to create or edit the service\-linked role\.

**Note**  
The ARN for a service\-linked role includes a service principal, which is indicated in the policies below as `SERVICE-NAME.amazonaws.com`\. Do not try to guess the service principal, because it is case sensitive and the format can vary across AWS services\. To view the service principal for a service, see its service\-linked role documentation\.

**To allow an IAM entity to create a specific service\-linked role**

Add the following policy to the IAM entity that needs to create the service\-linked role\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:CreateServiceLinkedRole",
            "Resource": "arn:aws:iam::*:role/aws-service-role/SERVICE-NAME.amazonaws.com/SERVICE-LINKED-ROLE-NAME-PREFIX*",
            "Condition": {"StringLike": {"iam:AWSServiceName": "SERVICE-NAME.amazonaws.com"}}
        },
        {
            "Effect": "Allow",
            "Action": [
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy"
            ],
            "Resource": "arn:aws:iam::*:role/aws-service-role/SERVICE-NAME.amazonaws.com/SERVICE-LINKED-ROLE-NAME-PREFIX*"
        }
    ]
}
```

**To allow an IAM entity to create any service\-linked role**

Add the following statement to the permissions policy for the IAM entity that needs to create a service\-linked role, or any service role that includes the needed policies\. This policy statement does not allow the IAM entity to attach a policy to the role\.

```
{
    "Effect": "Allow",
    "Action": "iam:CreateServiceLinkedRole",
    "Resource": "arn:aws:iam::*:role/aws-service-role/*"
}
```

**To allow an IAM entity to edit the description of any service roles**

Add the following statement to the permissions policy for the IAM entity that needs to edit the description of a service\-linked role, or any service role\.

```
{
    "Effect": "Allow",
    "Action": "iam:UpdateRoleDescription",
    "Resource": "arn:aws:iam::*:role/aws-service-role/*"
}
```

**To allow an IAM entity to delete a specific service\-linked role**

Add the following statement to the permissions policy for the IAM entity that needs to delete the service\-linked role\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:DeleteServiceLinkedRole",
        "iam:GetServiceLinkedRoleDeletionStatus"
    ],
    "Resource": "arn:aws:iam::*:role/aws-service-role/SERVICE-NAME.amazonaws.com/SERVICE-LINKED-ROLE-NAME-PREFIX*"
}
```

**To allow an IAM entity to delete any service\-linked role**

Add the following statement to the permissions policy for the IAM entity that needs to delete a service\-linked role, but not service role\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:DeleteServiceLinkedRole",
        "iam:GetServiceLinkedRoleDeletionStatus"
    ],
    "Resource": "arn:aws:iam::*:role/aws-service-role/*"
}
```

**To allow an IAM entity to pass an existing role to the service**

Some AWS services allow you to pass an existing role to the service, instead of creating a new service\-linked role\. To do this, a user must have permissions to *pass the role* to the service\. Add the following statement to the permissions policy for the IAM entity that needs to pass a role\. This policy statement also allows the entity to view a list of roles from which they can choose the role to pass\. For more information, see [Granting a user permissions to pass a role to an AWS service](id_roles_use_passrole.md)\.

```
{
    "Effect": "Allow",
    "Action": [
        "iam:ListRoles",
        "iam:PassRole"
    ],
    "Resource": "arn:aws:iam::123456789012:role/my-role-for-XYZ"
}
```

### Transferring service\-linked role permissions<a name="create-service-linked-role-permissions-transfer"></a>

The permissions granted by a service\-linked role are indirectly transferable to other users and roles\. When you allow a service to perform operations in other services, the service can use those permissions in the future\. If another user or role has permission to perform actions in the service, the service can then assume the role and access resources in other services\. This means that the other user or role can indirectly access the other services\.

For example, when you create an Amazon RDS DB instance, [RDS creates the service\-linked role](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.ServiceLinkedRoles.html) for you\. This role allows RDS to call Amazon EC2, Amazon SNS, Amazon CloudWatch Logs, and Amazon Kinesis on your behalf whenever you edit the DB instance\. If you create a policy to allow users and roles in your account or another account to access that Amazon RDS instance, then RDS can still use that role make changes to EC2, SNS, CloudWatch Logs, and Kinesis on their behalf\. The new user or role can indirectly edit resources in those other services\.

## Creating a service\-linked role<a name="create-service-linked-role"></a>

The method that you use to create a service\-linked role depends on the service\. In some cases, you don't need to manually create a service\-linked role\. For example, when you complete a specific action \(such as creating a resource\) in the service, the service might create the service\-linked role for you\. Or if you were using a service before it began supporting service\-linked roles, then the service might have automatically created the role in your account\. To learn more, see [A new role appeared in my AWS account](troubleshoot_roles.md#troubleshoot_roles_new-role-appeared)\.

In other cases, the service might support creating a service\-linked role manually using the service console, API, or CLI\. For information about which services support using service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. To learn whether the service supports creating the service\-linked role, choose the **Yes** link to view the service\-linked role documentation for that service\.

If the service does not support creating the role, then you can use IAM to create the service\-linked role\.

**Important**  
Service\-linked roles count toward your [IAM roles in an AWS account](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html#reference_iam-quotas-entities) limit, but if you have reached your limit, you can still create service\-linked roles in your account\. Only service\-linked roles can exceed the limit\.

### Creating a service\-linked role \(console\)<a name="create-service-linked-role-iam-console"></a>

Before you create a service\-linked role in IAM, find out whether the linked service automatically creates service\-linked roles, In addition, learn whether you can create the role from the service's console, API, or CLI\.

**To create a service\-linked role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\. Then choose **Create role**\.

1. Choose the **AWS Service** role type, and then choose the service that you want to allow to assume this role\.

1. Choose the use case for your service\. If the specified service has only one use case, it is selected for you\. Use cases are defined by the service to include the trust policy required by the service\. Then choose **Next: Permissions**\.

1. Choose one or more permissions policies to attach to the role\. Depending on the use case that you selected, the service might do any of the following:
   + Define the permissions used by the role
   + Allow you to choose from a limited set of permissions
   + Allow you to choose from any permissions
   + Allow you to select no policies at this time, create the policies later, and then attach them to the role\.

   Select the box next to the policy that assigns the permissions that you want the role to have, and then choose **Next: Tags**\. 
**Note**  
The permissions that you specify are available to any entity that uses the role\. By default, a role has no permissions\.

1. Choose **Next: Review**\. You cannot attach tags to service\-linked roles during creation\. For more information about using tags in IAM, see [Tagging IAM users and roles](id_tags.md)\.

1. For **Role name**, the degree of role name customization is defined by the service\. If the service defines the role's name, then this option is not editable\. In other cases, the service might define a prefix for the role and allow you to type an optional suffix\.

   If possible, type a role name suffix to add to the default name\. This suffix helps you identify the purpose of this role\. Role names must be unique within your AWS account\. They are not distinguished by case\. For example, you cannot create roles named both **<service\-linked\-role\-name>\_SAMPLE** and **<service\-linked\-role\-name>\_sample**\. Because various entities might reference the role, you cannot edit the name of the role after it has been created\.

1. \(Optional\) For **Role description**, edit the description for the new service\-linked role\.

1. Review the role and then choose **Create role**\.

### Creating a service\-linked role \(AWS CLI\)<a name="create-service-linked-role-iam-cli"></a>

Before creating a service\-linked role in IAM, find out whether the linked service automatically creates service\-linked roles and whether you can create the role from the service's CLI\. If the service CLI is not supported, you can use IAM commands to create a service\-linked role with the trust policy and inline policies that the service needs to assume the role\.

**To create a service\-linked role \(AWS CLI\)**

Run the following command:

```
aws iam [create\-service\-linked\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/create-service-linked-role.html) --aws-service-name SERVICE-NAME.amazonaws.com
```

### Creating a service\-linked role \(AWS API\)<a name="create-service-linked-role-iam-api"></a>

Before creating a service\-linked role in IAM, find out whether the linked service automatically creates service\-linked roles and whether you can create the role from the service's API\. If the service API is not supported, you can use the AWS API to create a service\-linked role with the trust policy and inline policies that the service needs to assume the role\.

**To create a service\-linked role \(AWS API\)**

Use the [CreateServiceLinkedRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateServiceLinkedRole.html) API call\. In the request, specify a service name of `SERVICE_NAME_URL.amazonaws.com`\. 

For example, to create the **Lex Bots** service\-linked role, use `lex.amazonaws.com`\.

## Editing a service\-linked role<a name="edit-service-linked-role"></a>

The method that you use to edit a service\-linked role depends on the service\. Some services might allow you to edit the permissions for a service\-linked role from the service console, API, or CLI\. However, after you create a service\-linked role, you cannot change the name of the role because various entities might reference the role\. You can edit the description of any role from the IAM console, API, or CLI\.

For information about which services support using service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. To learn whether the service supports editing the service\-linked role, choose the **Yes** link to view the service\-linked role documentation for that service\.

### Editing a service\-linked role description \(console\)<a name="edit-service-linked-role-iam-console"></a>

You can use the IAM console to edit the description of a service\-linked role\.

**To edit the description of a service\-linked role \(console\)**

1. In the navigation pane of the IAM console, choose **Roles**\.

1. Choose the name of the role to modify\.

1. To the far right of **Role description**, choose **Edit**\. 

1. Type a new description in the box and choose **Save**\.

### Editing a service\-linked role description \(AWS CLI\)<a name="edit-service-linked-role-iam-cli"></a>

You can use IAM commands from the AWS CLI to edit the description of a service\-linked role\.

**To change the description of a service\-linked role \(AWS CLI\)**

1. \(Optional\) To view the current description for a role, run the following commands:

   ```
   aws iam [get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html) --role-name ROLE-NAME
   ```

   Use the role name, not the ARN, to refer to roles with the CLI commands\. For example, if a role has the following ARN: `arn:aws:iam::123456789012:role/myrole`, you refer to the role as **myrole**\.

1. To update a service\-linked role's description, run the following command:

   ```
   aws iam [update\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/update-role.html) --role-name ROLE-NAME --description OPTIONAL-DESCRIPTION
   ```

### Editing a service\-linked role description \(AWS API\)<a name="edit-service-linked-role-iam-api"></a>

You can use the AWS API to edit the description of a service\-linked role\.

**To change the description of a service\-linked role \(AWS API\)**

1. \(Optional\) To view the current description for a role, call the following operation, and specify the name of the role:

   AWS API: [GetRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetRole.html) 

1. To update a role's description, call the following operation, and specify the name \(and optional description\) of the role: 

   AWS API: [UpdateRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_UpdateRole.html) 

## Deleting a service\-linked role<a name="delete-service-linked-role"></a>

The method that you use to create a service\-linked role depends on the service\. In some cases, you don't need to manually delete a service\-linked role\. For example, when you complete a specific action \(such as removing a resource\) in the service, the service might delete the service\-linked role for you\. 

In other cases, the service might support deleting a service\-linked role manually from the service console, API, or CLI\. 

For information about which services support using service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. To learn whether the service supports deleting the service\-linked role, choose the **Yes** link to view the service\-linked role documentation for that service\.

If the service does not support deleting the role, then you can delete the service\-linked role from the IAM console, API, or CLI\. If you no longer need to use a feature or service that requires a service\-linked role, we recommend that you delete that role\. That way you don't have an unused entity that is not actively monitored or maintained\. However, you must clean up your service\-linked role before you can delete it\.

### Cleaning up a service\-linked role<a name="service-linked-role-review-before-delete"></a>

Before you can use IAM to delete a service\-linked role, you must first confirm that the role has no active sessions and remove any resources used by the role\.

**To check whether the service\-linked role has an active session in the IAM console**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\. Then choose the name \(not the check box\) of the service\-linked role\.

1. On the **Summary** page for the selected role, choose the **Access Advisor** tab\.

1. On the **Access Advisor** tab, review recent activity for the service\-linked role\.
**Note**  
If you are unsure whether the service is using the service\-linked role, you can try to delete the role\. If the service is using the role, then the deletion fails and you can view the regions where the role is being used\. If the role is being used, then you must wait for the session to end before you can delete the role\. You cannot revoke the session for a service\-linked role\. 

**To remove resources used by a service\-linked role**

For information about which services support using service\-linked roles, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. To learn whether the service supports deleting the service\-linked role, choose the **Yes** link to view the service\-linked role documentation for that service\. See the documentation for that service to learn how to remove resources used by your service\-linked role\.

### Deleting a service\-linked role \(console\)<a name="delete-service-linked-role-iam-console"></a>

You can use the IAM console to delete a service\-linked role\.

**To delete a service\-linked role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane of the IAM console, choose **Roles**\. Then select the check box next to the role name that you want to delete, not the name or row itself\. 

1. For **Role actions** at the top of the page, choose **Delete role**\.

1. In the confirmation dialog box, review the last accessed information, which shows when each of the selected roles last accessed an AWS service\. This helps you to confirm whether the role is currently active\. If you want to proceed, choose **Yes, Delete** to submit the service\-linked role for deletion\.

1. Watch the IAM console notifications to monitor the progress of the service\-linked role deletion\. Because the IAM service\-linked role deletion is asynchronous, after you submit the role for deletion, the deletion task can succeed or fail\. 
   + If the task succeeds, then the role is removed from the list and a notification of success appears at the top of the page\.
   + If the task fails, you can choose **View details** or **View Resources** from the notifications to learn why the deletion failed\. If the deletion fails because the role is using the service's resources, then the notification includes a list of resources, if the service returns that information\. You can then [clean up the resources](#service-linked-role-review-before-delete) and submit the deletion again\.
**Note**  
You might have to repeat this process several times, depending on the information that the service returns\. For example, your service\-linked role might use six resources and your service might return information about five of them\. If you clean up the five resources and submit the role for deletion again, the deletion fails and the service reports the one remaining resource\. A service might return all of the resources, a few of them, or it might not report any resources\.
   + If the task fails and the notification does not include a list of resources, then the service might not return that information\. To learn how to clean up the resources for that service, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. Find your service in the table, and choose the **Yes** link to view the service\-linked role documentation for that service\.

### Deleting a service\-linked role \(AWS CLI\)<a name="delete-service-linked-role-iam-cli"></a>

You can use IAM commands from the AWS CLI to delete a service\-linked role\.

**To delete a service\-linked role \(AWS CLI\)**

1. If you don't know the name of the service\-linked role that you want to delete, type the following command to list the roles and their Amazon Resource Names \(ARNs\) in your account:

   ```
   aws iam [get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html) --role-name role-name
   ```

   Use the role name, not the ARN, to refer to roles with the CLI commands\. For example, if a role has the following ARN: `arn:aws:iam::123456789012:role/myrole`, you refer to the role as **myrole**\.

1. Because a service\-linked role cannot be deleted if it is being used or has associated resources, you must submit a deletion request\. That request can be denied if these conditions are not met\. You must capture the `deletion-task-id` from the response to check the status of the deletion task\. Type the following command to submit a service\-linked role deletion request:

   ```
   aws iam [delete\-service\-linked\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/delete-service-linked-role.html) --role-name role-name
   ```

1. Type the following command to check the status of the deletion task:

   ```
   aws iam [get\-service\-linked\-role\-deletion\-status](https://docs.aws.amazon.com/cli/latest/reference/iam/get-service-linked-role-deletion-status.html) --deletion-task-id deletion-task-id
   ```

   The status of the deletion task can be `NOT_STARTED`, `IN_PROGRESS`, `SUCCEEDED`, or `FAILED`\. If the deletion fails, the call returns the reason that it failed so that you can troubleshoot\. If the deletion fails because the role is using the service's resources, then the notification includes a list of resources, if the service returns that information\. You can then [clean up the resources](#service-linked-role-review-before-delete) and submit the deletion again\.
**Note**  
You might have to repeat this process several times, depending on the information that the service returns\. For example, your service\-linked role might use six resources and your service might return information about five of them\. If you clean up the five resources and submit the role for deletion again, the deletion fails and the service reports the one remaining resource\. A service might return all of the resources, a few of them, or it might not report any resources\. To learn how to clean up the resources for a service that does not report any resources, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. Find your service in the table, and choose the **Yes** link to view the service\-linked role documentation for that service\.

### Deleting a service\-linked role \(AWS API\)<a name="delete-service-linked-role-iam-api"></a>

You can use the AWS API to delete a service\-linked role\.

**To delete a service\-linked role \(AWS API\)**

1. To submit a deletion request for a service\-linked role, call [DeleteServiceLinkedRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteServiceLinkedRole.html)\. In the request, specify a role name\.

   Because a service\-linked role cannot be deleted if it is being used or has associated resources, you must submit a deletion request\. That request can be denied if these conditions are not met\. You must capture the `DeletionTaskId` from the response to check the status of the deletion task\.

1. To check the status of the deletion, call [GetServiceLinkedRoleDeletionStatus](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLinkedRoleDeletionStatus.html)\. In the request, specify the `DeletionTaskId`\.

   The status of the deletion task can be `NOT_STARTED`, `IN_PROGRESS`, `SUCCEEDED`, or `FAILED`\. If the deletion fails, the call returns the reason that it failed so that you can troubleshoot\. If the deletion fails because the role is using the service's resources, then the notification includes a list of resources, if the service returns that information\. You can then [clean up the resources](#service-linked-role-review-before-delete) and submit the deletion again\.
**Note**  
You might have to repeat this process several times, depending on the information that the service returns\. For example, your service\-linked role might use six resources and your service might return information about five of them\. If you clean up the five resources and submit the role for deletion again, the deletion fails and the service reports the one remaining resource\. A service might return all of the resources, a few of them, or it might not report any resources\. To learn how to clean up the resources for a service that does not report any resources, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\. Find your service in the table, and choose the **Yes** link to view the service\-linked role documentation for that service\.