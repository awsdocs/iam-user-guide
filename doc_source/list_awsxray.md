# Actions, Resources, and Condition Keys for AWS XRay<a name="list_awsxray"></a>

AWS XRay \(service prefix: `xray`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/xray/latest/devguide/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/xray/latest/api/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/xray/latest/devguide/xray-permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS XRay](#awsxray-actions-as-permissions)
+ [Resources Defined by XRay](#awsxray-resources-for-iam-policies)
+ [Condition Keys for AWS XRay](#awsxray-policy-keys)

## Actions Defined by AWS XRay<a name="awsxray-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
| [http://docs.aws.amazon.com/xray/latest/api/API_BatchGetTraces.html](http://docs.aws.amazon.com/xray/latest/api/API_BatchGetTraces.html) | Retrieves a list of traces specified by ID\. Each trace is a collection of segment documents that originates from a single request\. Use GetTraceSummaries to get a list of trace IDs\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/xray/latest/api/API_GetServiceGraph.html](http://docs.aws.amazon.com/xray/latest/api/API_GetServiceGraph.html) | Retrieves a document that describes services that process incoming requests, and downstream services that they call as a result\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/xray/latest/api/API_GetTraceGraph.html](http://docs.aws.amazon.com/xray/latest/api/API_GetTraceGraph.html) | Retrieves a service graph for one or more specific trace IDs\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/xray/latest/api/API_GetTraceSummaries.html](http://docs.aws.amazon.com/xray/latest/api/API_GetTraceSummaries.html) | Retrieves IDs and metadata for traces available for a specified time frame using an optional filter\. To get the full traces, pass the trace IDs to BatchGetTraces\. | Read |  |  |  | 
| [http://docs.aws.amazon.com/xray/latest/api/API_PutTelemetryRecords.html](http://docs.aws.amazon.com/xray/latest/api/API_PutTelemetryRecords.html) | Used by the AWS X\-Ray daemon to send telemetry to the service\. | Write |  |  |  | 
| [http://docs.aws.amazon.com/xray/latest/api/API_PutTraceSegments.html](http://docs.aws.amazon.com/xray/latest/api/API_PutTraceSegments.html) | Uploads segment documents to AWS X\-Ray\. The X\-Ray SDK generates segment documents and sends them to the X\-Ray daemon, which uploads them in batches\. | Write |  |  |  | 

## Resources Defined by XRay<a name="awsxray-resources-for-iam-policies"></a>

XRay has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS XRay<a name="awsxray-policy-keys"></a>

XRay has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.