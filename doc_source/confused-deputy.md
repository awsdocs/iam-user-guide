# The confused deputy problem<a name="confused-deputy"></a>

The confused deputy problem is a security issue where an entity that doesn't have permission to perform an action can coerce a more\-privileged entity to perform the action\. To prevent this, AWS provides tools that help you protect your account if you provide third parties \(known as *cross\-account*\) or other AWS services \(known as *cross\-service*\) access to resources in your account\.

At times, you might need to give a third party access to your AWS resources \(delegate access\)\. For example, let's say that you decide to hire a third\-party company called Example Corp to monitor your AWS account and help optimize costs\. In order to track your daily spending, Example Corp needs to access your AWS resources\. Example Corp also monitors many other AWS accounts for other customers\. You can use an IAM role to establish a trusted relationship between your AWS account and the Example Corp account\. One important aspect of this scenario is the *external ID*, optional information that you can use in an IAM role trust policy to designate who can assume the role\. The primary function of the external ID is to address and prevent the confused deputy problem\.

In AWS, cross\-service impersonation can result in the confused deputy problem\. Cross\-service impersonation can occur when one service \(the *calling service*\) calls another service \(the *called service*\)\. The calling service can be manipulated to use its permissions to act on another customer's resources in a way it should not otherwise have permission to access\.

## Cross\-account confused deputy prevention<a name="mitigate-confused-deputy"></a>

The following diagram illustrates the cross\-account confused deputy problem\.

