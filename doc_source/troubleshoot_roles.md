# Troubleshooting IAM Roles<a name="troubleshoot_roles"></a>

Use the information here to help you diagnose and fix common issues that you might encounter when working with IAM roles\.

**Topics**
+ [I Can't Assume a Role](#troubleshoot_roles_cant-assume-role)
+ [A New Role Appeared in My AWS Account](#troubleshoot_roles_new-role-appeared)
+ [I Can't Edit or Delete a Role in My AWS Account](#troubleshoot_roles_cant-edit-delete-role)

## I Can't Assume a Role<a name="troubleshoot_roles_cant-assume-role"></a>
+ Verify that your IAM policy grants you permission to call `sts:AssumeRole` for the role that you want to assume\. The `Action` element of your IAM policy must allow you to call the `AssumeRole` action, and the `Resource` element of your IAM policy must specify the role that you want to assume\. For example, the `Resource` element can specify a role by its Amazon Resource Name \(ARN\) or by using a wildcard \(\*\)\. For example, at least one policy applicable to you must grant permissions similar to the following:

  ```
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Resource": "arn:aws:iam::account_id_number:role/role-name-you-want-to-assume"
  ```
+ Verify that you meet all the conditions that are specified in the role's trust policy\. A `Condition` can specify an expiration date, an external ID, or that a request must come only from specific IP addresses\. In the following example, if the current date is any time after the specified date, then the policy never matches and cannot grant you the permission to assume the role\.

  ```
      "Effect": "Allow",
      "Action": "sts:AssumeRole",
      "Resource": "arn:aws:iam::account_id_number:role/role-name-you-want-to-assume"
      "Condition": {
          "DateLessThan" : {
              "aws:CurrentTime" : "2016-05-01T12:00:00Z"
          }
      }
  ```
+ Verify that the AWS account that you are calling `AssumeRole` from is a trusted entity for the role that you are assuming\. Trusted entities are defined as a `Principal` in a role's trust policy\. The following example is a trust policy attached to the role you want to assume\. In this example, the account ID with the IAM user you signed\-in with must be 123456789012\. If your account number is not listed in the `Principal` element of the role's trust policy, then you cannot assume the role, no matter what permissions are granted to you in access policies\. Note that the example policy limits permissions to actions that occur between July 1, 2017 and December 31, 2017 \(UTC\), inclusive\. If you log in before or after those dates, then the policy does not match, and you cannot assume the role\. 

  ```
      "Effect": "Allow",
      "Principal": { "AWS": "arn:aws:iam::123456789012:root" },
      "Action": "sts:AssumeRole",
      "Condition": {
        "DateGreaterThan": {"aws:CurrentTime": "2017-07-01T00:00:00Z"},
        "DateLessThan": {"aws:CurrentTime": "2017-12-31T23:59:59Z"}
      }
  ```

## A New Role Appeared in My AWS Account<a name="troubleshoot_roles_new-role-appeared"></a>

Some AWS services require that you use a unique type of service role that is linked directly to the service\. This [service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role) is predefined by the service and includes all the permissions that the service requires\. This makes setting up a service easier because you don’t have to manually add the necessary permissions\. For general information about service\-linked roles, see [Using Service\-Linked Roles](using-service-linked-roles.md)\.

You might already be using a service when it begins supporting service\-linked roles\. If so, you might receive an email telling you about a new role in your account\. This role includes all the permissions that the service needs to perform actions on your behalf\. You don't need to take any action to support this role\. However, you should not delete the role from your account\. Doing so could remove permissions that the service needs to access AWS resources\. You can view the service\-linked roles in your account by going to the IAM **Roles** page of the IAM console\. Service\-linked roles appear with **\(Service\-linked role\)** in the **Trusted entities** column of the table\.

For information about which services support service\-linked roles, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. For information about using the service\-linked role for a service, choose the **Yes** link\.

## I Can't Edit or Delete a Role in My AWS Account<a name="troubleshoot_roles_cant-edit-delete-role"></a>

You cannot delete or edit the permissions for a [service\-linked role](id_roles_terms-and-concepts.md#iam-term-service-linked-role) in IAM\. These roles include predefined trusts and permissions that are required by the service in order to perform actions on your behalf\. You can use the IAM console, AWS CLI, or API to edit only the description of a service\-linked role\. You can view the service\-linked roles in your account by going to the IAM **Roles** page in the console\. Service\-linked roles appear with **\(Service\-linked role\)** in the **Trusted entities** column of the table\. A banner on the role's **Summary** page also indicates that the role is a service\-linked role\. You can manage and delete these roles only through the linked service, if that service supports the action\. Be careful when modifying or deleting a service\-linked role because doing so could remove permissions that the service needs to access AWS resources\. 

For information about which services support service\-linked roles, see [AWS Services That Work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. 