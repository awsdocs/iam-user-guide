# IAM JSON Policy Elements: Version<a name="reference_policies_elements_version"></a>

**Disambiguation Note**  
This topic is about the JSON policy element named "Version"\. The `Version` policy element is different from a *policy version*\. The `Version` policy element is used within a policy and defines the version of the policy language\. A policy version, on the other hand, is created when you make changes to a customer managed policy in IAM\. The changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new version of the managed policy\. If you were searching for information about the multiple version support available for managed policies, see [Versioning IAM Policies](access_policies_managed-versioning.md)\.

The `Version` elements specifies the language syntax rules that are to be used to process this policy\. If you include features that are not available in the specified version, then your policy will generate errors or not work the way you intend\. As a general rule, you should specify the most recent version available, unless you depend on a feature that was deprecated in later versions\.

The `Version` element must appear before the `Statement` element\. The only allowed values are these:
+ `2012-10-17`\. This is the current version of the policy language, and you should use this version number for all policies\.
+ `2008-10-17`\. This was an earlier version of the policy language\. You might see this version on existing policies\. Do not use this version for any new policies or any existing policies that you are updating\. 

If you do not include a `Version` element, the value defaults to `2008-10-17`\. However, it is a good practice to always include a `Version` element and set it to `2012-10-17`\.

**Note**  
If your policy uses any features that were introduced in a later version, such as [policy variables](reference_policies_variables.md), you *must* include a `Version` element and set it to `2012-10-17`\. If you don't include a `Version` element set to `2012-10-17`, variables such as `${aws:username}` aren't recognized as variables and are instead treated as literal strings in the policy\.

```
"Version": "2012-10-17"
```