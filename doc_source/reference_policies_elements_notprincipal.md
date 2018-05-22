# IAM JSON Policy Elements: NotPrincipal<a name="reference_policies_elements_notprincipal"></a>

Use the `NotPrincipal` element to specify an exception to a list of principals\. For example, you can deny access to all principals *except* the one named in the `NotPrincipal` element\. The syntax for specifying `NotPrincipal` is the same as for specifying [IAM JSON Policy Elements: Principal](reference_policies_elements_principal.md)\.

Note that you can also use `NotPrincipal` to allow all principals *except* the one named in the `NotPrincipal` element; however, we do not recommend this\. 

**Warning**  
When you use `NotPrincipal` in the same policy statement as `"Effect": "Allow"`, the permissions specified in the policy statement will be granted to *all* principals except for the one\(s\) specified, including anonymous \(unauthenticated\) users\. We strongly recommend you do not use `NotPrincipal` in the same policy statement as `"Effect": "Allow"`\. 

When you use `NotPrincipal` in the same policy statement as `"Effect": "Deny"`, the permissions specified in the policy statement are explicitly denied to all principals *except* for the one\(s\) specified\. This enables you to implement a form of "whitelisting"\. When you explicitly deny access to an AWS account, you deny access to all users contained in that account\.

Note that if a resource\-based policy combines `"Effect": "Deny"` with a `NotPrincipal` element that specifies only a principal in an AWS account, the policy is likely denying access to the account containing the principal, and that in turn results in the specified principal not being able to access the resource\. To understand how this can happen, see the examples in the next section\.

**Important**  
Very few scenarios require the use of `NotPrincipal`, and we recommend that you explore other authorization options before you decide to use `NotPrincipal`\. 

## Specifying `NotPrincipal` in the same policy statement as `"Effect": "Deny"`<a name="specifying-notprincipal"></a>

You specify principals in the `NotPrincipal` element using the same syntax that you use for specifying principals in the [IAM JSON Policy Elements: Principal](reference_policies_elements_principal.md) element\. However, it can be difficult to achieve the intended effect, particularly when you combine `NotPrincipal` with `"Effect": "Deny"` in the same policy statement and you work across AWS account boundaries\. 

**Important**  
Combining `Deny` and `NotPrincipal` is the only time that the order in which AWS evaluates principals makes a difference\. AWS internally validates the principals from the "top down," meaning that AWS checks the account first and then the user\. If an assumed\-role user \(someone who is using a role rather than an IAM user\) is being evaluated, AWS looks at the account first, then the role, and finally the assumed\-role user\. The assumed\-role user is identified by the role session name that is specified when the user assumes the role\.  
Normally, this order does not have any impact on the results of the policy evaluation\. However, when you use both `Deny` and `NotPrincipal`, the evaluation order requires you to explicitly include the ARNs for the entities associated with the specified principal\. For example, to specify a user, you must explicitly include the ARN for the user's account\. To specify an assumed\-role user, you must also include both the ARN for the role and the ARN for the account containing the role\.

The following examples show how to use `NotPrincipal` and `"Effect": "Deny"` in the same policy statement effectively\.

**Example 1: An IAM user in the same or a different account**  
In the following example, all principals *except* the user named Bob in AWS account 444455556666 are explicitly denied access to a resource\. Note that to achieve the intended effect, the `NotPrincipal` element contains the ARN of both the user Bob and the AWS account that Bob belongs to \(`arn:aws:iam::444455556666:root`\)\. If the `NotPrincipal` element contained only Bob's ARN, the effect of the policy would be to explicitly deny access to the AWS account that contains the user Bob\. A user cannot have more permissions than its parent account, so if Bob's account is explicitly denied access then Bob is also unable to access the resource\.  
This example works as intended when it is part of a policy statement in a resource\-based policy that is attached to a resource in either the same or a different AWS account \(not 444455556666\)\. This example by itself does not grant access to Bob, it only omits Bob from the list of principals that are explicitly denied\. To give Bob access to the resource, another policy statement must explicitly allow access using `"Effect": "Allow"`\.  

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

**Example 2: An IAM role in the same or different account**  
In the following example, all principals *except* the assumed\-role user named cross\-account\-audit\-app in AWS account 444455556666 are explicitly denied access to a resource\. Note that to achieve the intended effect, the `NotPrincipal` element contains the ARN of the assumed\-role user \(cross\-account\-audit\-app\), the role \(cross\-account\-read\-only\-role\), and the AWS account that the role belongs to \(444455556666\)\. If the `NotPrincipal` element was missing the ARN of the role, the effect of the policy would be to explicitly deny access to the role\. Similarly, if the `NotPrincipal` element was missing the ARN of the AWS account that the role belongs to, the effect of the policy would be to explicitly deny access to the AWS account and all entities in that account\. Assumed\-role users cannot have more permissions than their parent role, and roles cannot have more permissions than their parent AWS account, so when the role or the account is explicitly denied access, the assumed role user is unable to access the resource\.   
This example works as intended when it is part of a policy statement in a resource\-based policy that is attached to a resource in a different AWS account \(not 444455556666\)\. This example by itself does not grant access to the assumed\-role user cross\-account\-audit\-app, it only omits cross\-account\-audit\-app from the list of principals that are explicitly denied\. To give cross\-account\-audit\-app access to the resource, another policy statement must explicitly allow access using `"Effect": "Allow"`\.  

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