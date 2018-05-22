# Sample Policies with MFA Conditions<a name="id_credentials_mfa_sample-policies"></a>

The following examples show additional ways that MFA conditions can be added to policies\. To learn how to create an IAM policy using these example JSON policy documents, see [Create a Policy on the JSON Tab](access_policies_create.md#access_policies_create-json-editor)\.

**Note**  
The following examples show policies attached directly to an IAM user or group in your own AWS account\. To adapt the example to MFA\-protect API operations across accounts, you use IAM roles instead and put the MFA condition check in the role trust policy, not in the role access policy\. For more information, see [Scenario: MFA Protection for Cross\-Account Delegation](id_credentials_mfa_configure-api-require.md#MFAProtectedAPI-cross-account-delegation)\. 

**Topics**
+ [Example 1: Granting Access After Recent MFA Authentication \(GetSessionToken\)](#ExampleMFAforIAMUserAge)
+ [Example 2: Denying Access to Specific API Operations Without Valid MFA Authentication \(GetSessionToken\)](#ExampleMFAforResource)
+ [Example 3: Denying Access to Specific API Operations Without *Recent* Valid MFA Authentication \(GetSessionToken\)](#ExampleMFADenyNotRecent)

## Example 1: Granting Access After Recent MFA Authentication \(GetSessionToken\)<a name="ExampleMFAforIAMUserAge"></a>

The following example shows a policy attached to a user or group that grants Amazon EC2 access only if the user was authenticated with MFA within the last hour \(3600 seconds\)\. Note that if a user with long\-term credentials and this policy calls the Amazon EC2 API, then the call fails because the `MultiFactorAuthAge` key is never present in the request context for long\-term credentials\. You can either allow long\-term credentials by changing the operator to `NumericLessThanIfExists`, or you can require that the user get short\-term credentials validated with an MFA using the `sts:GetSessionToken` API first\.

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": ["ec2:*"],
    "Resource": ["*"],
    "Condition": {"NumericLessThan": {"aws:MultiFactorAuthAge": "3600"}}
  }]
}
```

## Example 2: Denying Access to Specific API Operations Without Valid MFA Authentication \(GetSessionToken\)<a name="ExampleMFAforResource"></a>

The following example shows a policy attached to a user or group that grants access to the entire Amazon EC2 API, but denies access to `StopInstances` and `TerminateInstances` if the user is not authenticated with MFA\. The policy requires two statements to achieve the intended effect\. The first statement \(containing` "Sid": "AllowAllActionsForEC2"`\) allows all Amazon EC2 actions\. The second statement \(containing `"Sid": "DenyStopAndTerminateWhenMFAIsNotPresent"`\) denies the `StopInstances` and `TerminateInstances` actions when the MFA authentication context is missing \(meaning MFA was not used\)\.

**Note**  
The condition check for `MultiFactorAuthPresent` in the Deny statement should not be a `{"Bool":{"aws:MultiFactorAuthPresent":false}}` because that key is not present and cannot be evaluated when MFA is not used\. So instead, use the `BoolIfExists` check to see if the key is present before checking the value\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowAllActionsForEC2",
      "Effect": "Allow",
      "Action": "ec2:*",
      "Resource": "*"
    },
    {
      "Sid": "DenyStopAndTerminateWhenMFAIsNotPresent",
      "Effect": "Deny",
      "Action": [
        "ec2:StopInstances",
        "ec2:TerminateInstances"
      ],
      "Resource": "*",
      "Condition": {"BoolIfExists": {"aws:MultiFactorAuthPresent": false}}
    }
  ]
}
```

## Example 3: Denying Access to Specific API Operations Without *Recent* Valid MFA Authentication \(GetSessionToken\)<a name="ExampleMFADenyNotRecent"></a>

The following example shows a policy attached to a user or group that grants access to the entire Amazon EC2 API, but denies access to `StopInstances` and `TerminateInstances` unless the user authenticated with MFA within the last hour\. This example expands on the previous example and requires three statements to achieve the intended effect\. The first two statements are the same as the previous example\. The second statement still contains the condition that denies `StopInstances` and `TerminateInstances` if MFA isn't used at all \(the MFA context is missing\)\. The third statement in the following example \(containing `"Sid": "DenyStopAndTerminateWhenMFAIsOlderThanOneHour"`\) contains an additional condition that denies the `StopInstances` and `TerminateInstances` actions when MFA authentication is present but occurred more than one hour prior to the request\. For example, an IAM user might sign\-in to the AWS Management Console with MFA and then attempt to stop or terminate an EC2 instance two hours later\. The following policy prevents this\. To stop or terminate an EC2 instance in this scenario, the user must sign out, sign in again with MFA, and then stop or terminate the instance within one hour of signing in\. 

**Note**  
The condition check for `MultiFactorAuthPresent` in the first Deny statement uses `"BoolIfExists"`, because that key is not present and cannot be evaluated when MFA is not used\. If MFA is not used and the value does not exist, it returns true and the statement matches and denies access\.  
The condition `aws:MultiFactorAuthAge` is only present when MFA context is present in the request\. So statement 2 covers the case when MFA is not present at all, and statement 3 covers the case when MFA is present and evaluates whether it occurred in the proper time window\. Again, when the key is not present, the \.\.\.IfExists causes the test to return true, the statement matches, and the user is denied access to those API operations\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowAllActionsForEC2",
      "Effect": "Allow",
      "Action": "ec2:*",
      "Resource": "*"
    },
    {
      "Sid": "DenyStopAndTerminateWhenMFAIsNotPresent",
      "Effect": "Deny",
      "Action": [
        "ec2:StopInstances",
        "ec2:TerminateInstances"
      ],
      "Resource": "*",
      "Condition": {"BoolIfExists": {"aws:MultiFactorAuthPresent": false}}
    },
    {
      "Sid": "DenyStopAndTerminateWhenMFAIsOlderThanOneHour",
      "Effect": "Deny",
      "Action": [
        "ec2:StopInstances",
        "ec2:TerminateInstances"
      ],
      "Resource": "*",
      "Condition": {"NumericGreaterThanIfExists": {"aws:MultiFactorAuthAge": "3600"}}
    }
  ]
}
```