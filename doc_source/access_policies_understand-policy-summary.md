# Policy summary \(list of services\)<a name="access_policies_understand-policy-summary"></a>

Policies are summarized in three tables: the policy summary, the [service summary](access_policies_understand-service-summary.md), and the [action summary](access_policies_understand-action-summary.md)\. The *policy summary* table includes a list of services and summaries of the permissions that are defined by the chosen policy\. 

![\[Policy summaries diagram image that illustrates the 3 tables and their relationship\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_summaries-pol-sum.png)

The policy summary table is grouped into one or more **Uncategorized services**, **Explicit deny**, and **Allow** sections\. If the policy includes a service that IAM does not recognize, then the service is included in the **Uncategorized services** section of the table\. If IAM recognizes the service, then it is included under the **Explicit deny** or **Allow** sections of the table, depending on the effect of the policy \(`Deny` or `Allow`\)\.

## Viewing policy summaries<a name="viewing-policy-summaries"></a>

You can view the summaries for any policies that are attached to a user on the **Users** page\. You can view the summaries for any policies that are attached to a role on the **Roles** page\. You can view the policy summary for managed policies on the **Policies** page\. If your policy does not include a policy summary, see [Missing policy summary](troubleshoot_policies.md#missing-policy-summary) to learn why\.

**To view the policy summary from the **Policies** page**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies**\.

1. In the list of policies, choose the name of the policy that you want to view\.

1. On the **Summary** page for the policy, view the **Permissions** tab to see the policy summary\.

**To view the summary for a policy attached to a user**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Users** from the navigation pane\.

1. In the list of users, choose the name of the user whose policy you want to view\.

1. On the **Summary** page for the user, view the **Permissions** tab to see the list of policies that are attached to the user directly or from a group\.

1. In the table of policies for the user, expand the row of the policy that you want to view\.

**To view the summary for a policy attached to a role**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Roles**\.

1. In the list of roles, choose the name of the role whose policy you want to view\.

1. On the **Summary** page for the role, view the **Permissions** tab to see the list of policies that are attached to the role\.

1. In the table of policies for the role, expand the row of the policy that you want to view\.

## Editing policies to fix warnings<a name="edit-policy-summary"></a>

While viewing a policy summary, you might find a typo or notice that the policy does not provide the permissions that you expected\. You cannot edit a policy summary directly\. However, you can edit a managed policy using the visual policy editor, which catches many of the same errors and warnings that the policy summary reports\. You can then view the changes in the policy summary to confirm that you fixed all of the issues\. To learn how to edit an inline policy, see [Editing IAM policies](access_policies_manage-edit.md)\. You cannot edit AWS managed policies\.

**To edit a policy for your policy summary using the **Visual editor** tab**

1. Open the policy summary as explained in the previous procedures\.

1. Choose **Edit policy**\.

   If you are on the **Users** page and choose to edit a customer managed policy that is attached to that user, you are redirected to the **Policies** page\. You can edit customer managed policies only on the **Policies** page\.

1. Choose the **Visual editor** tab to view the editable visual representation of your policy\. IAM might restructure your policy to optimize it for the visual editor and to make it easier for you to find and fix any problems\. The warnings and error messages on the page can guide you to fix any issues with your policy\. For more information about how IAM restructures policies, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

1. Edit your policy and choose **Review policy** to see your changes reflected in the policy summary\. If you still see a problem, choose **Previous** to return to the editing screen\.

1. Choose **Save** to save your changes\.

**To edit a policy for your policy summary using the **JSON** tab**

1. Open the policy summary as explained in the previous procedures\.

1. Choose **\{ \} JSON** and **Policy summary** to compare the policy summary to the JSON policy document\. You can use this information to determine which lines in the policy document you want to change\.

1. Choose **Edit policy** and then choose the **JSON** tab to edit the JSON policy document\.
**Note**  
You can switch between the **Visual editor** and **JSON** tabs any time\. However, if you make changes or choose **Review policy** in the **Visual editor** tab, IAM might restructure your policy to optimize it for the visual editor\. For more information, see [Policy restructuring](troubleshoot_policies.md#troubleshoot_viseditor-restructure)\.

   If you are on the **Users** page and choose to edit a customer managed policy that is attached to that user, you are redirected to the **Policies** page\. You can edit customer managed policies only on the **Policies** page\.

1. Edit your policy and choose **Review policy** to see your changes reflected in the policy summary\. If you still see a problem, choose **Previous** to return to the editing screen\.

1. Choose **Save** to save your changes\.

## Understanding the elements of a policy summary<a name="understanding-elements-policy-summary"></a>

In the following example of a user details page, the **PolSumUser** user has eight attached policies\. The **SummaryAllElements** policy is a managed policy \(customer managed policy\) that is attached directly to the user\. This policy is expanded to show the policy summary\. To view the JSON policy document for this policy, see [**SummaryAllElements** JSON policy document](#policy-summary-example-json)\.

![\[Policy summary dialog image\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-summary-user-page-dialog.png)

In the preceding image, the policy summary is visible from within the user details page:

1. The **Permissions** tab for a user includes the policies that are attached to the **PolSumUser** user\.

1. The **SummaryAllElements** policy is one of several policies that are attached to the user\. The policy is expanded in order to view the policy summary\.

1. If the policy does not grant permissions to all the actions, resources, and conditions defined in the policy, then a warning or error banner appears at the top of the page\. The policy summary then includes details about the problem\. To learn how policy summaries help you to understand and troubleshoot the permissions that your policy grants, see [My policy does not grant the expected permissions](troubleshoot_policies.md#policy-summary-not-grant-permissions)\.

1. Use the **Policy summary** and **\{ \} JSON** buttons to toggle between the policy summary and the JSON policy document\.

1. **Simulate policy** opens the policy simulator for testing the policy\.

1.  Use the search box to reduce the list of services and easily find a specific service\.

1. The expanded view shows additional details of the **SummaryAllElements** policy\.

The following policy summary table image shows the expanded **SummaryAllElements** policy on the **PolSumUser** user details page\.

![\[Policy summary dialog image\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-summary-table-dialog.png)

In the preceding image, the policy summary is visible from within the user details page:

1. **Service** – This column lists the services that are defined within the policy and provides details for each service\. Each service name in the policy summary table is a link to the *service summary* table, which is explained in [Service summary \(list of actions\)](access_policies_understand-service-summary.md)\. In this example, permissions are defined for the Amazon S3, Billing, and Amazon EC2 services\. The policy also defines permissions for a \(misspelled\) `codedploy` service, which IAM does not recognize\.

1. **Unrecognized services** – This policy includes an unrecognized service \(in this case **codedploy ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png)**\)\. You can use this warning to check whether a service name might include a typo\. If the service name is correct, then the service might not support policy summaries, might be in preview, or might be a custom service\. To request policy summary support for a generally available \(GA\) service, see [Service does not support IAM policy summaries](troubleshoot_policies.md#unsupported-services-actions)\. In this example, the policy includes an unrecognized `codedploy` service that is missing an `e`\. Because of this typo, the policy does not provide the expected AWS CodeDeploy permissions\. You can [edit the policy](#edit-policy-summary) to include the accurate `codedeploy` service name; the service then appears in the policy summary\.

1. For those services that IAM recognizes, it arranges services according to whether the policy allows or explicitly denies the use of the service\. In this example, the policy includes `Allow` and `Deny` statements for the Amazon S3 service\. Therefore the policy summary includes S3 within both the **Explicit deny** and **Allow** sections\.

1. **Show remaining 100** – Choose this link to expand the table to include the services that are not defined by the policy\. These services are *implicitly denied* \(or denied by default\) within this policy\. However, a statement in another policy might still allow or explicitly deny using the service\. The policy summary summarizes the permissions of a single policy\. To learn about how the AWS service decides whether a given request should be allowed or denied, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.

1. **EC2 ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png)** – This service includes an unrecognized action\. IAM recognizes service names, actions, and resource types for services that support policy summaries\. When a service is recognized but contains an action that is not recognized, IAM includes a warning next to that service\. In this example, IAM can't recognize at least one Amazon EC2 action\. To learn more about unrecognized actions and to view the unrecognized action in an S3 service summary, see [Service summary \(list of actions\)](access_policies_understand-service-summary.md)\.
**Note**  
IAM reviews service names, actions, and resource types for services that support policy summaries\. However, your policy summary might include a resource value or condition that does not exist\. Always test your policies with the [policy simulator](access_policies_testing-policies.md)\.

1. **S3 ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png)** – This service includes an unrecognized resource\. IAM recognizes service names, actions, and resource types for services that support policy summaries\. When a service is recognized but contains a resource type that is not recognized, IAM includes a warning next to that service\. In this example, IAM can't recognize at least one Amazon S3 action\. To learn more about unrecognized resources and to view the unrecognized resource type in an S3 service summary, see [Service summary \(list of actions\)](access_policies_understand-service-summary.md)\.

1. **Access level** – This column tells whether the actions in each access level \(`List`, `Read`, `Write`, and `Permissions management`\) have `Full` or `Limited` permissions defined in the policy\. For additional details and examples of the access level summary, see [Understanding access level summaries within policy summaries](access_policies_understand-policy-summary-access-level-summaries.md)\.
   + **Full access** – This entry indicates that the service has access to all actions within all four of the access levels available for the service\. In this example, because this row is in the **Explicit deny** section of the table, all Amazon S3 actions are denied for the resources included in the policy\.
   + <a name="full-vs-limited-access-summary"></a>If the entry does not include **Full access**, then the service has access to some but not all of the actions for the service\. The access is then defined by following descriptions for each of the four access level classifications \(`List`, `Read`, `Write`, and `Permissions management`\):

     **Full**: The policy provides access to all actions within each access level classification listed\. In this example, the policy provides access to all of the Billing `Read` actions\.

     **Limited**: The policy provides access to one or more but not all actions within each access level classification listed\. In this example, the policy provides access to some of the Billing `Write` actions\.

1. **Resource** – This column shows the resources that the policy specifies for each service\. 
   + **Multiple** – The policy includes more than one but not all of the resources within the service\. In this example, access is explicitly denied to more than one Amazon S3 resource\.
   + **All resources** –\- The policy is defined for all resources within the service\. In this example, the policy allows the listed actions to be performed on all Billing resources\.
   + Resource text – The policy includes one resource within the service\. In this example, the listed actions are allowed on only the `developer_bucket` Amazon S3 bucket resource\. Depending on the information that the service provides to IAM, you might see an ARN such as `arn:aws:s3:::developer_bucket/*`, or you might see the defined resource type, such as `BucketName = developer_bucket`\.
**Note**  
This column can include a resource from a different service\. If the policy statement that includes the resource does not include both actions and resources from the same service, then your policy includes mismatched resources\. IAM does not warn you about mismatched resources when you create a policy, or when you view a policy in the policy summary\. If this column includes a mismatched resource, then you should review your policy for errors\. To better understand your policies, always test them with the [policy simulator](access_policies_testing-policies.md)\.

1. **Request condition** – This column indicates whether the services or actions associated with the resource are subject to conditions\.
   + **None** – The policy includes no conditions for the service\. In this example no conditions are applied to the denied actions in the Amazon S3 service\.
   + Condition text – The policy includes one condition for the service\. In this example, the listed **Billing** actions are allowed only if the IP address of the source matches `203.0.113.0/24`\.
   + **Multiple** – The policy includes more than one condition for the service\. In this example, access to the listed Amazon S3 actions is allowed based on more than one condition\. To view each of the multiple conditions for the policy, choose **\{ \} JSON** to view the policy document\.

When a policy or an element within the policy does not grant permissions, IAM provides additional warnings and information in the policy summary\. The following policy summary table shows the expanded **Show remaining 100** services on the **PolSumUser** user details page with the possible warnings\.

![\[Policy summary dialog image\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policies-summary-table-showremaining-dialog.png)

In the preceding image, you can see all services that include defined actions, resources, or conditions with no permissions:

1. **Resource warnings** – For services that do not provide permissions for all of the included actions or resources, you see one of the following warnings in the **Resource** column of the table:
   + **![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) No resources are defined\.** – This means that the service has defined actions but no supported resources are included in the policy\.
   + **![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) One or more actions do not have an applicable resource\.** – This means that the service has defined actions, but that some of those actions don't have a supported resource\.
   + **![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) One or more resources do not have an applicable action\.** – This means that the service has defined resources, but that some of those resources don't have a supporting action\.

   If a service includes both actions that do not have an applicable resource and resources that do not have an applicable resource, then only the **One or more resources do not have an applicable action\.** warning is shown\. This is because when you view the service summary for the service, resources that do not apply to any action are not shown\. For the `ListAllMyBuckets` action, this policy includes the last warning because the action does not support resource\-level permissions, and does not support the `s3:x-amz-acl` condition key\. If you fix either the resource problem or the condition problem, the remaining issue appears in a detailed warning\.

1. **Request condition warnings** – For services that do not provide permissions for all of the included conditions, you see one of the following warnings in the **Request condition** column of the table:
   + **![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) One or more actions do not have an applicable condition\.** – This means that the service has defined actions, but that some of those actions don't have a supported condition\.
   + **![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) One or more conditions do not have an applicable action\.** – This means that the service has defined conditions, but that some of those conditions don't have a supporting action\.

1. **Multiple \| ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) One or more actions do not have an applicable resource\.** – The `Deny` statement for Amazon S3 includes more than one resource\. It also includes more than one action, and some actions support the resources and some do not\. To view this policy, see [**SummaryAllElements** JSON policy document](#policy-summary-example-json)\. In this case, the policy includes all Amazon S3 actions, and only the actions that can be performed on a bucket or bucket object are denied\.

1. The ellipses \(…\) indicate that all the services are included in the page, but we are showing only the rows with information relevant to this policy\. When you view this page in the AWS Management Console, you see all the AWS services\.

1. The background color in the table rows indicates services that do not grant any permissions\. You cannot get any additional information about these services in the policy summary\. For services in white rows, you can choose the name of the service to view the service summary \(list of actions\) page\. There you can learn more about the permissions granted for that service\.

1. **![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) None \- No actions are defined\.** – This means that the service is defined as a resource or condition, but that no actions are included for the service, and therefore the service provides no permissions\. In this case, the policy includes a CodeBuild resource but no CodeBuild actions\.

1. **![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) No resources are defined** – The service has defined actions, but no supported resources are included in the policy, and therefore the service provides no permissions\. In this case, the policy includes CodeCommit actions but no CodeCommit resources\.

1. **BucketName = developer\_bucket, ObjectPath = All \| ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) One or more resources do not have an applicable action\.** – The service has a defined bucket object resource, and at least one more resource that does not have a supporting action\.

1. **s3:x\-amz\-acl = public\-read \| ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/console-alert-icon.console.png) One or more conditions do not have an applicable action\.** – The service has a defined `s3:x-amz-acl` condition key, and at least one more condition key that does not have a supporting action\.

## **SummaryAllElements** JSON policy document<a name="policy-summary-example-json"></a>

The **SummaryAllElements** policy is not intended for you to use to define permissions in your account\. Rather, it is included to demonstrate the errors and warnings that you might encounter while viewing a policy summary\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "aws-portal:ViewBilling",
                "aws-portal:ViewPaymentMethods",
                "aws-portal:ModifyPaymentMethods",
                "aws-portal:ViewAccount",
                "aws-portal:ModifyAccount",
                "aws-portal:ViewUsage"
            ],
            "Resource": [
                "*"
            ],
            "Condition": {
                "IpAddress": {
                    "aws:SourceIp": "203.0.113.0/24"
                }
            }
        },
        {
            "Effect": "Deny",
            "Action": [
                "s3:*"
            ],
            "Resource": [
                "arn:aws:s3:::customer",
                "arn:aws:s3:::customer/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:GetConsoleScreenshots"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "codedploy:*",
                "codecommit:*"
            ],
            "Resource": [
                "arn:aws:codedeploy:us-west-2:123456789012:deploymentgroup:*",
                "arn:aws:codebuild:us-east-1:123456789012:project/my-demo-project"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListAllMyBuckets",
                "s3:GetObject",
                "s3:DeletObject",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Resource": [
                "arn:aws:s3:::developer_bucket",
                "arn:aws:s3:::developer_bucket/*",
                "arn:aws:autoscling:us-east-2:123456789012:autoscalgrp"
            ],
            "Condition": {
                "StringEquals": {
                    "s3:x-amz-acl": [
                        "public-read"
                    ],
                    "s3:prefix": [
                        "custom",
                        "other"
                    ]
                }
            }
        }
    ]
}
```