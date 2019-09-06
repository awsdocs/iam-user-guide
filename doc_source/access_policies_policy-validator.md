# Validating JSON Policies<a name="access_policies_policy-validator"></a>

Policy Validator automatically examines your new and existing IAM access control policies to ensure that they comply with the IAM policy grammar\. A [policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/policies_overview.html) is a JSON document written using the [IAM policy grammar](https://docs.aws.amazon.com/IAM/latest/UserGuide/policies-grammar.html)\. It defines access permissions for the AWS user, group, or role that you attach the policy to\. If Policy Validator determines that a policy is not in compliance with the grammar, it prompts you to fix the policy\. Policy Validator is only available if you have non\-compliant policies\.

You can use the following methods to access Policy Validator: 

1. **Creating JSON policies** – When you create a new JSON policy, Policy Validator runs automatically when you choose **Review policy**\. If the policy is not valid, you receive a notification and must fix the problem before you can continue\.

1. **Editing JSON policies** – When you edit an existing JSON policy, Policy Validator runs automatically when you choose **Review policy**\. If the policy is not valid, you receive a notification and must fix the problem before you can continue\. Existing policies with errors that were set up before the introduction of Policy Validator will continue to function\. However, you cannot edit and save them without fixing the policy syntax errors\.

**Note**  
Policy Validator only checks JSON policy syntax and grammar\. It does not validate that your ARNs, action names, or condition keys are correct\.