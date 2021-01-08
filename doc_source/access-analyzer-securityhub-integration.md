# Integration with AWS Security Hub<a name="access-analyzer-securityhub-integration"></a>

[AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html) provides you with a comprehensive view of your security state in AWS and helps you to check your environment against security industry standards and best practices\. Security Hub collects security data from across AWS accounts, services, and supported third\-party partner products and helps you to analyze your security trends and identify the highest priority security issues\.

The IAM Access Analyzer integration with Security Hub enables you to send findings from Access Analyzer to Security Hub\. Security Hub can then include those findings in its analysis of your security posture\.

**Contents**
+ [How Access Analyzer sends findings to Security Hub](#access-analyzer-securityhub-integration-sending-findings)
  + [Types of findings that Access Analyzer sends](#access-analyzer-securityhub-integration-finding-types)
  + [Latency for sending findings](#access-analyzer-securityhub-integration-finding-latency)
  + [Retrying when Security Hub is not available](#access-analyzer-securityhub-integration-retry-send)
  + [Updating existing findings in Security Hub](#access-analyzer-securityhub-integration-finding-updates)
+ [Viewing Access Analyzer findings in Security Hub](#access-analyzer-securityhub-integration-viewing-findings)
  + [Interpreting Access Analyzer finding names in Security Hub](#access-analyzer-securityhub-integration-intrepreting-finding-names)
+ [Typical finding from Access Analyzer](#access-analyzer-securityhub-integration-finding-example)
+ [Enabling and configuring the integration](#access-analyzer-securityhub-integration-enable)
+ [How to stop sending findings](#access-analyzer-securityhub-integration-disable)

## How Access Analyzer sends findings to Security Hub<a name="access-analyzer-securityhub-integration-sending-findings"></a>

In Security Hub, security issues are tracked as findings\. Some findings come from issues that are detected by other AWS services or by third\-party partners\. Security Hub also has a set of rules that it uses to detect security issues and generate findings\.

Security Hub provides tools to manage findings from across all of these sources\. You can view and filter lists of findings and view details for a finding\. See [Viewing findings](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-findings-viewing.html) in the *AWS Security Hub User Guide*\. You can also track the status of an investigation into a finding\. See [Taking action on findings](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-findings-taking-action.html) in the *AWS Security Hub User Guide*\.

All findings in Security Hub use a standard JSON format called the AWS Security Finding Format \(ASFF\)\. The ASFF includes details about the source of the issue, the affected resources, and the current status of the finding\. See [AWS Security Finding Format \(ASFF\)](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-findings-format.html) in the *AWS Security Hub User Guide*\.

IAM Access Analyzer is one of the AWS services that sends findings to Security Hub\. Access Analyzer generates a finding when it detects a policy statement that allows an external principal access to a [supported resource](access-analyzer-resources.md) in your organization or account\. Access Analyzer groups all of its findings for a resource and sends a single finding to Security Hub\.

### Types of findings that Access Analyzer sends<a name="access-analyzer-securityhub-integration-finding-types"></a>

Access Analyzer sends the findings to Security Hub using the [AWS Security Finding Format \(ASFF\)](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-findings-format.html)\. In ASFF, the `Types` field provides the finding type\. Findings from Access Analyzer can have the following values for `Types`\.
+ Effects/Data Exposure/External Access Granted
+ Software and Configuration Checks/AWS Security Best Practices/External Access Granted

### Latency for sending findings<a name="access-analyzer-securityhub-integration-finding-latency"></a>

When Access Analyzer creates a new finding, it is usually sent to Security Hub within 30 minutes\. Rarely, and under certain conditions, Access Analyzer is not notified that a policy was added or updated\. For example, a change to Amazon S3 account\-level block public access settings can take up to 12 hours\. Also, if there is a delivery issue with AWS CloudTrail log delivery, the policy change does not trigger a rescan of the resource that was reported in the finding\. When this happens, Access Analyzer analyzes the new or updated policy during the next periodic scan, which is within 24 hours\.

### Retrying when Security Hub is not available<a name="access-analyzer-securityhub-integration-retry-send"></a>

If Security Hub is not available, Access Analyzer retries sending the findings on a periodic basis\.

### Updating existing findings in Security Hub<a name="access-analyzer-securityhub-integration-finding-updates"></a>

After it sends a finding to Security Hub, IAM Access Analyzer sends updates to reflect additional observations of the finding activity to Security Hub\. The updates are reflected within the same finding\.

The finding for a resource in Security Hub is active if at least one of the findings for the resource in Access Analyzer is active\. If all findings in Access Analyzer for a resource are archived or resolved, then the Security Hub finding is archived\.

The Security Hub finding is updated when you change the policy access between public and cross\-account access\. This update can include changes to the type, title, description, and severity of the finding\.

## Viewing Access Analyzer findings in Security Hub<a name="access-analyzer-securityhub-integration-viewing-findings"></a>

To view your Access Analyzer findings in Security Hub, choose **See findings** in the **AWS: IAM Access Analyzer** section of the summary page\. Alternatively, you can choose **Findings** from the navigation panel\. You can then filter the findings to display only IAM Access Analyzer findings by choosing the **Product name:** field with a value of **IAM Access Analyzer**\.

### Interpreting Access Analyzer finding names in Security Hub<a name="access-analyzer-securityhub-integration-intrepreting-finding-names"></a>

IAM Access Analyzer sends the findings to Security Hub using the AWS Security Finding Format \(ASFF\)\. In ASFF, the **Types** field provides the finding type\. ASFF types use a different naming scheme than IAM Access Analyzer\. The following table includes details about all of the ASFF types associated with IAM Access Analyzer findings as they appear in Security Hub\.


****  

| ASFF finding type | Security Hub finding title | Description | 
| --- | --- | --- | 
| Effects/Data Exposure/External Access Granted | <resource ARN> allows public access | A resource\-based policy attached to the resource allows public access on the resource to all external principals\. | 
| Software and Configuration Checks/AWS Security Best Practices/ External Access Granted | <resource ARN> allows cross\-account access | A resource\-based policy attached to the resource allows cross\-account access to external principals outside the zone of trust for the analyzer\. | 

## Typical finding from Access Analyzer<a name="access-analyzer-securityhub-integration-finding-example"></a>

Access Analyzer sends findings to Security Hub using the [AWS Security Finding Format \(ASFF\)](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-findings-format.html)\.

Here is an example of a typical finding from Access Analyzer\.

```
{
    "SchemaVersion": "2018-10-08",
    "Id": "arn:aws:access-analyzer:us-west-2:111122223333:analyzer/my-analyzer/arn:aws:s3:::my-bucket",
    "ProductArn": "arn:aws:securityhub:us-west-2::product/aws/access-analyzer",
    "GeneratorId": "aws/access-analyzer",
    "AwsAccountId": "111122223333",
    "Types": ["Software and Configuration Checks/AWS Security Best Practices/External Access Granted"],
    "CreatedAt": "2020-11-10T16:17:47Z",
    "UpdatedAt": "2020-11-10T16:43:49Z",
    "Severity": {
        "Product": 1,
        "Label": "LOW",
        "Normalized": 1
    },
    "Title": "AwsS3Bucket/arn:aws:s3:::my-bucket/ allows cross-account access",
    "Description": "AWS::S3::Bucket/arn:aws:s3:::my-bucket/ allows cross-account access from AWS 444455556666",
    "Remediation": {
        "Recommendation": {"Text": "If the access isn't intended, it indicates a potential security risk. Use the console for the resource to modify or remove the policy that grants the unintended access. You can use the Rescan button on the Finding details page in the Access Analyzer console to confirm whether the change removed the access. If the access is removed, the status changes to Resolved."}
    },
    "SourceUrl": "https://console.aws.amazon.com/access-analyzer/home?region=us-west-2#/findings/details/dad90d5d-63b4-6575-b0fa-ef9c556ge798",
    "Resources": [
        {
            "Type": "AwsS3Bucket",
            "Id": "arn:aws:s3:::my-bucket",
            "Details": {
                "Other": {
                    "External Principal Type": "AWS",
                    "Condition": "none",
                    "Action Granted": "s3:GetObject,s3:GetObjectVersion",
                    "External Principal": "444455556666"
                }
            }
        }
    ],
    "WorkflowState": "NEW",
    "Workflow": {"Status": "NEW"},
    "RecordState": "ACTIVE"
}
```

## Enabling and configuring the integration<a name="access-analyzer-securityhub-integration-enable"></a>

To use the integration with Security Hub, you must enable Security Hub\. For information on how to enable Security Hub, see [Setting up Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-settingup.html) in the *AWS Security Hub User Guide*\.

When you enable both Access Analyzer and Security Hub, the integration is enabled automatically\. Access Analyzer immediately begins to send findings to Security Hub\.

## How to stop sending findings<a name="access-analyzer-securityhub-integration-disable"></a>

To stop sending findings to Security Hub, you can use either the Security Hub console or the API\.

See [Disabling and enabling the flow of findings from an integration \(console\)](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-integrations-managing.html#securityhub-integration-findings-flow-console) or [Disabling the flow of findings from an integration \(Security Hub API, AWS CLI\)](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-integrations-managing.html#securityhub-integration-findings-flow-disable-api) in the *AWS Security Hub User Guide*\.