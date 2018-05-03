# IAM JSON Policy Evaluation Logic<a name="reference_policies_evaluation-logic"></a>

**Topics**
+ [Policy Evaluation Basics](#policy-eval-basics)
+ [The Impact of AWS Organizations on IAM Policies](#evaluation-logic-organizations)
+ [The Request Context](#policy-eval-reqcontext)
+ [Determining Whether a Request is Allowed or Denied](#policy-eval-denyallow)
+ [The Difference Between Denying by Default and Explicit Deny](#AccessPolicyLanguage_Interplay)

## Policy Evaluation Basics<a name="policy-eval-basics"></a>

When an AWS service receives a request, the request is first authenticated using information about the access key ID and signature\. \(A few services, like Amazon S3, allow requests from anonymous users\.\) If the request passes authentication, AWS then determines whether the requester is authorized to perform the action represented by the request\. 

Requests that are made by the AWS account root user are allowed for resources in that account\. However, the request might be made using the credentials of an IAM user\. Or the request could be signed using temporary credentials that are granted by AWS STS\., In either of those cases, AWS uses the permissions that are defined in one or more IAM policies to determine whether the user's request is authorized\. 

**Note**  
Amazon S3 supports Access Control Lists \(ACLs\) and resource\-level policies for buckets and objects\. The permissions established using ACLs and bucket\-level policies can affect what actions the root user is allowed to perform on a bucket\. For more information, see [Guidelines for Using the Available Access Policy Options](http://docs.aws.amazon.com/AmazonS3/latest/dev/access-policy-alternatives-guidelines.html) in the *Amazon Simple Storage Service Developer Guide*\. 

## The Impact of AWS Organizations on IAM Policies<a name="evaluation-logic-organizations"></a>

AWS Organizations is a service that enables you to group together and centrally manage the AWS accounts that your business owns\. If you enable all features in an organization, then you can apply service control policies \(SCPs\) to any or all of your accounts\. These SCPs serve as "filters" or "guardrails" that limit what services and actions can be accessed by the IAM users, groups, and roles in those accounts\. If an SCP that is attached to an account denies access to a service, such as Amazon S3, then no user in that account can access any Amazon S3 API\. This is so even if the user has administrator permissions in the account\. Even the AWS account root user is denied access to Amazon S3 API operations\.

An IAM user in an account that is in an organization can use the *intersection* of all permissions defined in Organizations, IAM, and other affected services\. IAM permissions policies are attached to the entity that you use to sign in to AWS\. Organizations SCPs apply to the account that you use to sign in\. Resource\-based policies are attached to a resource within a service and define who can access the resource\.

For more information about Organizations and SCPs, see [About Service Control Policies](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_about-scps.html) in the *AWS Organizations User Guide*\.

## The Request Context<a name="policy-eval-reqcontext"></a>

When AWS authorizes a request, information about the request is assembled from several sources:
+ Principal \(the requester\), which is determined based on the secret access key\. This might represent the root user, an IAM user, a federated user \(via AWS STS\), or an assumed role, and includes the aggregate permissions that are associated with that principal\. 
+ Environment data, such as the IP address, user agent, SSL enabled, the time of day, etc\. This information is determined from the request\.
+ Resource data, which pertains to information that is part of the resource being requested\. This can include information such as a DynamoDB table name, a tag on an Amazon EC2 instance, etc\. 

This information is gathered into a *request context*, which is a collection of information that's derived from the request\. During evaluation, AWS uses values from the request context to determine whether to allow or deny the request\. For example, does the action in the request context match an action in the `Action` element? If not, the request is denied\. Similarly, does the resource in the request context match one of the resources in the `Resource` element? If not, the request is denied\.

This is also how the keys work that you can use in the `Condition` element\. For example, for the following policy fragment, AWS uses the date and time from the current request context for the `aws:CurrentTime` key and then performs the `DateGreaterThan` and `DateLessThan` comparisons\.

```
"Condition" :  {
  "DateGreaterThan" : {
    "aws:CurrentTime" : "2013-08-16T12:00:00Z"
  },
  "DateLessThan": {
    "aws:CurrentTime" : "2013-08-16T15:00:00Z"
  }
}
```

Policy variables like `${aws:username}` also work like this\. In the following policy fragment, AWS gets the user name from the request context and uses it in the policy at the place where the `${aws:username}` occurs\.

```
"Resource": [
  "arn:aws:s3:::mybucket/${aws:username}/*"
]
```

## Determining Whether a Request is Allowed or Denied<a name="policy-eval-denyallow"></a>

When a request is made, the AWS service decides whether a given request should be allowed or denied\. The evaluation logic follows these rules:
+ By default, all requests are denied\. \(In general, requests made using the account credentials for resources in the account are always allowed\.\) 
+ An explicit allow overrides this default\.
+ An explicit deny overrides any allows\.

The order in which the policies are evaluated has no effect on the outcome of the evaluation\. All policies are evaluated, and the result is always that the request is either allowed or denied\.

The following flow chart provides details about how the decision is made\.

![\[Evaluation flow chart\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Evaluation_Flow.diagram.png)

1. The decision starts by assuming that the request will be denied\.

1. The enforcement code evaluates all user\-based and resource\-based policies that are applicable to the request \(based on the resource, principal, action, and conditions\)\. 

   The order in which the enforcement code evaluates the policies is not important\.

1. In all those policies, the enforcement code looks for an explicit deny instruction that would apply to the request\.

   If the code finds even one explicit deny that applies, the code returns a decision of `Deny` and the process is finished\.

1. If no explicit deny is found, the code looks for any `Allow` instructions that would apply to the request\.

   If it finds even one explicit allow, the code returns a decision of `Allow` and the service continues to process the request\. 

1. If no allow is found, the final decision is `Deny`\.

   If the code encounters an error at any point during the evaluation, then it will generate an exception and close\.

The following example illustrates how you can use an explicit deny to override a broad policy that allows access to a wide set of resources\. Let's say that you give an IAM group permissions to use any Amazon SQS queues in your AWS account whose names begin with the string `test`\. 

The following diagram represents that set of queues\.

![\[Set of queues whose names start with test\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Explicit_Deny_Override_1.diagram.png)

Let's say that you have a queue called `test0` that you want to remove the group's access to\. The following diagram represents that set of queues\.

![\[Set of queues whose names start with test, except for test0\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Explicit_Deny_Override_2.diagram.png)

You could add another policy to the group, or another statement to the existing policy, that explicitly denies the group's access to the `test0` queue\. The group would still have access to all other queues whose names begin with the string `test`\. The following diagram illustrates those two statements in the policy\.

![\[Example policy for explicit deny overriding allow\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Explicit_Deny_Override_3.diagram.png)

When any user in the group makes a request to use the queue `test0`, the explicit deny overrides the allow, and the user is denied access to the queue\.

## The Difference Between Denying by Default and Explicit Deny<a name="AccessPolicyLanguage_Interplay"></a>

A policy results in a deny if the policy doesn't directly apply to the request\. For example, a user might make a request to use Amazon SQS, but the only policy that applies to the user states that the user can use Amazon S3\. In that case, the request is denied\. 

A policy also results in a deny if a condition in a statement isn't met\. If all conditions in the statement are met, the policy results in either an allow or an explicit deny, based on the value of the `Effect` element in the policy\. Policies don't specify what to do if a condition isn't met, so the result in that case is `Deny`\.

For example, let's say you want to prevent requests that come from Antarctica\. You write a policy called Policy A1 that allows a request only if it doesn't come from Antarctica\. The following diagram illustrates the policy\.

![\[Policy allowing request if it's not from Antarctica\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Allow_Override_1.diagram.png)

If someone sends a request from the US, the condition is met \(the request is not from Antarctica\)\. Therefore, the result is `Allow`\. But if someone sends a request from Antarctica, the condition isn't met, and the policy's result is therefore `Deny`\. 

You could *explicitly* deny access from Antarctica by creating a different policy \(named Policy A2\) as in the following diagram\.

![\[Policy denying request if it's from Antarctica\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Allow_Override_2.diagram.png)

If this policy applies to a user who sends a request from Antarctica, the condition is met, and the policy's result is therefore `Deny`\.

The distinction between a request being denied by default and an explicit deny in a policy is important\. By default, a request is denied, but this can be overridden by an allow\. In contrast, if a policy explicitly denies a request, that deny can't be overridden\. 

For example, let's say there's another policy that allows requests if they arrive on June 1, 2010\. How does this policy affect the outcome when evaluated together with the policy that restricts access from Antarctica? We'll compare the outcome when evaluating the date\-based policy \(we'll call it Policy B\) with the preceding policies \(A1 and A2\)\. Scenario 1 evaluates Policy A1 with Policy B, and Scenario 2 evaluates Policy A2 with Policy B\. The following figure shows the results when a request comes in from Antarctica on June 1, 2010\.

![\[Override of deny by default\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/AccessPolicyLanguage_Allow_Override.diagram.png)

In Scenario 1, Policy A1 returns `Deny` because requests are allowed only if they don't come from Antarctica; any other condition \(requests that do come from Antarctica\) are denied by default\. Policy B returns an allow because the request arrives on June 1, 2010\. The allow from Policy B overrides the default deny from Policy A1, and the request is therefore allowed\.

In Scenario 2, Policy A2 returns an explicit deny, as described earlier in this section\. Again, Policy B returns an allow\. However, the explicit deny from Policy A2 overrides the allow from Policy B, and the request is therefore `Deny`\.