# IAM JSON policy elements: Effect<a name="reference_policies_elements_effect"></a>

The `Effect` element is required and specifies whether the statement results in an allow or an explicit deny\. Valid values for `Effect` are `Allow` and `Deny`\. 

```
"Effect":"Allow"
```

By default, access to resources is denied\. To allow access to a resource, you must set the `Effect` element to `Allow`\. To override an allow \(for example, to override an allow that is otherwise in force\), you set the `Effect` element to `Deny`\. For more information, see [Policy evaluation logic](reference_policies_evaluation-logic.md)\.