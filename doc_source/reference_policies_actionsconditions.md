# AWS Service Actions and Condition Context Keys for Use in IAM Policies<a name="reference_policies_actionsconditions"></a>

Each AWS service can provide actions and condition context keys for use in IAM policies\. Not all API actions defined by a service can be used in an IAM policy, and a service might define some permissions that don't directly correspond to an API action\. Use this list to determine which actions can be used as permissions in an IAM policy\.

+ Use actions found in these lists in the `Action` element of an IAM policy to allow or deny what a user can do within a service\. For more information about the `Action` element, see [Action](http://docs.aws.amazon.com/IAM/latest/UserGuide/AccessPolicyLanguage_ElementDescriptions.html#Action) in the [IAM Policy Element Reference](http://docs.aws.amazon.com/IAM/latest/UserGuide/AccessPolicyLanguage_ElementDescriptions.html)\.

+ Use the context keys in these lists in the `Condition` element of an IAM policy to allow or deny access only when specified values are present\. For more information about the `Condition` element, see [IAM JSON Policy Elements: Condition](reference_policies_elements_condition.md)\.

+ For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys)\.

AWS services with actions and/or condition context keys: