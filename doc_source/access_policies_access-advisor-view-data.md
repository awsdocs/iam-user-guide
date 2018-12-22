# Viewing Service Last Accessed Data<a name="access_policies_access-advisor-view-data"></a>

You can view service last accessed data using the AWS Management Console, AWS CLI, or AWS API\. For more information about service last accessed data, see [Reducing Permissions Using Service Last Accessed Data](access_policies_access-advisor.md)\.

**Note**  
Before you view the access data for a resource in IAM, make sure you understand the reporting period, reported entities, and the evaluated policy types for your data\. For more details, see [Things to Know](access_policies_access-advisor.md#access_policies_access-advisor-know)\.

## Viewing Entity Activity \(Console\)<a name="access_policies_access-advisor-viewing"></a>

In the IAM console, you can view service last accessed data on the **Access Advisor** tab for users, groups, roles, or policies\.

**To view service last accessed data \(console\)**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose either **Groups**, **Users**, **Roles**, or **Policies**\.

1. Choose any user, group, role, or policy name to open its **Summary** page and choose the **Access Advisor** tab\. View the following information, based on the resource that you chose:
   + **Group** – View the list of services that group members \(users\) can access, when a member last accessed the service, what group policies they used, and which group member made the request\. Choose the name of the policy to learn whether it is a managed policy or an inline group policy\. Choose the name of the group member to see all of the members of the group and when they last accessed the service\.
   + **User** – View the list of services that the user can access, when they last accessed the service, and what policies they used\. Choose the name of the policy to learn whether the policy is managed, an inline user policy, or an inline policy for the group to which the user belongs\.
   + **Role** – View the list of services that the role can access, when the role last accessed the service, and what policies were used\. Choose the name of the policy to learn whether it is a managed policy or an inline role policy\.
   + **Policy** – View the list of services with allowed actions in the policy, when the policy was last used to access the service, and which entity \(user or role\) used the policy\. Choose the name of the entity to learn which entities have this policy attached and when they last accessed the service\.

## Viewing Entity Activity \(AWS CLI\)<a name="access_policies_access-advisor-viewing-cli"></a>

You can use the AWS CLI to retrieve data about the last time that an IAM resource \(user, group, role, or policy\) was used to attempt to access AWS services\.

**To view service last accessed data \(AWS CLI\)**

1. Generate a report\. The request must include the ARN of the IAM resource \(user, group, role, or policy\) for which you want a report\. It returns a `job-id` that you can then use in the `get-service-last-accessed-details` and `get-service-last-accessed-details-with-entities` operations to monitor the `job-status` until the job is complete\.
   + [aws iam generate\-service\-last\-accessed\-details](https://docs.aws.amazon.com/cli/latest/reference/iam/generate-service-last-accessed-details.html)

1. Retrieve details about the report using the `job-id` parameter from the previous step\.
   + [aws iam get\-service\-last\-accessed\-details](https://docs.aws.amazon.com/cli/latest/reference/iam/get-service-last-accessed-details.html)

   This operation returns the following information, based on the type of resource that you requested in the `generate-service-last-accessed-details` operation:
   + **User** – Returns a list of services that the specified user can access\. For each service, the operation returns the date and time of the user's last attempt and the ARN of the user\.
   + **Group** – Returns a list of services that members of the specified group can access using the policies attached to the group\. For each service, the operation returns the date and time of the last attempt made by any group member \(user\)\. It also returns the ARN of that user and the total number of group members that have attempted to access the service\. Use the [GetServiceLastAccessedDetailsWithEntities](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLastAccessedDetailsWithEntities.html) operation to retrieve a list of all of the members\.
   + **Role** – Returns a list of services that the specified role can access\. For each service, the operation returns the date and time of the role's last attempt and the ARN of the role\.
   + **Policy** – Returns a list of services for which the specified policy allows access\. For each service, the operation returns the date and time that an entity \(user or role\) last attempted to access the service using the policy\. It also returns the ARN of that entity and the total number of entities that attempted access\.

1. Learn more about the entities that used group or policy permissions in an attempt to access a specific service\. This operation returns a list of entities with each entity's ARN, ID, name, path, type \(user or role\), and when they last attempted to access the service\. You can also use this operation for users and roles, but it only returns information about that entity\.
   + [aws iam get\-service\-last\-accessed\-details\-with\-entities](https://docs.aws.amazon.com/cli/latest/reference/iam/get-service-last-accessed-details-with-entities.html)

1. Learn more about the permissions policies that an identity \(user, group, or role\) used in an attempt to access a specific service\. When you specify an identity and service, this operation returns a list of permissions policies that the identity can use to access the specified service\. This operation gives the current state of policies and does not depend on the generated report\. It also does not return other policy types, such as resource\-based policies, access control lists, AWS Organizations policies, IAM permissions boundaries, or AWS STS assume role policies\. For more information, see [Policy Types](access_policies.md#access_policy-types) or [Evaluating Policies Within a Single Account](reference_policies_evaluation-logic.md#policy-eval-basics)\.
   + [aws iam list\-policies\-granting\-service\-access](https://docs.aws.amazon.com/cli/latest/reference/iam/list-policies-granting-service-access.html)

## Viewing Entity Activity \(AWS API\)<a name="access_policies_access-advisor-viewing-api"></a>

You can use the AWS API to retrieve data about the last time that an IAM resource \(user, group, role, or policy\) was used to attempt to access AWS services\.

**To view service last accessed data \(AWS API\)**

1. Generate a report\. The request must include the ARN of the IAM resource \(user, group, role, or policy\) for which you want a report\. It returns a `JobId` that you can then use in the `GetServiceLastAccessedDetails` and `GetServiceLastAccessedDetailsWithEntities` operations to monitor the `JobStatus` until the job is complete\.
   + [GenerateServiceLastAccessedDetails](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GenerateServiceLastAccessedDetails.html)

1. Retrieve details about the report using the `JobId` parameter from the previous step\.
   + [GetServiceLastAccessedDetails](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLastAccessedDetails.html)

   This operation returns the following information, based on the type of resource that you requested in the `GenerateServiceLastAccessedDetails` operation:
   + **User** – Returns a list of services that the specified user can access\. For each service, the operation returns the date and time of the user's last attempt and the ARN of the user\.
   + **Group** – Returns a list of services that members of the specified group can access using the policies attached to the group\. For each service, the operation returns the date and time of the last attempt made by any group member \(user\)\. It also returns the ARN of that user and the total number of group members that have attempted to access the service\. Use the [GetServiceLastAccessedDetailsWithEntities](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLastAccessedDetailsWithEntities.html) operation to retrieve a list of all of the members\.
   + **Role** – Returns a list of services that the specified role can access\. For each service, the operation returns the date and time of the role's last attempt and the ARN of the role\.
   + **Policy** – Returns a list of services for which the specified policy allows access\. For each service, the operation returns the date and time that an entity \(user or role\) last attempted to access the service using the policy\. It also returns the ARN of that entity and the total number of entities that attempted access\.

1. Learn more about the entities that used group or policy permissions in an attempt to access a specific service\. This operation returns a list of entities with each entity's ARN, ID, name, path, type \(user or role\), and when they last attempted to access the service\. You can also use this operation for users and roles, but it only returns information about that entity\.
   + [GetServiceLastAccessedDetailsWithEntities](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetServiceLastAccessedDetailsWithEntities.html)

1. Learn more about the permissions policies that an identity \(user, group, or role\) used in an attempt to access a specific service\. When you specify an identity and service, this operation returns a list of permissions policies that the identity can use to access the specified service\. This operation gives the current state of policies and does not depend on the generated report\. It also does not return other policy types, such as resource\-based policies, access control lists, AWS Organizations policies, IAM permissions boundaries, or AWS STS assume role policies\. For more information, see [Policy Types](access_policies.md#access_policy-types) or [Evaluating Policies Within a Single Account](reference_policies_evaluation-logic.md#policy-eval-basics)\.
   + [ListPoliciesGrantingServiceAccess](https://docs.aws.amazon.com/IAM/latest/APIReference/API_ListPoliciesGrantingServiceAccess.html)