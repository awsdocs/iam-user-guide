# IAM JSON policy elements: Version<a name="reference_policies_elements_version"></a>

**Disambiguation note**  
This `Version` JSON policy element is different from a *policy version*\. The `Version` policy element is used within a policy and defines the version of the policy language\. A policy version, on the other hand, is created when you make changes to a customer managed policy in IAM\. The changed policy doesn't overwrite the existing policy\. Instead, IAM creates a new version of the managed policy\. If you were searching for information about the multiple version support available for managed policies, see [Versioning IAM policies](access_policies_managed-versioning.md)\.

The `Version` policy element specifies the language syntax rules that are to be used to process a policy\. To use all of the available policy features, include the following `Version` element before the `Statement` element in all of your policies\.

```
"Version": "2012-10-17"
```

IAM supports the following `Version` element values:
+ `2012-10-17`\. This is the current version of the policy language, and you should always include a `Version` element and set it to `2012-10-17`\. Otherwise, you cannot use features such as [policy variables](reference_policies_variables.md) that were introduced with this version\.
+ `2008-10-17`\. This was an earlier version of the policy language\. You might see this version on older existing policies\. Do not use this version for any new policies or when you update any existing policies\. 

If you do not include a `Version` element, the value defaults to `2008-10-17`, but newer features, such as policy variables, will not work with your policy\. For example, variables such as `${aws:username}` aren't recognized as variables and are instead treated as literal strings in the policy\.