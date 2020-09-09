# AWS JSON policy elements: NotPrincipal<a name="reference_policies_elements_notprincipal"></a>

Use the `NotPrincipal` element to specify the IAM user, federated user, IAM role, AWS account, AWS service, or other principal that is ***not*** allowed or denied access to a resource\. The `NotPrincipal` element enables you to specify an exception to a list of principals\. Use this element to deny access to all principals *except* the one named in the `NotPrincipal` element\. The syntax for specifying `NotPrincipal` is the same as for specifying [AWS JSON policy elements: Principal](reference_policies_elements_principal.md)\.

You cannot use the `NotPrincipal` element in an IAM identity\-based policy\. You can use it in the trust policies for IAM roles and in resource\-based policies\. Resource\-based policies are policies that you embed directly in an IAM resource\. 

**Important**  
Very few scenarios require the use of `NotPrincipal`, and we recommend that you explore other authorization options before you decide to use `NotPrincipal`\. 

## `NotPrincipal` With `Allow`<a name="specifying-notprincipal-allow"></a>

We strongly recommend that you do not use `NotPrincipal` in the same policy statement as `"Effect": "Allow"`\. Doing so allows all principals *except* the one named in the `NotPrincipal` element\. We do not recommend this because the permissions specified in the policy statement will be granted to *all* principals except for the ones specified\. By doing this, you might grant access to anonymous \(unauthenticated\) users\. 

## `NotPrincipal` With `Deny`<a name="specifying-notprincipal"></a>

When you use `NotPrincipal` in the same policy statement as `"Effect": "Deny"`, the actions specified in the policy statement are explicitly denied to all principals *except* for the ones specified\. You can use this method to implement a form of whitelisting\. When you use `NotPrincipal` with `Deny`, you must also specify the account ARN of the not\-denied principal\. Otherwise, the policy might deny access to the entire account containing the principal\. Depending on the service that you include in your policy, AWS might validate the account first and then the user\. If an assumed\-role user \(someone who is using a role\) is being evaluated, AWS might validate the account first, then the role, and then the assumed\-role user\. The assumed\-role user is identified by the role session name that is specified when they assumed the role\. Therefore, we strongly recommend that you explicitly include the ARN for a user's account, or include both the ARN for a role and the ARN for the account containing that role\.

**Note**  
As a best practice, you should include the ARNs for the account in your policy\. Some services require the account ARN, although this is not required in all cases\. Any existing policies without the required ARN will continue to work, but new policies that include these services must meet this requirement\. IAM does not track these services, and therefore recommends that you always include the account ARN\.

The following examples show how to use `NotPrincipal` and `"Effect": "Deny"` in the same policy statement effectively\.

**Example IAM user in the same or a different account**  
In the following example, all principals *except* the user named Bob in AWS account 444455556666 are explicitly denied access to a resource\. Note that as a best practice, the `NotPrincipal` element contains the ARN of both the user Bob and the AWS account that Bob belongs to \(`arn:aws:iam::444455556666:root`\)\. If the `NotPrincipal` element contained only Bob's ARN, the effect of the policy might be to explicitly deny access to the AWS account that contains the user Bob\. In some cases, a user cannot have more permissions than its parent account, so if Bob's account is explicitly denied access then Bob might be unable to access the resource\.  
This example works as intended when it is part of a policy statement in a resource\-based policy that is attached to a resource in either the same or a different AWS account \(not 444455556666\)\. This example by itself does not grant access to Bob, it only omits Bob from the list of principals that are explicitly denied\. To allow Bob access to the resource, another policy statement must explicitly allow access using `"Effect": "Allow"`\.  

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Deny",
        "NotPrincipal": {"AWS": [
            "arn:aws:iam::444455556666:user/Bob",
            "arn:aws:iam::444455556666:root"
        ]},
        "Action": "s3:*",
        "Resource": [
            "arn:aws:s3:::BUCKETNAME",
            "arn:aws:s3:::BUCKETNAME/*"
        ]
    }]
}
```

**Example IAM role in the same or different account**  
In the following example, all principals *except* the assumed\-role user named cross\-account\-audit\-app in AWS account 444455556666 are explicitly denied access to a resource\. As a best practice, the `NotPrincipal` element contains the ARN of the assumed\-role user \(cross\-account\-audit\-app\), the role \(cross\-account\-read\-only\-role\), and the AWS account that the role belongs to \(444455556666\)\. If the `NotPrincipal` element was missing the ARN of the role, the effect of the policy might be to explicitly deny access to the role\. Similarly, if the `NotPrincipal` element was missing the ARN of the AWS account that the role belongs to, the effect of the policy might be to explicitly deny access to the AWS account and all entities in that account\. In some cases, assumed\-role users cannot have more permissions than their parent role, and roles cannot have more permissions than their parent AWS account, so when the role or the account is explicitly denied access, the assumed role user might be unable to access the resource\.   
This example works as intended when it is part of a policy statement in a resource\-based policy that is attached to a resource in a different AWS account \(not 444455556666\)\. This example by itself does not allow access to the assumed\-role user cross\-account\-audit\-app, it only omits cross\-account\-audit\-app from the list of principals that are explicitly denied\. To give cross\-account\-audit\-app access to the resource, another policy statement must explicitly allow access using `"Effect": "Allow"`\.  

```
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Deny",
        "NotPrincipal": {"AWS": [
            "arn:aws:sts::444455556666:assumed-role/cross-account-read-only-role/cross-account-audit-app",
            "arn:aws:iam::444455556666:role/cross-account-read-only-role",
            "arn:aws:iam::444455556666:root"
        ]},
        "Action": "s3:*",
        "Resource": [
            "arn:aws:s3:::Bucket_AccountAudit",
            "arn:aws:s3:::Bucket_AccountAudit/*"
        ]
    }]
}
```
When you specify an assumed\-role session in a `NotPrincipal` element, you cannot use a wildcard \(\*\) to mean "all sessions"\. Principals must always name a specific session\.