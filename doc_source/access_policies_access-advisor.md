# Reducing Policy Scope by Viewing User Activity<a name="access_policies_access-advisor"></a>

The IAM console provides information about when IAM users and roles last attempted to access AWS services\. This information is called *service last accessed data*\. This data can help you identify unnecessary permissions so that you can refine your IAM policies to better adhere to the principle of "least privilege\." That means granting the minimum permissions required to perform a specific task\.

**Note**  
Recent activity usually appears within 4 hours\. Access advisor reports activity for the last 365 days\.

You can get the date and hour when an IAM entity \(user, group, or role\) last accessed an AWS service through IAM policy permissions\. You can use this information to identify unused and not recently used permissions in your IAM policies\. You can then choose to remove permissions for unused services or reorganize users with similar usage patterns into a group to help improve account security\. Knowing if and when an IAM entity last exercised a permission can help you remove unnecessary permissions and tighten your IAM policies with less effort\.

**Important**  
The service last accessed data includes ***all*** attempts to access an AWS API, not just the successful ones\. This includes all access attempts made using the AWS Management Console, the AWS API through any of the SDKs, or any of the command line tools\. An unexpected entry in the service last accessed data does not mean that your account has been compromised, because the request might have been denied\. Refer to your CloudTrail logs as the authoritative source for information about all API calls and whether they were successful or denied access\. For more information, see [Logging IAM Events with AWS CloudTrail](cloudtrail-integration.md)\.

This topic describes the functionality of the IAM service last accessed data and how you can use it with the IAM console\. It also describes two practical scenarios of using the service last accessed data to remove unnecessary permissions from an IAM policy\.

