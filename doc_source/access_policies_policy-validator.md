# Validating IAM policies<a name="access_policies_policy-validator"></a>

A [policy](https://docs.aws.amazon.com/IAM/latest/UserGuide/policies_overview.html) is a JSON document that uses the [IAM policy grammar](https://docs.aws.amazon.com/IAM/latest/UserGuide/policies-grammar.html)\. When you attach a policy to an IAM entity, such as a user, group, or role, it grants permissions to that entity\.

When you create or edit IAM access control policies using the AWS Management Console, AWS automatically examines them to ensure that they comply with the IAM policy grammar\. If AWS determines that a policy is not in compliance with the grammar, it prompts you to fix the policy\.

IAM Access Analyzer provides additional policy checks with recommendations to help you further refine the policy\. To learn more about IAM Access Analyzer policy checks and actionable recommendations, see [ IAM Access Analyzer policy validation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-validation.html)\. To view a list of warnings, errors, and suggestions that are returned by IAM Access Analyzer, see [ IAM Access Analyzer policy check reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-reference-policy-checks.html)\.

**Validation scope**  
AWS checks JSON policy syntax and grammar\. It also verifies that your ARNs are formatted properly and action names and condition keys are correct\.

**Accessing policy validation**  
Policies are validated automatically when you create a JSON policy or edit an existing policy in the AWS Management Console\. If the policy syntax is not valid, you receive a notification and must fix the problem before you can continue\. The findings from the IAM Access Analyzer policy validation are automatically returned in the AWS Management Console if you have permissions for `access-analyzer:ValidatePolicy`\. You can also validate policies using the AWS API or AWS CLI\.

**Existing policies**  
You might have existing policies that are not valid because they were created or last saved before the latest updates to the policy engine\. As a best practice, we recommend that you open your existing policies and review the policy validation results that are generated\. You cannot edit and save existing policies without fixing any policy syntax errors\.