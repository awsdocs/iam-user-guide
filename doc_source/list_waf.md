# Actions and Condition Context Keys for AWS WAF<a name="list_waf"></a>

AWS WAF \(service prefix: waf\) provides the following service\-specific actions and condition context keys for use in IAM policies\.

**Actions for AWS WAF**

For information about using the following AWS WAF API actions in an IAM policy, see [Using IAM to Control Access to AWS WAF Resources](http://docs.aws.amazon.com/waf/latest/developerguide/waf-iam.html) in the *AWS WAF Developer Guide*\.
+ `[waf:CreateByteMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateByteMatchSet.html)`
+ `[waf:CreateGeoMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateGeoMatchSet.html)`
+ `[waf:CreateIPSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateIPSet.html)`
+ `[waf:CreateRateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateRateBasedRule.html)`
+ `[waf:CreateRegexMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateRegexMatchSet.html)`
+ `[waf:CreateRegexPatternSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateRegexPatternSet.html)`
+ `[waf:CreateRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateRule.html)`
+ `[waf:CreateSizeConstraintSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateSizeConstraintSet.html)`
+ `[waf:CreateSqlInjectionMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateSqlInjectionMatchSet.html)`
+ `[waf:CreateWebACL](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateWebACL.html)`
+ `[waf:CreateXssMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_CreateXssMatchSet.html)`
+ `[waf:DeleteByteMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteByteMatchSet.html)`
+ `[waf:DeleteGeoMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteGeoMatchSet.html)`
+ `[waf:DeleteIPSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteIPSet.html)`
+ `[waf:DeleteRateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteRateBasedRule.html)`
+ `[waf:DeleteRegexMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteRegexMatchSet.html)`
+ `[waf:DeleteRegexPatternSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteRegexPatternSet.html)`
+ `[waf:DeleteRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteRule.html)`
+ `[waf:DeleteSizeConstraintSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteSizeConstraintSet.html)`
+ `[waf:DeleteSqlInjectionMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteSqlInjectionMatchSet.html)`
+ `[waf:DeleteWebACL](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteWebACL.html)`
+ `[waf:DeleteXssMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_DeleteXssMatchSet.html)`
+ `[waf:GetByteMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetByteMatchSet.html)`
+ `[waf:GetChangeToken](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetChangeToken.html)`
+ `[waf:GetChangeTokenStatus](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetChangeTokenStatus.html)`
+ `[waf:GetGeoMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetGeoMatchSet.html)`
+ `[waf:GetIPSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetIPSet.html)`
+ `[waf:GetRateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetRateBasedRule.html)`
+ `[waf:GetRateBasedRuleManagedKeys](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetRateBasedRuleManagedKeys.html)`
+ `[waf:GetRegexMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetRegexMatchSet.html)`
+ `[waf:GetRegexPatternSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetRegexPatternSet.html)`
+ `[waf:GetRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetRule.html)`
+ `[waf:GetSampledRequests](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetSampledRequests.html)`
+ `[waf:GetSizeConstraintSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetSizeConstraintSet.html)`
+ `[waf:GetSqlInjectionMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetSqlInjectionMatchSet.html)`
+ `[waf:GetWebACL](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetWebACL.html)`
+ `[waf:GetXssMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_GetXssMatchSet.html)`
+ `[waf:ListByteMatchSets](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListByteMatchSets.html)`
+ `[waf:ListGeoMatchSets](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListGeoMatchSets.html)`
+ `[waf:ListIPSets](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListIPSets.html)`
+ `[waf:ListRateBasedRules](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListRateBasedRules.html)`
+ `[waf:ListRegexMatchSets](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListRegexMatchSets.html)`
+ `[waf:ListRegexPatternSets](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListRegexPatternSets.html)`
+ `[waf:ListRules](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListRules.html)`
+ `[waf:ListSizeConstraintSets](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListSizeConstraintSets.html)`
+ `[waf:ListSqlInjectionMatchSets](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListSqlInjectionMatchSets.html)`
+ `[waf:ListWebACLs](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListWebACLs.html)`
+ `[waf:ListXssMatchSets](http://docs.aws.amazon.com/waf/latest/APIReference/API_ListXssMatchSets.html)`
+ `[waf:UpdateByteMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateByteMatchSet.html)`
+ `[waf:UpdateGeoMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateGeoMatchSet.html)`
+ `[waf:UpdateIPSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateIPSet.html)`
+ `[waf:UpdateRateBasedRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateRateBasedRule.html)`
+ `[waf:UpdateRegexMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateRegexMatchSet.html)`
+ `[waf:UpdateRegexPatternSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateRegexPatternSet.html)`
+ `[waf:UpdateRule](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateRule.html)`
+ `[waf:UpdateSizeConstraintSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateSizeConstraintSet.html)`
+ `[waf:UpdateSqlInjectionMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateSqlInjectionMatchSet.html)`
+ `[waf:UpdateWebACL](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateWebACL.html)`
+ `[waf:UpdateXssMatchSet](http://docs.aws.amazon.com/waf/latest/APIReference/API_UpdateXssMatchSet.html)`

**Condition context keys for AWS WAF**

AWS WAF has no service\-specific context keys that can be used in an IAM policy\. For the list of the global condition context keys that are available to all services, see [Available Global Condition Keys](reference_policies_condition-keys.md#AvailableKeys) in the *IAM Policy Elements Reference*\.