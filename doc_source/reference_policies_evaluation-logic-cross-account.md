# Cross\-account policy evaluation logic<a name="reference_policies_evaluation-logic-cross-account"></a>

You can allow a principal in one account to access resources in a second account\. This is called cross\-account access\. When you allow cross\-account access, the account where the principal exists is called the *trusted* account\. The account where the resource exists is the *trusting* account\. 

To allow cross\-account access, you attach a resource\-based policy to the resource that you want to share\. You must also attach an identity\-based policy to the identity that acts the principal in the request\. The resource\-based policy in the trusting account must specify the principal of the trusted account that will have access the resource\. You can specify the entire account or its IAM users, federated users, IAM roles, or assumed\-role sessions\. You can also specify an AWS service as a principal\. For more information, see [Specifying a principal](reference_policies_elements_principal.md#Principal_specifying)\. 

The principal's identity\-based policy must allow the requested access to the resource in the trusting service\. You can do this by specifying the ARN of the resource or by allowing access to all resources \(`*`\)\.

In IAM, you can attach a resource\-based policy to an IAM role to allow principals in other accounts to assume that role\. The role's resource\-based policy is called a role trust policy\. After assuming that role, the allowed principals can use the resulting temporary credentials to access multiple resources in your account\. This access is defined in the role's identity\-based permissions policy\. To learn how allowing cross\-account access using roles is different from allowing cross\-account access using other resource\-based policies, see [How IAM roles differ from resource\-based policies](id_roles_compare-resource-policies.md)\. 

**Important**  
Other services can affect the policy evaluation logic\. For example, AWS Organizations supports [service control policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html) that can be applied to principals one or more accounts\. AWS Resource Access Manager supports [policy fragments](https://docs.aws.amazon.com/ram/latest/userguide/permissions.html) that control which actions that principals are allowed to perform on resources that are shared with them\.

## Determining whether a cross\-account request is allowed<a name="policy-eval-cross-account"></a>

For cross\-account requests, the requester in the trusted `AccountA` must have an identity\-based policy\. That policy must allow them to make a request to the resource in the trusting `AccountB`\. Additionally, the resource\-based policy in `AccountB` must allow the requester in `AccountA` to access the resource\.

When you make a cross\-account request, AWS performs two evaluations\. AWS evaluates the request in the trusting account and the trusted account\. For more information about how a request is evaluated within a single account, see [Determining whether a request is allowed or denied within an account](reference_policies_evaluation-logic.md#policy-eval-denyallow)\. The request is allowed only if both evaluations return a decision of `Allow`\.

![\[Cross-account evalusation\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_cross-account-eval-simple.png)

1. When a principal in one account makes a request to access a resource in another account, this is a cross\-account request\.

1. The requesting principal exists in the trusted account \(`AccountA`\)\. When AWS evaluates this account, it checks the identity\-based policy and any policies that can limit an identity\-based policy\. For more information, see [Evaluating policies within a single account](reference_policies_evaluation-logic.md#policy-eval-basics)\.

1. The requested resource exists in the trusting account \(`AccountB`\)\. When AWS evaluates this account, it checks the resource\-based policy that is attached to the requested resource and any policies that can limit a resource\-based policy\. For more information, see [Evaluating policies within a single account](reference_policies_evaluation-logic.md#policy-eval-basics)\.

1. AWS allows the request only if both account policy evaluations allow the request\.

## Example cross\-account policy evaluation<a name="policies_evaluation_example-cross-account"></a>

The following example demonstrates a scenario where a user in one account is granted permissions by a resource\-based policy in a second account\.

Assume that Carlos is a developer with an IAM user named `carlossalazar` in account 111111111111\. He wants to save a file to the `Production-logs` Amazon S3 bucket in account 222222222222\. 

Also assume that the following policy is attached to the `carlossalazar` IAM user\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowS3ListRead",
            "Effect": "Allow",
            "Action": "s3:ListAllMyBuckets",
            "Resource": "*"
        },
        {
            "Sid": "AllowS3ProductionObjectActions",
            "Effect": "Allow",
            "Action": "s3:*Object*",
            "Resource": "arn:aws:s3:::Production/*"
        },
        {
            "Sid": "DenyS3Logs",
            "Effect": "Deny",
            "Action": "s3:*",
            "Resource": [
                "arn:aws:s3:::*log*",
                "arn:aws:s3:::*log*/*"
            ]
        }
    ]
}
```

The `AllowS3ListRead` statement in this policy allows Carlos to view a list of all of the buckets in Amazon S3\. The `AllowS3ProductionObjectActions` statement allows Carlos full access to objects in the `Production` bucket\. The `DenyS3Logs` statement denies Carlos access to any S3 bucket with `log` in its name\. It also denies access to all objects in those buckets\.

Additionally, the following resource\-based policy \(called a bucket policy\) is attached to the `Production` bucket in account 222222222222\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject*",
                "s3:PutObject*",
                "s3:ReplicateObject",
                "s3:RestoreObject"
            ],
            "Principal": { "AWS": "arn:aws:iam::111111111111:user/carlossalazar" },
            "Resource": "arn:aws:s3:::Production/*"
        }
    ]
}
```

This policy allows the `carlossalazar` user to access objects in the `Production` bucket\. He can create and edit, but not delete the objects in the bucket\. He can't manage the bucket itself\.

When Carlos makes his request to save a file to the `Production-logs` bucket, AWS determines what policies apply to the request\. In this case, the identity\-based policy attached to the `carlossalazar` user is the only policy that applies in account `111111111111`\. In account `222222222222`, there is no resource\-based policy attached to the `Production-logs` bucket\. When AWS evaluates account `111111111111`, it returns a decision of `Deny`\. This is because the `DenyS3Logs` statement in the identity\-based policy explicitly denies access to any log buckets\. For more information about how a request is evaluated within a single account, see [Determining whether a request is allowed or denied within an account](reference_policies_evaluation-logic.md#policy-eval-denyallow)\.

Because the request is explicitly denied within one of the accounts, the final decision is to deny the request\.

![\[Request to Production-logs bucket\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_cross-account-eval-example.png)

Assume that Carlos then realizes his mistake and tries to save the file to the `Production` bucket\. AWS first checks account `111111111111` to determine if the request is allowed\. Only the identity\-based policy applies, and it allows the request\. AWS then checks account `222222222222`\. Only the resource\-based policy attached to the `Production` bucket applies, and it allows the request\. Because both accounts allow the request, the final decision is to allow the request\.

![\[Request to Production bucket\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/policy_cross-account-eval-example-correct.png)