# Refining Permissions Using Service Last Accessed Data<a name="access_policies_access-advisor"></a>

You can view service last accessed data for entities or policies in IAM or AWS Organizations\. This data is available for an IAM policy or entity \(user or role\) in your account\. The data for IAM includes information about the allowed services that IAM entities last attempted to access and when\. To learn more about the report and how to view service last accessed data for IAM, see [Viewing Service Last Accessed Data for IAM](access_policies_access-advisor-view-data.md)\.

If you sign in using master account credentials, you can also view service last accessed data for an AWS Organizations entity or policy in your organization\. AWS Organizations entities include the organization root, organizational units \(OUs\), or accounts\. The Organizations service last accessed data includes information about the allowed services that principals in an Organizations account last attempted to access and when\. To learn more about the report and how to view service last accessed data for AWS Organizations, see [Viewing Service Last Accessed Data for Organizations](access_policies_access-advisor-view-data-orgs.md)\.

You can then use the service last accessed data to refine your policies and allow access to only the services that your entities use\. This helps you to better adhere to the best practice of [least privilege](best-practices.md#grant-least-privilege)\.

For example scenarios for using service last accessed data to make decisions about the permissions that you grant to your IAM entities or Organizations entities, see [Example Scenarios for Using Service Last Accessed Data](access_policies_access-advisor-example-scenarios.md)\.

**Topics**
+ [Things to Know](#access_policies_access-advisor-know)
+ [Permissions Required](#access_policies_access-advisor-permissions)
+ [Troubleshooting Activity for IAM and Organizations Entities](#access_policies_access-advisor-troubleshooting)
+ [Regions Where Data Is Tracked](#access-advisor_tracking-period)
+ [Viewing Service Last Accessed Data for IAM](access_policies_access-advisor-view-data.md)
+ [Viewing Service Last Accessed Data for Organizations](access_policies_access-advisor-view-data-orgs.md)
+ [Example Scenarios for Using Service Last Accessed Data](access_policies_access-advisor-example-scenarios.md)

## Things to Know<a name="access_policies_access-advisor-know"></a>

Before you use service last accessed data from a report to change the permissions for an IAM entity or Organizations entity, review the following details about the data\.
+ **Reporting period** – Recent activity usually appears in the IAM console within four hours\. IAM reports activity for the last 365 days, or less if your Region began supporting this feature within the last year\. For more information, see [Regions Where Data Is Tracked](#access-advisor_tracking-period)\. 
+ **Report owner** – Only the principal that generates a report can view the report details\. This means that when you view the data in the AWS Management Console, you might have to wait for it to generate and load\. If you use the AWS CLI or AWS API to get report details, your credentials must match the credentials of the principal that generated the report\. If you use temporary credentials for a role or federated user, you must generate and retrieve the report during the same session\. For more information about assumed\-role session principals, see [AWS JSON Policy Elements: Principal](reference_policies_elements_principal.md)\.
+ **PassRole** – The`iam:PassRole` action is not tracked\.
+ **Authenticated IAM entities** – The data for IAM includes only authenticated IAM entities \(users or roles\) in your account\. Data for Organizations includes only authenticated principals \(IAM users, IAM roles, or the AWS account root user\) in the specified Organizations entity\. The data does not include unauthenticated attempts\.
+ **IAM policy types** – The data for IAM includes services that are allowed by an IAM entity's policies\. These are policies attached to a role or attached to a user directly or through a group\. Access allowed by other policy types is not included in your report\. The excluded policy types include resource\-based policies, access control lists, AWS Organizations SCPs, IAM permissions boundaries, and session policies\. To learn how the different policy types are evaluated to allow or deny access, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.
+ **Organizations policy types** – The data for AWS Organizations includes only services that are allowed by an Organizations entity's inherited service control policies \(SCPs\)\. SCPs are policies attached to a root, OU, or account\. Access allowed by other policy types is not included in your report\. The excluded policy types include identity\-based policies, resource\-based policies, access control lists, IAM permissions boundaries, and session policies\. To learn how the different policy types are evaluated to allow or deny access, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.
+ **Specifying a policy ID** – When you use the AWS CLI or AWS API to generate a report for service last accessed data in Organizations, you can optionally specify a policy ID\. The resulting report includes data for the services that are allowed by only that policy\. The data includes the most recent account activity in the specified Organizations entity or the entity's children\. For more information, see [aws iam generate\-organizations\-access\-report](https://docs.aws.amazon.com/cli/latest/reference/iam/generate-organizations-access-report.html) or [GenerateOrganizationsAccessReport](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GenerateOrganizationsAccessReport.html)\.
+ **Organizations master account** – You must sign in using your organization's master account credentials to view service last accessed data\. You can choose to view data for the master account using the IAM console, the AWS CLI, or the AWS API\. The resulting report lists all AWS services, because the master account is not limited by SCPs\. If you specify a policy ID in the CLI or API, the policy is ignored\. For each service, the report includes data for only the master account\. However, reports for other Organizations entities do not return data for activity in the master account\.
+ **Organizations settings** – An administrator must [enable SCPs in your organization root](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies.html#enable_policies_on_root) before you can generate data for Organizations\.

## Permissions Required<a name="access_policies_access-advisor-permissions"></a>

To view the service last accessed data in the AWS Management Console, you must have a policy that grants the necessary permissions\.

### Permissions for IAM Data<a name="access_policies_access-advisor-permissions-iam"></a>

To use the IAM console to view the service last accessed data for an IAM user, role, or policy, you must have a policy that includes the following actions:
+ `iam:GenerateServiceLastAccessedDetails`
+ `iam:Get*`
+ `iam:List*`

These permissions allow a user to see the following:
+ Which users, groups, or roles are attached to a [managed policy](https://docs.aws.amazon.com/general/latest/gr/glos-chap.html#managed_policy)
+ Which services a user or role can access
+ The last time they accessed the service

To use the AWS CLI or AWS API to view service last accessed data for IAM, you must have permissions that match the operation you want to use:
+ `iam:GenerateServiceLastAccessedDetails`
+ `iam:GetServiceLastAccessedDetails`
+ `iam:GetServiceLastAccessedDetailsWithEntities`
+ `iam:ListPoliciesGrantingServiceAccess`

This example shows how you might create a policy that allows viewing IAM service last accessed data\. Additionally, it allows read\-only access to all of IAM\. This policy also grants the necessary permissions to complete this action on the console\. 

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "iam:GenerateServiceLastAccessedDetails",
            "iam:Get*",
            "iam:List*"
        ],
        "Resource": "*"
    }
```

### Permissions for AWS Organizations Data<a name="access_policies_access-advisor-permissions-orgs"></a>

To use the IAM console to view a report for the root, OU, or account entities in Organizations, you must have a policy that includes the following actions:
+ `iam:GenerateOrganizationsAccessReport`
+ `iam:GetOrganizationsAccessReport`
+ `organizations:DescribeAccount`
+ `organizations:DescribeOrganization`
+ `organizations:DescribeOrganizationalUnit`
+ `organizations:DescribePolicy`
+ `organizations:ListChildren`
+ `organizations:ListParents`
+ `organizations:ListPoliciesForTarget`
+ `organizations:ListRoots`
+ `organizations:ListTargetsForPolicy`

To use the AWS CLI or AWS API to view service last accessed data for Organizations, you must have a policy that includes the following actions:
+ `iam:GenerateOrganizationsAccessReport`
+ `iam:GetOrganizationsAccessReport`
+ `organizations:DescribePolicy`
+ `organizations:ListChildren`
+ `organizations:ListParents`
+ `organizations:ListPoliciesForTarget`
+ `organizations:ListRoots`
+ `organizations:ListTargetsForPolicy`

This example shows how you might create a policy that allows viewing service last accessed data for Organizations\. Additionally, it allows read\-only access to all of Organizations\. This policy also grants the necessary permissions to complete this action on the console\. 

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "iam:GenerateOrganizationsAccessReport",
            "iam:GetOrganizationsAccessReport",
            "organizations:Describe*",
            "organizations:List*"
        ],
        "Resource": "*"
    }
}
```

You can also use the [iam:OrganizationsPolicyId](reference_policies_iam-condition-keys.md#ck_OrganizationsPolicyId) condition key to allow generating a report only for a specific Organizations policy\. For an example policy, see [IAM: View Service Last Accessed Data for an Organizations Policy](reference_policies_examples_iam_service-accessed-data-orgs.md)\.

## Troubleshooting Activity for IAM and Organizations Entities<a name="access_policies_access-advisor-troubleshooting"></a>

In some cases, your AWS Management Console service last accessed data table might be empty\. Or perhaps your AWS CLI or AWS API request returns an empty set of data or a null field\. In these cases, review the following issues:
+ For an IAM user, make sure that the user has at least one inline or managed policy attached, either directly or through group memberships\.
+ For an IAM group, verify that the group has at least one inline or managed policy attached\.
+ For an IAM group, the report returns only the service last access data for members that used the group's policies to access a service\. To learn whether a member used other policies, review the service last accessed data for that user\.
+ For an IAM role, verify that the role has at least one inline or managed policy attached\.
+ For an IAM entity \(user or role\), review other policy types that might affect the permissions of that entity\. These include resource\-based policies, access control lists, AWS Organizations policies, IAM permissions boundaries, or session policies\. For more information, see [Policy Types](access_policies.md#access_policy-types) or [Evaluating Policies Within a Single Account](reference_policies_evaluation-logic.md#policy-eval-basics)\.
+ For an IAM policy, make sure that the specified managed policy is attached to at least one user, group with members, or role\.
+ For an Organizations entity \(root, OU, or account\), make sure that you are signed using Organizations master account credentials\.
+ Verify that [SCPs are enabled in your organization root](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies.html#enable_policies_on_root)\.

When you make changes, wait at least four hours for activity to appear in your IAM console report\. If you use the AWS CLI or AWS API, you must generate a new report to view the updated data\.

## Regions Where Data Is Tracked<a name="access-advisor_tracking-period"></a>

AWS collects service last accessed data in most Regions\. Data is stored for a maximum of 365 days\. When AWS adds additional Regions, those Regions are added to the following table, including the date that AWS started tracking data in each Region:


****  

| Region Name | Region | Tracking Start Date | 
| --- | --- | --- | 
| US East \(Ohio\) | us\-east\-2 | October 27, 2017 | 
| US East \(N\. Virginia\) | us\-east\-1 | October 1, 2015 | 
| US West \(N\. California\) | us\-west\-1 | October 1, 2015 | 
| US West \(Oregon\) | us\-west\-2 | October 1, 2015 | 
| Asia Pacific \(Tokyo\) | ap\-northeast\-1 | October 1, 2015 | 
| Asia Pacific \(Seoul\) | ap\-northeast\-2 | January 6, 2016 | 
| Asia Pacific \(Singapore\) | ap\-southeast\-1 | October 1, 2015 | 
| Asia Pacific \(Sydney\) | ap\-southeast\-2 | October 1, 2015 | 
| Asia Pacific \(Mumbai\) | ap\-south\-1 | June 27, 2016 | 
| Asia Pacific \(Hong Kong\) | ap\-east\-1 | April 24, 2019 | 
| Middle East \(Bahrain\) | me\-south\-1 | July 29, 2019 | 
| Canada \(Central\) | ca\-central\-1 | October 28, 2017 | 
| Europe \(Frankfurt\) | eu\-central\-1 | October 1, 2015 | 
| Europe \(Stockholm\) | eu\-north\-1 | December 12, 2018 | 
| Europe \(Ireland\) | eu\-west\-1 | October 1, 2015 | 
| Europe \(London\) | eu\-west\-2 | October 28, 2017 | 
| Europe \(Paris\) | eu\-west\-3 | December 18, 2017 | 
| South America \(São Paulo\) | sa\-east\-1 | December 11, 2015 | 

If a Region is not listed in the previous table, then that Region does not yet provide service last accessed data\.