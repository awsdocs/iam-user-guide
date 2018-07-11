# Actions, Resources, and Condition Keys for Amazon Mechanical Turk<a name="list_amazonmechanicalturk"></a>

Amazon Mechanical Turk \(service prefix: `mechanicalturk`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMechanicalTurkRequester/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMechanicalTurkRequester/SetUp.html#create-iam-user-or-role) permission policies\.

**Topics**
+ [Actions Defined by Amazon Mechanical Turk](#amazonmechanicalturk-actions-as-permissions)
+ [Resources Defined by MechanicalTurk](#amazonmechanicalturk-resources-for-iam-policies)
+ [Condition Keys for Amazon Mechanical Turk](#amazonmechanicalturk-policy-keys)

## Actions Defined by Amazon Mechanical Turk<a name="amazonmechanicalturk-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ ApproveAssignment ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_ApproveAssignmentOperation.html)  | The ApproveAssignment operation approves the results of a completed assignment | Write |  |  |  | 
|   [ ApproveRejectedAssignment ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_ApproveRejectedAssignmentOperation.html)  | The ApproveRejectedAssignment operation approves an assignment that was previously rejected | Write |  |  |  | 
|   [ AssignQualification ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_AssignQualificationOperation.html)  | The AssignQualification operation gives a Worker a Qualification | Write |  |  |  | 
|   [ BlockWorker ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_BlockWorkerOperation.html)  | The BlockWorker operation allows you to prevent a Worker from working on your HITs | Write |  |  |  | 
|   [ ChangeHITTypeOfHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_ChangeHITTypeOfHITOperation.html)  | The BlockWorker operation allows you to prevent a Worker from working on your HITs | Write |  |  |  | 
|   [ CreateHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_CreateHITOperation.html)  | The CreateHIT operation creates a new Human Intelligence Task \(HIT\) | Write |  |  |  | 
|   [ CreateQualificationType ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_CreateQualificationTypeOperation.html)  | The CreateQualificationType operation creates a new Qualification type, which is represented by a QualificationType data structure | Write |  |  |  | 
|   [ DisableHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_DisableHITOperation.html)  | The DisableHIT operation removes a HIT from the Amazon Mechanical Turk marketplace, approves any submitted assignments pending approval or rejection, and disposes of the HIT and all assignment data | Write |  |  |  | 
|   [ DisposeHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_DisposeHITOperation.html)  | The DisposeHIT operation disposes of a HIT that is no longer needed | Write |  |  |  | 
|   [ DisposeQualificationType ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_DisposeQualificationTypeOperation.html)  | The DisposeQualificationType operation disposes a Qualification type and disposes any HIT types that are associated with the Qualification type | Write |  |  |  | 
|   [ ExtendHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_ExtendHITOperation.html)  | The ExtendHIT operation increases the maximum number of assignments, or extends the expiration date, of an existing HIT | Write |  |  |  | 
|   [ ForceExpireHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_ForceExpireHITOperation.html)  | The ForceExpireHIT operation causes a HIT to expire immediately, as if the LifetimeInSeconds parameter of the HIT had elapsed | Write |  |  |  | 
|   [ GetAccountBalance ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetAccountBalanceOperation.html)  | The GetAccountBalance operation retrieves the amount of money in your Amazon Mechanical Turk account | Read |  |  |  | 
|   [ GetAssignment ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetAssignmentOperation.html)  | The GetAssignment operation retrieves an assignment with an AssignmentStatus value of Submitted, Approved, or Rejected, using the assignment's ID | Read |  |  |  | 
|   [ GetAssignmentsForHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetAssignmentsForHITOperation.html)  | The GetAssignmentsForHIT operation retrieves completed assignments for a HIT | Read |  |  |  | 
|   [ GetBlockedWorkers ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetBlockedWorkersOperation.html)  | The GetBlockedWorkers operation retrieves a list of Workers who are blocked from working on your HITs | Read |  |  |  | 
|   [ GetBonusPayments ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetBonusPaymentsOperation.html)  | The GetBonusPayments operation retrieves the amounts of bonuses you have paid to Workers for a given HIT or assignment | Read |  |  |  | 
|   [ GetFileUploadURL ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetFileUploadURLOperation.html)  | The GetFileUploadURL operation generates and returns a temporary URL | Read |  |  |  | 
|   [ GetHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetHITOperation.html)  | The GetHIT operation retrieves the details of the specified HIT | Read |  |  |  | 
|   [ GetHITsForQualificationType ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetHITsForQualificationTypeOperation.html)  | The GetHITsForQualificationType operation returns the HITs that use the given Qualification type for a Qualification requirement | Read |  |  |  | 
|   [ GetQualificationRequests ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetQualificationRequestsOperation.html)  | The GetQualificationRequests operation retrieves requests for Qualifications of a particular Qualification type | Read |  |  |  | 
|   [ GetQualificationScore ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetQualificationScoreOperation.html)  | The GetQualificationScore operation returns the value of a Worker's Qualification for a given Qualification type | Read |  |  |  | 
|   [ GetQualificationType ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetQualificationTypeOperation.html)  | The GetQualificationType operation retrieves information about a Qualification type using its ID | Read |  |  |  | 
|   [ GetQualificationsForQualificationType ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetQualificationsForQualificationTypeOperation.html)  | The GetQualificationsForQualificationType operation returns all of the Qualifications granted to Workers for a given Qualification type | Read |  |  |  | 
|   [ GetRequesterStatistic ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetRequesterStatisticOperation.html)  | The GetRequesterStatistic operation retrieves statistics about you \(the Requester calling the operation\) | Read |  |  |  | 
|   [ GetRequesterWorkerStatistic ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetRequesterWorkerStatisticOperation.html)  | The GetRequesterWorkerStatistic operation retrieves statistics about a specific Worker who has completed Human Intelligence Tasks \(HITs\) for you | Read |  |  |  | 
|   [ GetReviewResultsForHIT ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetReviewResultsForHITOperation.html)  | The GetReviewResultsForHIT operation retrieves the computed results and the actions taken in the course of executing your Review Policies during a CreateHIT operation | Read |  |  |  | 
|   [ GetReviewableHITs ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GetReviewableHITsOperation.html)  | The GetReviewableHITs operation retrieves the HITs with Status equal to Reviewable or Status equal to Reviewing that belong to the Requester calling the operation | Read |  |  |  | 
|   [ GrantBonus ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GrantBonusOperation.html)  | The GrantBonus operation issues a payment of money from your account to a Worker | Write |  |  |  | 
|   [ GrantQualification ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_GrantQualificationOperation.html)  | The GrantQualification operation grants a Worker's request for a Qualification | Write |  |  |  | 
|   [ NotifyWorkers ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_NotifyWorkersOperation.html)  | The NotifyWorkers operation sends an email to one or more Workers that you specify with the Worker ID | Write |  |  |  | 
|   [ RegisterHITType ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_RegisterHITTypeOperation.html)  | The RegisterHITType operation creates a new HIT type | Write |  |  |  | 
|   [ RejectAssignment ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_RejectAssignmentOperation.html)  | The RejectAssignment operation rejects the results of a completed assignment | Write |  |  |  | 
|   [ RejectQualificationRequest ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_RejectQualificationRequestOperation.html)  | The RejectQualificationRequest operation rejects a user's request for a Qualification | Write |  |  |  | 
|   [ RevokeQualification ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_RevokeQualificationOperation.html)  | The RevokeQualification operation revokes a previously granted Qualification from a user | Write |  |  |  | 
|   [ SearchHITs ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_SearchHITsOperation.html)  | The SearchHITs operation returns all of a Requester's HITs, on behalf of the Requester | Read |  |  |  | 
|   [ SearchQualificationTypes ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_SearchQualificationTypesOperation.html)  | The SearchQualificationTypes operation searches for Qualification types using the specified search query, and returns a list of Qualification types | Read |  |  |  | 
|   [ SendTestEventNotification ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_SendTestEventNotificationOperation.html)  | The SendTestEventNotification operation causes Amazon Mechanical Turk to send a notification message as if a HIT event occurred, according to the provided notification specification | Write |  |  |  | 
|   [ SetHITAsReviewing ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_SetHITAsReviewingOperation.html)  | The SetHITAsReviewing operation updates the status of a HIT | Write |  |  |  | 
|   [ SetHITTypeNotification ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_SetHITTypeNotificationOperation.html)  | The SetHITTypeNotification operation creates, updates, disables or re\-enables notifications for a HIT type | Write |  |  |  | 
|   [ UnblockWorker ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_UnblockWorkerOperation.html)  | The UnblockWorker operation allows you to reinstate a blocked Worker to work on your HITs | Write |  |  |  | 
|   [ UpdateQualificationScore ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_UpdateQualificationScoreOperation.html)  | The UpdateQualificationScore operation changes the value of a Qualification previously granted to a Worker | Write |  |  |  | 
|   [ UpdateQualificationType ](http://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_UpdateQualificationTypeOperation.html)  | The UpdateQualificationType operation modifies the attributes of an existing Qualification type, which is represented by a QualificationType data structure | Write |  |  |  | 

## Resources Defined by MechanicalTurk<a name="amazonmechanicalturk-resources-for-iam-policies"></a>

Amazon Mechanical Turk has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for Amazon Mechanical Turk<a name="amazonmechanicalturk-policy-keys"></a>

MechanicalTurk has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.