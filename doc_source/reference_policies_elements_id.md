# IAM JSON policy elements: Id<a name="reference_policies_elements_id"></a>

The `Id` element specifies an optional identifier for the policy\. The ID is used differently in different services\.

For services that let you set an `ID` element, we recommend you use a UUID \(GUID\) for the value, or incorporate a UUID as part of the ID to ensure uniqueness\. 

```
"Id": "cd3ad3d9-2776-4ef1-a904-4c229d1642ee"
```

**Note**  
Some AWS services \(for example, Amazon SQS or Amazon SNS\) might require this element and have uniqueness requirements for it\. For service\-specific information about writing policies, refer to the documentation for the service you're working with\.