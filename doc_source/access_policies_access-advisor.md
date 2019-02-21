# Reducing Permissions Using Service Last Accessed Data<a name="access_policies_access-advisor"></a>

You can view a report about the last time that an IAM entity \(user or role\) attempted to access a service\. This is known as service last accessed data\. You can then use this information to refine your policies to allow access to only the services that the entities use\. You can generate a report for each type of resource in IAM\. In each case, the report covers allowed services for the given reporting period:
+ **User** – View the last time that the user tried to access the service\.
+ **Group** – View information about the last time that a group member attempted to access the service\. This report also includes the total number of members that attempted access\.
+ **Role** – View the last time that someone used the role in an attempt to access the service\.
+ **Policy** – View information about the last time that a user or role attempted to access the service\. This report also includes the total number of entities that attempted access\.

You can use service last accessed data to identify unused and not recently used permissions in associated policies\. You can then choose to remove permissions for unused services or reorganize users with similar usage patterns into a group\. This helps improve account security\. Knowing if and when an entity last exercised a permission can help you remove unnecessary permissions and tighten your IAM policies with less effort\.

To learn how to view service last accessed data using the AWS Management Console, AWS CLI, or AWS API, see [Viewing Service Last Accessed Data](access_policies_access-advisor-view-data.md)\. 

For example scenarios for using service last accessed data to make decisions about the permissions that you grant to your IAM entities, see [Example Scenarios for Using Access Data](access_policies_access-advisor-example-scenarios.md)\.

## Things to Know<a name="access_policies_access-advisor-know"></a>

Before you use service last accessed data from a report to change the permissions for an entity, review the following details about the data\.
+ **Reporting period** – Recent activity usually appears within 4 hours\. IAM reports activity for the last 365 days, or less if your region began supporting this feature within the last year\. For more information, see [Regions Where Data Is Tracked](#access-advisor_tracking-period)\.
+ **Authenticated entities** – Your report includes data only for authenticated entities \(users or roles\) in your account\. The report does not include data about unauthenticated attempts\. It also does not include data for attempts made from other accounts 
+ **Policy types** – Your report includes data for only services that are allowed by an entity's policy\. These are policies attached to a role or attached to a user directly or through a group\. Access allowed by other policy types is not included in your report\. The excluded policy types include resource\-based policies, access control lists, AWS Organizations policies, IAM permissions boundaries, and session policies\. To learn how the different policy types are evaluated to allow or deny access, see [Policy Evaluation Logic](reference_policies_evaluation-logic.md)\.

**Topics**
+ [Things to Know](#access_policies_access-advisor-know)
+ [Permissions Required](#access_policies_access-advisor-permissions)
+ [Troubleshooting Entity Activity](#access_policies_access-advisor-troubleshooting)
+ [Regions Where Data Is Tracked](#access-advisor_tracking-period)
+ [Viewing Service Last Accessed Data](access_policies_access-advisor-view-data.md)
+ [Example Scenarios for Using Access Data](access_policies_access-advisor-example-scenarios.md)

## Permissions Required<a name="access_policies_access-advisor-permissions"></a>

 To view the service last accessed data using the AWS Management Console, you must have a policy that includes the following actions:
+ `iam:GenerateServiceLastAccessedDetails`
+ `iam:Get*`
+ `iam:List*`

**Note**  
These permissions allow a user to see the following:  
Which users, groups, or roles are attached to a [managed policy](https://docs.aws.amazon.com/general/latest/gr/glos-chap.html#managed_policy)
Which services a user or role can access
The last time they accessed the service

To view the service last accessed data using the AWS CLI or AWSAPI, you must also have permissions that match the operation you want to use:
+ `iam:GenerateServiceLastAccessedDetails`
+ `iam:GetServiceLastAccessedDetails`
+ `iam:GetServiceLastAccessedDetailsWithEntities`
+ `iam:ListPoliciesGrantingServiceAccess`

This example shows how you might create a policy that allows viewing service last accessed data, and read\-only access to all of IAM\. This policy also grants the permissions necessary to complete this action on the console\. 

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

## Troubleshooting Entity Activity<a name="access_policies_access-advisor-troubleshooting"></a>

If the AWS Management Console service last accessed data table is empty, or your AWS CLI or AWS API request returns an empty set of data or a null field, review the following examples:
+ For a user, make sure that the user has at least one inline or managed policy attached, either directly or through group memberships\.
+ For a group, verify that the group has at least one inline or managed policy attached\.
+ For a group, the report returns only the service last access data for members that used the group's policies to access a service\. To learn whether a member used other policies, review the service last accessed data for that user\.
+ For a role, verify that the role has at least one inline or managed policy attached\.
+ For an entity \(user or role\), review other policy types that might affect the permissions of that entity\. These include resource\-based policies, access control lists, AWS Organizations policies, IAM permissions boundaries, or session policies\. For more information, see [Policy Types](access_policies.md#access_policy-types) or [Evaluating Policies Within a Single Account](reference_policies_evaluation-logic.md#policy-eval-basics)\.
+ For a policy, make sure that the specified managed policy is attached to at least one user, group with members, or role\.

When you make changes, wait at least 4 hours for activity to appear in your report\. If you use the AWS CLI or AWS API, you must generate a new report to view the updated data\.

## Regions Where Data Is Tracked<a name="access-advisor_tracking-period"></a>

AWS collects service last accessed data in most regions\. Data is stored for a maximum of 365 days\. When AWS adds additional regions, those regions are added to the following table, including the date that AWS started tracking data in each region:


****  

| Region name | Region | Tracking start date | 
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
| Canada \(Central\) | ca\-central\-1 | October 28, 2017 | 
| EU \(Frankfurt\) | eu\-central\-1 | October 1, 2015 | 
| EU \(Ireland\) | eu\-west\-1 | October 1, 2015 | 
| EU \(London\) | eu\-west\-2 | October 28, 2017 | 
| EU \(Paris\) | eu\-west\-3 | December 18, 2017 | 
| South America \(São Paulo\) | sa\-east\-1 | December 11, 2015 | 

If a region is not listed in the previous table, then that region does not yet provide service last accessed data\.