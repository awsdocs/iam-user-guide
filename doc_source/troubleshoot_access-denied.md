# Troubleshooting access denied error messages<a name="troubleshoot_access-denied"></a>

Access denied errors are displayed when AWS explicitly or implicitly denies an authorization request\. An explicit denial occurs when a policy contains a `Deny` statement for the specific AWS action\. An implicit denial occurs when there is no applicable `Deny` statement and also no applicable `Allow` statement\. Because an IAM principal is denied access by default, it must be explicitly allowed to perform an action\. Otherwise, access is implicitly denied\. For more information, see [The difference between explicit and implicit denies](reference_policies_evaluation-logic.md#AccessPolicyLanguage_Interplay)\.

Most access denied error messages are in the format `User user is not authorized to perform action on resource because context`\. In this example, *user* is the [ARN](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html#identifiers-arns) that is denied access, *action* is the service action that is being denied, and *resource* is the ARN of the resource on which the action is being performed\. The *context* field represents additional context about the policy type that explains why the access is denied\.

When access is explicitly denied due to a `Deny` statement in a policy, then AWS includes `with an explicit deny in a type policy` in the access denied error message\. When access is implicitly denied, then AWS includes `because no type policy allows the action action` in the access denied error message\. 

**Note**  
The only exception is when access is denied due to a Service Control Policy \(SCP\)\. The error message will always include `due to an explicit deny in a Service Control Policy`, even if it is an implicit denial\.

If multiple policies of the same policy type deny an authorization request, then AWS does not specify the number in the access denied error message\. If an authorization request is denied due to multiple policy types, AWS includes only one of those policy types in the error message\. 