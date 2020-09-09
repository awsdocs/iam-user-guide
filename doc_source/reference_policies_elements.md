# IAM JSON policy elements reference<a name="reference_policies_elements"></a>

JSON policy documents are made up of elements\. The elements are listed here in the general order you use them in a policy\. The order of the elements doesn't matter—for example, the `Resource` element can come before the `Action` element\. You're not required to specify any `Condition` elements in the policy\. To learn more about the general structure and purpose of a JSON policy document, see [Overview of JSON policies](access_policies.md#access_policies-json)\.

Some JSON policy elements are mutually exclusive\. This means that you cannot create a policy that uses both\. For example, you cannot use both `Action` and `NotAction` in the same policy statement\. Other pairs that are mutually exclusive include `Principal`/`NotPrincipal` and `Resource`/`NotResource`\. 

The details of what goes into a policy vary for each service, depending on what actions the service makes available, what types of resources it contains, and so on\. When you're writing policies for a specific service, it's helpful to see examples of policies for that service\. For a list of all the services that support IAM, and for links to the documentation in those services that discusses IAM and policies, see [AWS services that work with IAM](reference_aws-services-that-work-with-iam.md)\.

**Topics**
+ [Version](reference_policies_elements_version.md)
+ [Id](reference_policies_elements_id.md)
+ [Statement](reference_policies_elements_statement.md)
+ [Sid](reference_policies_elements_sid.md)
+ [Effect](reference_policies_elements_effect.md)
+ [Principal](reference_policies_elements_principal.md)
+ [NotPrincipal](reference_policies_elements_notprincipal.md)
+ [Action](reference_policies_elements_action.md)
+ [NotAction](reference_policies_elements_notaction.md)
+ [Resource](reference_policies_elements_resource.md)
+ [NotResource](reference_policies_elements_notresource.md)
+ [Condition](reference_policies_elements_condition.md)
+ [Variables and tags](reference_policies_variables.md)
+ [Supported data types](reference_policies_elements_datatypes.md)