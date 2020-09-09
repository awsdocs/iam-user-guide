# Viewing last accessed information for IAM<a name="access_policies_access-advisor-view-data"></a>

You can view last accessed information for IAM using the AWS Management Console, AWS CLI, or AWS API\. Last accessed information includes information about some actions that were last accessed for Amazon S3\. For more information about last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\. 

You can view information for each type of resource in IAM\. In each case, the information includes allowed services for the given reporting period:
+ **User** – View the last time that the user tried to access each allowed service\.
+ **Group** – View information about the last time that a group member attempted to access each allowed service\. This report also includes the total number of members that attempted access\.
+ **Role** – View the last time that someone used the role in an attempt to access each allowed service\.
+ **Policy** – View information about the last time that a user or role attempted to access each allowed service\. This report also includes the total number of entities that attempted access\.

**Note**  
Before you view the access information for a resource in IAM, make sure you understand the reporting period, reported entities, and the evaluated policy types for your information\. For more details, see [Things to know about last accessed information](access_policies_access-advisor.md#access_policies_access-advisor-know)\.

## Viewing information for IAM \(console\)<a name="access_policies_access-advisor-viewing"></a>

You can view last accessed information for IAM on the **Access Advisor** tab in the IAM console\.

**To view information for IAM \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose either **Groups**, **Users**, **Roles**, or **Policies**\.

1. Choose any user, group, role, or policy name to open its **Summary** page and choose the **Access Advisor** tab\. View the following information, based on the resource that you chose:
   + **Group** – View the list of services that group members \(users\) can access\. You can also view when a member last accessed the service, what group policies they used, and which group member made the request\. Choose the name of the policy to learn whether it is a managed policy or an inline group policy\. Choose the name of the group member to see all of the members of the group and when they last accessed the service\.
   + **User** – View the list of services that the user can access\. You can also view when they last accessed the service, and what policies they used\. Choose the name of the policy to learn whether it is a managed policy, an inline user policy, or an inline policy for the group\.
   + **Role** – View the list of services that the role can access, when the role last accessed the service, and what policies were used\. Choose the name of the policy to learn whether it is a managed policy or an inline role policy\.
   + **Policy** – View the list of services with allowed actions in the policy\. You can also view when the policy was last used to access the service, and which entity \(user or role\) used the policy\. Choose the name of the entity to learn which entities have this policy attached and when they last accessed the service\.

1. \(Optional\) In the **Service** column of the table, choose **Amazon S3** to view a list of Amazon S3 management actions that IAM entities have attempted to access\. You can view the AWS Region and a timestamp that shows when someone last attempted to perform the action\.

1. The **Last accessed** column is displayed for services and Amazon S3 management actions\. Review the following possible results that are returned in this column\. These results vary depending on whether a service or action is allowed, was accessed, and whether it is tracked by AWS for last accessed information\.   
**<number of> days ago**  
The number of days since the service or action was used in the tracking period\. The tracking period for services is for the last 400 days\. The tracking period for actions started on April 12, 2020\. To learn more about the tracking start dates for each AWS Region, see [Where AWS tracks last accessed information](access_policies_access-advisor.md#access-advisor_tracking-period)\.  
**Not accessed in the tracking period**  
The tracked service or action has not been used by an entity in the tracking period\.

   It is possible for you to have permissions for an action that doesn't appear in the list\. This can happen if the tracking information for the action is not currently supported by AWS\. You should not make permissions decisions based solely on the absence of tracking information\. Instead, we recommend that you use this information to inform and support your overall strategy of granting least privilege\. Check your policies to confirm that the level of access is appropriate\.

## Viewing information for IAM \(AWS CLI\)<a name="access_policies_access-advisor-viewing-cli"></a>

You can use the AWS CLI to retrieve information about the last time that an IAM resource was used to attempt to access AWS services and Amazon S3 actions\. An IAM resource can be a user, group, role, or policy\.

**To view information for IAM \(AWS CLI\)**

1. Generate a report\. The request must include the ARN of the IAM resource \(user, group, role, or policy\) for which you want a report\. You can specify the level of granularity that you want to generate in the report to view access details for either services or both services and actions\. The request returns a `job-id` that you can then use in the `get-service-last-accessed-details` and `get-service-last-accessed-details-with-entities` operations to monitor the `job-status` until the job is complete\.
   + [aws iam generate\-service\-last\-accessed\-details](https://docs.aws.amazon.com/cli/latest/reference/iam/generate-service-last-accessed-details.html)

1. Retrieve details about the report using the `job-id` parameter from the previous step\.
   + [aws iam get\-service\-last\-accessed\-details](https://docs.aws.amazon.com/cli/latest/reference/iam/get-service-last-accessed-details.html)

   This operation returns the following information, based on the type of resource and level of granularity that you requested in the `generate-service-last-accessed-details` operation:
   + **User** – Returns a list of services that the specified user can access\. For each service, the operation returns the date and time of the user's last attempt and the ARN of the user\.
   + **Group** – Returns a list of services that members of the specified group can access using the policies attached to the group\. For each service, the operation returns the date and time of the last attempt made by any group member \(user\)\. It also returns the ARN of that user and the total number of group members that have attempted to access the service\. Use the [GetServiceLastAccessedDetailsWithEntities](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLastAccessedDetailsWithEntities.html) operation to retrieve a list of all of the members\.
   + **Role** – Returns a list of services that the specified role can access\. For each service, the operation returns the date and time of the role's last attempt and the ARN of the role\.
   + **Policy** – Returns a list of services for which the specified policy allows access\. For each service, the operation returns the date and time that an entity \(user or role\) last attempted to access the service using the policy\. It also returns the ARN of that entity and the total number of entities that attempted access\.

1. Learn more about the entities that used group or policy permissions in an attempt to access a specific service\. This operation returns a list of entities with each entity's ARN, ID, name, path, type \(user or role\), and when they last attempted to access the service\. You can also use this operation for users and roles, but it only returns information about that entity\.
   + [aws iam get\-service\-last\-accessed\-details\-with\-entities](https://docs.aws.amazon.com/cli/latest/reference/iam/get-service-last-accessed-details-with-entities.html)

1. Learn more about the identity\-based policies that an identity \(user, group, or role\) used in an attempt to access a specific service\. When you specify an identity and service, this operation returns a list of permissions policies that the identity can use to access the specified service\. This operation gives the current state of policies and does not depend on the generated report\. It also does not return other policy types, such as resource\-based policies, access control lists, AWS Organizations policies, IAM permissions boundaries, or session policies\. For more information, see [Policy types](access_policies.md#access_policy-types) or [Evaluating policies within a single account](reference_policies_evaluation-logic.md#policy-eval-basics)\.
   + [aws iam list\-policies\-granting\-service\-access](https://docs.aws.amazon.com/cli/latest/reference/iam/list-policies-granting-service-access.html)

## Viewing information for IAM \(AWS API\)<a name="access_policies_access-advisor-viewing-api"></a>

You can use the AWS API to retrieve information about the last time that an IAM resource was used to attempt to access AWS services and Amazon S3 actions\. An IAM resource can be a user, group, role, or policy\. You can specify the level of granularity to generate in the report to view details for either services or both services and actions\. 

**To view information for IAM \(AWS API\)**

1. Generate a report\. The request must include the ARN of the IAM resource \(user, group, role, or policy\) for which you want a report\. It returns a `JobId` that you can then use in the `GetServiceLastAccessedDetails` and `GetServiceLastAccessedDetailsWithEntities` operations to monitor the `JobStatus` until the job is complete\.
   + [GenerateServiceLastAccessedDetails](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GenerateServiceLastAccessedDetails.html)

1. Retrieve details about the report using the `JobId` parameter from the previous step\.
   + [GetServiceLastAccessedDetails](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLastAccessedDetails.html)

   This operation returns the following information, based on the type of resource and level of granularity that you requested in the `GenerateServiceLastAccessedDetails` operation:
   + **User** – Returns a list of services that the specified user can access\. For each service, the operation returns the date and time of the user's last attempt and the ARN of the user\.
   + **Group** – Returns a list of services that members of the specified group can access using the policies attached to the group\. For each service, the operation returns the date and time of the last attempt made by any group member \(user\)\. It also returns the ARN of that user and the total number of group members that have attempted to access the service\. Use the [GetServiceLastAccessedDetailsWithEntities](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLastAccessedDetailsWithEntities.html) operation to retrieve a list of all of the members\.
   + **Role** – Returns a list of services that the specified role can access\. For each service, the operation returns the date and time of the role's last attempt and the ARN of the role\.
   + **Policy** – Returns a list of services for which the specified policy allows access\. For each service, the operation returns the date and time that an entity \(user or role\) last attempted to access the service using the policy\. It also returns the ARN of that entity and the total number of entities that attempted access\.

1. Learn more about the entities that used group or policy permissions in an attempt to access a specific service\. This operation returns a list of entities with each entity's ARN, ID, name, path, type \(user or role\), and when they last attempted to access the service\. You can also use this operation for users and roles, but it only returns information about that entity\.
   + [GetServiceLastAccessedDetailsWithEntities](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLastAccessedDetailsWithEntities.html)

1. Learn more about the identity\-based policies that an identity \(user, group, or role\) used in an attempt to access a specific service\. When you specify an identity and service, this operation returns a list of permissions policies that the identity can use to access the specified service\. This operation gives the current state of policies and does not depend on the generated report\. It also does not return other policy types, such as resource\-based policies, access control lists, AWS Organizations policies, IAM permissions boundaries, or session policies\. For more information, see [Policy types](access_policies.md#access_policy-types) or [Evaluating policies within a single account](reference_policies_evaluation-logic.md#policy-eval-basics)\.
   + [ListPoliciesGrantingServiceAccess](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPoliciesGrantingServiceAccess.html)