# Deleting roles or instance profiles<a name="id_roles_manage_delete"></a>

If you no longer need a role, we recommend that you delete the role and its associated permissions\. That way you don't have an unused entity that is not actively monitored or maintained\. 

If the role was associated with an EC2 instance, you can also remove the role from the instance profile and then delete the instance profile\.

**Warning**  
Make sure that you do not have any Amazon EC2 instances running with the role or instance profile you are about to delete\. Deleting a role or instance profile that is associated with a running instance will break any applications that are running on the instance\.

If you prefer not to permanently delete a role, you can disable a role\. To do this, change the role's policies and then revoke all current sessions\. For example, you could add a policy to the role that denied access to all of AWS\. You could also edit the trust policy to deny access to anyone attempting to assume the role\. For more information about revoking sessions, see [Revoking IAM role temporary security credentials](id_roles_use_revoke-sessions.md)\.

**Topics**
+ [View role access](#roles-delete_prerequisites)
+ [Deleting a service\-linked role](#id_roles_manage_delete_slr)
+ [Deleting an IAM role \(console\)](#roles-managingrole-deleting-console)
+ [Deleting an IAM role \(AWS CLI\)](#roles-managingrole-deleting-cli)
+ [Deleting an IAM role \(AWS API\)](#roles-managingrole-deleting-api)
+ [Related information](#roles-managingrole-deleting-related-info)

## View role access<a name="roles-delete_prerequisites"></a>

Before you delete a role, we recommend that you review when the role was last used\. You can do this using the AWS Management Console, the AWS CLI, or the AWS API\. It's important to view this information because you don't want to remove access from someone who is using it\. 

The date of the role's last activity might not match the last date reported in the **Access Advisor** tab\. The [**Access Advisor**](access_policies_access-advisor-view-data.md) tab reports activity only for services that are allowed by the role's permissions policies\. The date of the role's last activity includes the last attempt to access any service in AWS\. 

**Note**  
The tracking period for a role's last activity and Access Advisor data is for the trailing 400 days\. This period can be shorter if your Region began supporting these features within the last year\. The role might have been used more than 400 days ago\. For more information about the tracking period, see [Where AWS tracks last accessed information](access_policies_access-advisor.md#access-advisor_tracking-period)\.

**To view when a role was last used \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles**\.

1. Find the row of the role whose activity you want to view\. You can use the search field to narrow the results\. View the **Last activity** column to see the number of days since the role was last used\. If the role has not been used within the tracking period, then the table displays **None**\. 

1. Choose the name of the role to view more information\. The role's ** Summary** page also includes **Last activity**, which displays the date that the role was last used\. If the role has not been used within the last 400 days, then **Last activity** displays **Not accessed in the tracking period**\.

**To view when a role was last used \(AWS CLI\)**  
`[aws iam get\-role](https://docs.aws.amazon.com/cli/latest/reference/iam/get-role.html)` \- Run this command to return information about a role, including the `RoleLastUsed` object\. This object contains the `LastUsedDate` and the `Region` in which the role was last used\. If `RoleLastUsed` is present but does not contain a value, then the role has not been used within the tracking period\.

**To view when a role was last used \(AWS API\)**  
`[GetRole](https://docs.aws.amazon.com/IAM/latest/APIReference/GetRole.html)` \- Call this operation to return information about a role, including the `RoleLastUsed` object\. This object contains the `LastUsedDate` and the `Region` in which the role was last used\. If `RoleLastUsed` is present but does not contain a value, then the role has not been used within the tracking period\.

## Deleting a service\-linked role<a name="id_roles_manage_delete_slr"></a>

If the role is a *[service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role)*, review the documentation for the linked service to learn how to delete the role\. You can view the service\-linked roles in your account by going to the IAM **Roles** page in the console\. Service\-linked roles appear with **\(Service\-linked role\)** in the **Trusted entities** column of the table\. A banner on the role's **Summary** page also indicates that the role is a service\-linked role\.

If the service does not include documentation for deleting the service\-linked role, you can use the IAM console, AWS CLI, or API to delete the role\. For more information, see [Deleting a service\-linked role](using-service-linked-roles.md#delete-service-linked-role)\.

## Deleting an IAM role \(console\)<a name="roles-managingrole-deleting-console"></a>

When you use the AWS Management Console to delete a role, IAM also automatically deletes the policies associated with the role\. It also deletes any Amazon EC2 instance profile that contains the role\.

**Important**  
In some cases, a role might be associated with an Amazon EC2 instance profile, and the role and the instance profile might have the same name\. In that case you can use the AWS Management Console to delete the role and the instance profile\. This linkage happens automatically for roles and instance profiles that you create in the console\. If you created the role from the AWS CLI, Tools for Windows PowerShell, or the AWS API, then the role and the instance profile might have different names\. In that case you cannot use the console to delete them\. Instead, you must use the AWS CLI, Tools for Windows PowerShell, or AWS API to first remove the role from the instance profile\. You must then take a separate step to delete the role\.

**To delete a role \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles**, and then select the check box next to the role name that you want to delete\. 

1. At the top of the page, choose **Delete role**\.

1. In the confirmation dialog box, review the last accessed information, which shows when each of the selected roles last accessed an AWS service\. This helps you to confirm whether the role is currently active\. If you want to proceed, choose **Yes, Delete**\. If you are sure, you can proceed with the deletion even if the last accessed information is still loading\.

**Note**  
You cannot use the console to delete an instance profile unless it has the same name as the role\. In addition, you must delete the instance profile as part of the process of deleting a role as described in the preceding procedure\. To delete an instance profile without also deleting the role, you must use the AWS CLI or AWS API\. For more information, see the following sections\.

## Deleting an IAM role \(AWS CLI\)<a name="roles-managingrole-deleting-cli"></a>

When you use the AWS CLI to delete a role, you must first delete the policies that are associated with the role\. Also, if you want to delete the associated instance profile that contains the role, you must delete it separately\.

**To delete a role \(AWS CLI\)**

1. If you don't know the name of the role that you want to delete, enter the following command to list the roles in your account:

   ```
   aws iam list-roles
   ```

   The list includes the Amazon Resource Name \(ARN\) of each role\. Use the role name, not the ARN, to refer to roles with the CLI commands\. For example, if a role has the following ARN: `arn:aws:iam::123456789012:role/myrole`, you refer to the role as **myrole**\.

1. Remove the role from all instance profiles that the role is in\.

   1. To list all instance profiles that the role is associated with, enter the following command:

      ```
      aws iam list-instance-profiles-for-role --role-name role-name
      ```

   1. To remove the role from an instance profile, enter the following command for each instance profile:

      ```
      aws iam remove-role-from-instance-profile --instance-profile-name instance-profile-name --role-name role-name
      ```

1. Delete all policies that are associated with the role\.

   1. To list all policies that are in the role, enter the following command:

      ```
      aws iam list-role-policies --role-name role-name
      ```

   1. To delete each policy from the role, enter the following command for each policy: 

      ```
      aws iam delete-role-policy --role-name role-name --policy-name policy-name
      ```

1. Enter the following command to delete the role:

   ```
   aws iam delete-role --role-name role-name
   ```

1. If you do not plan to reuse the instance profiles that were associated with the role, you can enter the following command to delete them:

   ```
   aws iam delete-instance-profile --instance-profile-name instance-profile-name
   ```

## Deleting an IAM role \(AWS API\)<a name="roles-managingrole-deleting-api"></a>

When you use the IAM API to delete a role, you must first delete the policies associated with the role\. Also, if you want to delete the associated instance profile that contains the role, you must delete it separately\.

**To delete a role \(AWS API\)**

1. To list all instance profiles that a role is in, call [ListInstanceProfilesForRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListInstanceProfilesForRole.html)\.

   To remove the role from all instance profiles that the role is in, call [RemoveRoleFromInstanceProfile](https://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveRoleFromInstanceProfile.html)\. You must pass the role name and instance profile name\. 

   If you are not going to reuse an instance profile that was associated with the role, call [DeleteInstanceProfile](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteInstanceProfile.html) to delete it\.

1. To list all policies for a role, call [ListRolePolicies](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListRolePolicies.html)\.

   To delete all policies that are associated with the role, call [DeleteRolePolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteRolePolicy.html)\. You must pass the role name and policy name\. 

1. Call [DeleteRole](https://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteRole.html) to delete the role\.

## Related information<a name="roles-managingrole-deleting-related-info"></a>

For general information about instance profiles, see [Using instance profiles](id_roles_use_switch-role-ec2_instance-profiles.md)\.

For general information about service\-linked roles, see [Using service\-linked roles](using-service-linked-roles.md)\.