# IAM JSON Policy Elements: Version<a name="reference_policies_elements_version"></a>

**Disambiguation Note**  
This topic is about the JSON policy element named "Version"\. The `Version` policy element is different from a *policy version*\. The `Version` policy element is used within a policy and defines the version of the policy language\. A policy version, on the other hand, is created when you make changes to a customer managed policy in IAM\. The changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new version of the managed policy\. If you were searching for information about the multiple version support available for managed policies, see [Versioning IAM Policies](access_policies_managed-versioning.md)\.

The `Version` elements specifies the language syntax rules that are to be used to process this policy\. If you include features that are not available in the specified version, then your policy will generate errors or not work the way you intend\. As a general rule, you should specify the most recent version available, unless you depend on a feature that was deprecated in later versions\.

The `Version` element must appear before the `Statement` element\. The only allowed values are these:
+ `2012-10-17`\. This is the current version of the policy language\. This version added [policy variables](reference_policies_variables.md).
+ `2008-10-17`\. You might see this version on old policies\. It was replaced by version `2012-10-17` (which is fully backwards compatible)\.

If you do not include a `Version` element, the value defaults to `2008-10-17`\. However, it is a good practice to always include a `Version` element and set it to `2012-10-17`\. If your policy uses any features that were introduced in a later version, you *must* include a `Version` element and set it appropriately\.

```
"Version": "2012-10-17"
```
