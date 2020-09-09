# Validating IAM policy grammar<a name="access_policies_policy-validator"></a>

A [policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/policies_overview.html) is a JSON document that uses the [IAM policy grammar](https://docs.aws.amazon.com/IAM/latest/UserGuide/policies-grammar.html)\. When you attach a policy to an IAM entity, such as a user, group, or role, it grants permissions to that entity\.

When you create or edit IAM access control policies using the AWS Management Console, Policy Validator automatically examines them to ensure that they comply with the IAM policy grammar\. If Policy Validator determines that a policy is not in compliance with the grammar, it prompts you to fix the policy\.

**Validation Scope**  
Policy Validator only checks JSON policy syntax and grammar\. It does not verify that your ARNs, action names, or condition keys are correct\.

**Accessing Policy Validator**  
Policy Validator runs automatically when you do the following using the IAM console:
+ **Create a JSON policy** – When you create a new JSON policy, Policy Validator runs automatically when you choose **Review policy**\. If the policy is not valid, you receive a notification and must fix the problem before you can continue\.
+ **Edit a JSON policy** – When you edit an existing JSON policy, Policy Validator runs automatically when you choose **Review policy**\. If the policy is not valid, you receive a notification and must fix the problem before you can continue\.

**Existing Policies**  
You might have existing policies that are not valid because they were created or last saved before the introduction of Policy Validator\. You cannot edit and save an existing policy without fixing any policy syntax errors\.