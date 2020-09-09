# IAM: Pass an IAM role to a specific AWS service<a name="reference_policies_examples_iam-passrole-service"></a>

This example shows how you might create a policy that allows passing any IAM service role to the Amazon CloudWatch service\. This policy grants the permissions necessary to complete this action from the AWS API or AWS CLI only\. To use this policy, replace the *italicized placeholder text* in the example policy with your own information\. Then, follow the directions in [create a policy](access_policies_create.md) or [edit a policy](access_policies_manage-edit.md)\. 

A service role is an IAM role that specifies an AWS service as the principal that can assume the role\. This allows the service to assume the role and access resources in other services on your behalf\. To allow Amazon CloudWatch to assume the role that you pass, you must specify the `cloudwatch.amazonaws.com` service principal as the principal in the trust policy of your role\. The service principal is defined by the service\. To learn the service principal for a service, see the documentation for that service\. For some services, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md) and look for the services that have **Yes **in the **Service\-Linked Role** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\. Search for `amazonaws.com` to view the service principal\.

To learn more about passing a service role to a service, see [Granting a user permissions to pass a role to an AWS service](id_roles_use_passrole.md)\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:PassRole",
            "Resource": "*",
            "Condition": {
                "StringEquals": {"iam:PassedToService": "cloudwatch.amazonaws.com"}
            }
        }
    ]
}
```