**Topics**
+ [Viewing Access Advisor Information](#access_policies_access-advisor-viewing)
+ [Notes](#access_policies_access-advisor-notes)
+ [Troubleshooting Tips](#access_policies_access-advisor-troubleshooting)
+ [Sample Usage Scenarios](#access_policies_access-advisor-scenarios)
+ [Regions Where Data Is Tracked](#access-advisor_tracking-period)

## Viewing Access Advisor Information<a name="access_policies_access-advisor-viewing"></a>

You can find the data on the **Access Advisor** tab in the IAM console by examining the detail view for any IAM user, group, role, or managed policy\.

**Minimum permissions to see access advisor information**  
Users must have permission to see user, group, role, and policy details in order to view those entities in the IAM console\. However, in order to view the service last accessed data, you must also have permission to use the following actions:  
`iam:GenerateServiceLastAccessedDetails`
`iam:GetServiceLastAccessedDetails`
`iam:GetServiceLastAccessedDetailsWithEntities`
`iam:ListPoliciesGrantingServiceAccess`
Because these actions are not specific to a single resource, administrators should provide access to use these actions on all resources \(`"Resource": "*"`\)\.   
Be aware that granting these permissions permits the user to see which users, groups, or roles are attached to a [managed policy](http://docs.aws.amazon.com/general/latest/gr/glos-chap.html#managed_policy)\. It also allows the user to see which services a user or role has access to and which services have been accessed, by whom and when\. This is similar to the `iam:ListEntitiesForPolicy` and `iam:ListAttached[User/Group/Role]Policies` permissions\.

**To view access advisor information**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose either **Groups**, or **Users**, or **Roles**, or **Policies**\.

1. Choose any user, group, role, or policy name to open its detailed view and choose the **Access Advisor** tab\. The tab displays a table with the following columns:  
**Service Name**  
A list of services with permissions granted by an IAM policy \(if you are examining a policy\), or the list of services with permissions granted to the IAM entity by all IAM policies \(if you are examining a user, group, or role\)\.   
A row for a service appears if the entity is granted *any* permission to that service by an IAM policy, whether that permission is for only one action in the service or all of them\.  
**Policies Granting Permissions**  
The name of one policy and a count of other policies that grant this entity permission to access the specified service\. Choose the link with the policy name and count to see a list of all of the IAM policies that grant this entity permission to access the specified service\. The list also includes the name, the type of policy \(AWS managed, customer managed, or inline\), and the group \(if applicable\) through which a user gets the policy\.  
If you choose the name of a managed policy in the **Policies Granting Permissions** dialog box, IAM opens a new browser tab that shows the policy text\. If you click a group name in the dialog box, IAM opens a new browser tab that displays the details for the group\.  
**Last Accessed**  
The length of time since this user, role, or a member of a group last accessed the specified service\. If the service has been updated, but it was 365 days ago or longer, this value is **365**\.  
**Access by Members**  
*\(Group only\)* The name of one user and a count of other users who are members of the group and that have accessed this service\. Choose the link to see a list of all of the IAM users who are members of the group and when each member last accessed the specified service\.   
If you choose the name of a user in the dialog box, IAM opens a new browser tab that displays the details for the user\.  
**Access by Entities**  
*\(Policy only\)* The name of one user or role and a count of other users and roles who have used this policy to access the specified service\. Choose the link to see a list of all of the users and roles to which this policy is attached and when each last accessed the specified service\.

**Additional options**
   + Use the **Filter** menu on the **Access Advisor** tab to limit the list to **Services accessed** and **Services not accessed**\. For example, you might select **Services not accessed** for a policy to discover which services listed in that policy are never used\. In that case, you might want to remove those services from the policy\. You can also type a name \(or part of a name\) in the search box to restrict the list to only those entities whose name matches what you type\.
   + Choose one of the column heads to sort the information according to that column's information\. Choose the header a second time to sort in the opposite order\.

## Notes<a name="access_policies_access-advisor-notes"></a>
+ The list of services in the table reflects the *current* state of your IAM policies, not any historical state\. For example, if the current version of your policy allows only Amazon S3 access and it previously allowed access to other AWS services, the service last accessed data shows only a table entry for Amazon S3\. If you are trying to determine the history of access control changes in your account, or want to audit historical access, we recommend that you use [AWS CloudTrail](https://aws.amazon.com/cloudtrail/)\.
+ It usually takes less than 4 hours for recent **Last Accessed** activity to appear in the table\. However, under some circumstances it can take up to 12 hours\. If the service is running unusually slow, a notification appears in the IAM console\.
+ Access advisor reports activity for the last 365 days\. If there has been no activity, then Access Advisor reports **Not accessed in the tracking period**\. If there has been activity, but it was 365 days ago or longer, then Access Advisor reports a last accessed period of **365**\.

## Troubleshooting Tips<a name="access_policies_access-advisor-troubleshooting"></a>

If the service last accessed table is empty, it might be caused by one of the following:
+ You selected a user that has no attached policies, either directly or through group memberships\.
+ You selected a managed policy attached to a group that has no members\.
+ You selected a user, group, or role that has neither inline nor managed policies attached\.
+ You selected a user that has permissions granted only by a resource\-based policy\.

## Sample Usage Scenarios<a name="access_policies_access-advisor-scenarios"></a>

Some examples that show the value of using the IAM access advisor for both policies \(the first example\) and principals \(the second\)\.

### Scoping Down Permissions for an IAM Policy<a name="access-advisor-sample-use-case1"></a>

Imagine an administrator who is responsible for managing a team’s AWS infrastructure\. The team has created an application that runs on Amazon EC2 and calls other AWS services\. This means that the administrator needs to provision an EC2 instance for this application and manage its configuration\. One part of this is to attach an IAM role to this EC2 instance\. 

**Note**  
You can attach IAM roles to EC2 instances to enable applications that run on those instances to make API requests\. That way you don't need to manually manage the security credentials that the applications use\. Instead of creating and distributing your AWS credentials, you can delegate permission to make API requests to an IAM role that is assigned to the instance\. For more information, see [IAM Roles for Amazon EC2](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)\. 

However, the administrator is new to IAM and when attaching the IAM role to the EC2 instance, the administrator is not sure what to put in the role’s permission policy\. The administrator *wants* to implement a thorough access control mechanism, but the immediate priority is to make sure that the application works\. To do that the administrator simply copies the **PowerUserAccess** AWS managed policy shown below with the intention of modifying it as it becomes clear over time what permissions are really needed\. This policy grants full read\-write permissions to all AWS services and resources in the account except for IAM \(and is definitely *not* recommended as a long\-term solution\)\.

```
{
  "Statement": [
    {
      "Effect": "Allow",
      "NotAction": "iam:*",
      "Resource": "*"
    }
  ]
}
```

After the application runs for a while, the administrator can use the service last accessed data to view which permissions are actually used\. The administrator can then reduce the permissions for the application\. The administrator signs in to the IAM console and chooses **Policies**, finds the policy attached to the IAM role associated with the EC2 instance where the application is running\. The administrator then chooses the policy name to view its details and chooses the **Access Advisor** tab\.

The administrator reviews the time stamps listed in the **Last Accessed** column and notices that the team's application is using only Amazon DynamoDB, Amazon S3, Amazon CloudWatch, Amazon Simple Notification Service \(Amazon SNS\), and Amazon Simple Queue Service \(Amazon SQS\)\. The administrator can then choose the **Permissions** tab and expand the row for a policy whose permissions need to be restricted\. The administrator chooses **Edit policy** for inline policies that are attached directly to the user\. To edit a managed policy, the administrator chooses the name of the policy to go to the **Policies** page\. From there, administrators can revise the policy's access to include only those permissions that are required for the application to successfully run\.

### Scoping Down Permissions for an IAM User<a name="access_policies_access-advisor-scope-permissions"></a>

Imagine an IT administrator who is responsible for ensuring that people in the organization do not have excess AWS permissions\. As part of a periodic security check, the administrator reviews the permissions of all IAM users\. One of these users is an application developer, who previously filled the role of a security engineer\. Because of the change in job requirements, the developer is a member of both the “app\-dev” group for the new job \(which grants permissions to multiple services including Amazon EC2, Amazon EBS, Auto Scaling, etc\.\) and the “security\-team” group for the old job \(which grants permissions to IAM and CloudTrail\)\.

The administrator signs into the IAM console and chooses **Users**, then chooses the name of the IAM user of the developer and then chooses the **Access Advisor** tab\.

The administrator reviews the time stamps in the **Last Accessed** column and notices that the developer has not recently accessed IAM, CloudTrail, Route 53, Amazon Elastic Transcoder, and a number of other AWS services\. The administrator is now ready to act on the service last accessed information\. However, unlike the previous example, the next steps for a principal like the developer's IAM user \(who may be subject to multiple policies and a member of multiple IAM groups\) requires the administrator to proceed with caution to avoid inadvertently disrupting other users’ access\. So his first step is to determine *how* the developer is receiving these permissions\.

The administrator confirms that the developer has no business need for access to IAM and CloudTrail anymore because the developer is no longer a member of the internal security team\. For these permissions, after analyzing the group memberships and policies, the administrator realizes that the simplest solution is to remove the developer’s membership in the security\-team IAM group, rather than make any policy changes\.

The administrator might also infer that the developer’s access to Route 53, Elastic Transcoder, etc\. from the app\-dev group should also be revoked due to lack of use\. However, before cutting these permissions out of the app\-dev policy \(which may adversely affect other members of the group\), the administrator should consult the service last accessed data for the app\-dev group policies\. That data can reveal whether these permissions are universally unused by all app\-dev group members or simply unused by this particular developer\. If they are truly unused by all group members, then the administrator can probably safely remove those permissions from the app\-dev group's policy\. If it is only this one developer that is not using the permissions, then the administrator may want to craft a different set of permissions for the developer\. Another option is for the administrator to do nothing, accepting that not all users exercise all the permissions granted to them\.

As this example shows, you might use the service last accessed data for principals as a starting point for a number of possible next steps, including the following suggestions\. However, it’s up to you as an IAM administrator to choose the steps that strike the right balance of accessibility and least\-privilege that’s appropriate to your organization\.
+ [Removing membership in a group](id_groups_manage_add-remove-users.md)
+ [Detaching a managed policy](access_policies_manage-attach-detach.md#detach-managed-policy-console)
+ [Deleting a managed policy](access_policies_manage-delete.md#delete-managed-policy)
+ [Deleting an inline policy and converting to a managed policy](access_policies_manage-delete.md)
+ [Editing an existing policy to remove permissions](access_policies_manage-edit.md)
+ [Adding an explicit deny to an existing policy](reference_policies_evaluation-logic.md#AccessPolicyLanguage_Interplay)

## Regions Where Data Is Tracked<a name="access-advisor_tracking-period"></a>

AWS collects service last accessed data in most regions\. Data is stored for a maximum of 365 days\. When AWS adds additional regions, those regions are added to the following table, including the date that AWS started tracking data in each region:


****  

| Region name | Region | Tracking start date | 
| --- | --- | --- | 
| US East \(N\. Virginia\) | us\-east\-1 | October 1, 2015 | 
| US East \(Ohio\) | us\-east\-2 | October 27, 2017 | 
| US West \(N\. California\) | us\-west\-1 | October 1, 2015 | 
| US West \(Oregon\) | us\-west\-2 | October 1, 2015 | 
| Asia Pacific \(Tokyo\) | ap\-northeast\-1 | October 1, 2015 | 
| Asia Pacific \(Seoul\) | ap\-northeast\-2 | January 6, 2016 | 
| Asia Pacific \(Singapore\) | ap\-southeast\-1 | October 1, 2015 | 
| Asia Pacific \(Sydney\) | ap\-southeast\-2 | October 1, 2015 | 
| Asia Pacific \(Mumbai\) | ap\-south\-1 | June 27, 2016 | 
| Canada \(Central\) | ca\-central\-1 | October 28, 2017 | 
| EU \(Frankfurt\) | eu\-central\-1 | October 1, 2015 | 
| EU \(Ireland\) | eu\-west\-1 | October 1, 2015 | 
| EU \(London\) | eu\-west\-2 | October 28, 2017 | 
| EU \(Paris\) | eu\-west\-3 | December 18, 2017 | 
| South America \(São Paulo\) | sa\-east\-1 | December 11, 2015 | 

If a region is not listed in the previous table, then that region does not yet provide service last accessed data\.