![\[The description of a confused deputy problem.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[The description of a confused deputy problem.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[The description of a confused deputy problem.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

This scenario assumes the following:
+ **AWS1** is your AWS account\.
+ **AWS1:ExampleRole** is a role in your account\. This role's trust policy trusts Example Corp by specifying Example Corp's AWS account as the one that can assume the role\.

Here's what happens:

1. When you start using Example Corp's service, you provide the ARN of **AWS1:ExampleRole** to Example Corp\.

1. Example Corp uses that role ARN to obtain temporary security credentials to access resources in your AWS account\. In this way, you are trusting Example Corp as a "deputy" that can act on your behalf\.

1. Another AWS customer also starts using Example Corp's service, and this customer also provides the ARN of **AWS1:ExampleRole** for Example Corp to use\. Presumably the other customer learned or guessed the **AWS1:ExampleRole**, which isn't a secret\.

1. When the other customer asks Example Corp to access AWS resources in \(what it claims to be\) its account, Example Corp uses **AWS1:ExampleRole** to access resources in your account\.

This is how the other customer could gain unauthorized access to your resources\. Because this other customer was able to trick Example Corp into unwittingly acting on your resources, Example Corp is now a "confused deputy\."

Example Corp can address the confused deputy problem by requiring that you include the `ExternalId` condition check in the role's trust policy\. Example Corp generates a unique `ExternalId` value for each customer and uses that value in its request to assume the role\. The `ExternalId` value must be unique among Example Corp's customers and controlled by Example Corp, not its customers\. This is why you get it from Example Corp and you don't come up with it on your own\. This prevents Example Corp from being a confused deputy and granting access to another account's AWS resources\.

In our scenario, imagine Example Corp's unique identifier for you is 12345, and its identifier for the other customer is 67890\. These identifiers are simplified for this scenario\. Generally, these identifiers are GUIDs\. Assuming that these identifiers are unique among Example Corp's customers, they are sensible values to use for the external ID\. 

Example Corp gives the external ID value of 12345 to you\. You must then add a `Condition` element to the role's trust policy that requires the `sts:ExternalId` value to be 12345, like this:

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {
      "AWS": "Example Corp's AWS Account ID"
    },
    "Action": "sts:AssumeRole",
    "Condition": {
      "StringEquals": {
        "sts:ExternalId": "12345"
      }
    }
  }
}
```

The Condition element in this policy allows Example Corp to assume the role only when the AssumeRole API call includes the external ID value of 12345\. Example Corp makes sure that whenever it assumes a role on behalf of a customer, it always includes that customer's external ID value in the AssumeRole call\. Even if another customer supplies Example Corp with your ARN, it cannot control the external ID that Example Corp includes in its request to AWS\. This helps prevent an unauthorized customer from gaining access to your resources\.

The following diagram illustrates this\.

![\[How to mitigate a confused deputy problem.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[How to mitigate a confused deputy problem.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)![\[How to mitigate a confused deputy problem.\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/)

1. As before, when you start using Example Corp's service, you provide the ARN of **AWS1:ExampleRole** to Example Corp\.

1.  When Example Corp uses that role ARN to assume the role **AWS1:ExampleRole**, Example Corp includes your external ID \(12345\) in the AssumeRole API call\. The external ID matches the role's trust policy, so the AssumeRole API call succeeds and Example Corp obtains temporary security credentials to access resources in your AWS account\.

1. Another AWS customer also starts using Example Corp's service, and as before, this customer also provides the ARN of **AWS1:ExampleRole** for Example Corp to use\. 

1. But this time, when Example Corp attempts to assume the role **AWS1:ExampleRole**, it provides the external ID associated with the other customer \(67890\)\. The other customer has no way to change this\. Example Corp does this because the request to use the role came from the other customer, so 67890 indicates the circumstance in which Example Corp is acting\. Because you added a condition with your own external ID \(12345\) to the trust policy of **AWS1:ExampleRole**, the AssumeRole API call fails\. The other customer is prevented from gaining unauthorized access to resources in your account \(indicated by the red "X" in the diagram\)\.

The external ID helps prevent any other customer from tricking Example Corp into unwittingly accessing your resources\.

## Cross\-service confused deputy prevention<a name="cross-service-confused-deputy-prevention"></a>

We recommend using the [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-sourcearn](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-sourcearn) and [https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-sourceaccount](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-sourceaccount) global condition context keys in resource\-based policies to limit the permissions that a service has to a specific resource\. If the `aws:SourceArn` value does not contain the account ID, such as an Amazon S3 bucket ARN, you must use both global condition context keys to limit permissions\. If you use both global condition context keys and the `aws:SourceArn` value contains the account ID, the `aws:SourceAccount` value and the account in the `aws:SourceArn` value must use the same account ID when used in the same policy statement\. Use `aws:SourceArn` if you want only one resource to be associated with the cross\-service access\. Use `aws:SourceAccount` if you want to allow any resource in that account to be associated with the cross\-service use\.

The most effective way to protect against the confused deputy problem is to use the `aws:SourceArn` global condition context key with the full ARN of the resource in your resource\-based policies\. If you don't know the full ARN of the resource or if you are specifying multiple resources, use the `aws:SourceArn` global condition context key with wildcards \(`*`\) for the unknown portions of the ARN\. For example, `arn:aws:servicename:*:123456789012:*`\.

### Cross\-service confused deputy prevention for AWS Security Token Service<a name="cross-service-confused-deputy-prevention-sts"></a>

Many AWS services require that you use roles to allow the service to access another service's resources on your behalf\. A role that a service assumes to perform actions on your behalf is called a [service role](id_roles_terms-and-concepts.md#iam-term-service-role)\. A role requires two policies: a role trust policy that specifies the principal that is allowed to assume the role and a permissions policy that specifies what can be done with the role\. A role trust policy is the only type of resource\-based policy in IAM\. Other AWS services have resource\-based policies, such as an Amazon S3 bucket policy\.

When a service assumes a role on your behalf, the service principal must be allowed to perform the `sts:AssumeRole` action in the role trust policy\. When a service calls `sts:AssumeRole`, AWS STS returns a set of temporary security credentials that the service principal uses to access the resources that are permitted by the role’s permissions policy\. When a service assumes a role in your account, you can include the `aws:SourceAccount` and `aws:SourceArn` global condition context keys in your role trust policy to limit access to the role to only requests that are generated by expected resources\.

For example, in AWS Systems Manager Incident Manager, you must choose a role to allow Incident Manager to run a Systems Manager automation document on your behalf\. The automation document can include automated response plans for incidents that are initiated by CloudWatch alarms or EventBridge events\. In the following role trust policy example, you can use the `aws:SourceArn` condition key to restrict access to the service role based on the incident record's ARN\. Only incident records that are created from the response plan resource `myresponseplan` are able to use this role\.

```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {
      "Service": "ssm-incidents.amazonaws.com"
    },
    "Action": "sts:AssumeRole",
    "Condition": {
      "ArnLike": {
        "aws:SourceArn": "arn:aws:ssm-incidents:*:111122223333:incident-record/myresponseplan/*"
      }
    }
  }
}
```