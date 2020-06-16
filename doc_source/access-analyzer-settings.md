# Settings<a name="access-analyzer-settings"></a>

If you're configuring AWS IAM Access Analyzer in your AWS Organizations master account, you can add a member account in the organization as the delegated administrator to manage Access Analyzer for your organization\. The delegated administrator has permissions to create and manage analyzers with the organization as the zone of trust\. Only the master account can add a delegated administrator\.

## Delegated Administrator for Access Analyzer<a name="access-analyzer-delegated-administrator"></a>

The delegated administrator for Access Analyzer is a member account within the organization that has permissions to create and manage analyzers with the organization as the zone of trust\. Only the master account can add, remove, or change a delegated administrator\.

If you add a delegated administrator, you can later change to a different account for the delegated administrator\. When you do, the former delegated administrator account loses permission to all analyzers with organization as the zone of trust that were created using that account\. These analyzers move to a disabled state and no longer generate new or update existing findings\. The existing findings for these analyzers are also no longer accessible\. You can access them again in the future by configuring the account as the delegated administrator\. If you know that you won't use the same account as a delegated administrator, consider deleting the analyzers before changing the delegated administrator\. This deletes all findings generated\. When the new delegated administrator creates new analyzers, new instances of the same findings are generated\. You don't lose any findings, they just get generated for the new analyzer in a different account\. And you can continue to access findings for the organization using the organization master account, which also has administrator permissions\. The new delegated administrator must create new analyzers for Access Analyzer to start monitoring resources in your organization\.

If the delegated administrator leaves the AWS organization, the delegated administration privileges are removed from the account\. All analyzers in the account with the organization as the zone of trust move to a disabled state\. The existing findings for these analyzers are also no longer accessible\.

The first time that you configure analyzers in the master account, you can choose the option to **Add delegated administrator** that is displayed on the Access Analyzer homepage in the IAM console\.

**To add a delegated administrator \(console\)**

1. Log in to the AWS console using the master account for your organization\.

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Under **Access Analyzer**, choose **Settings**\.

1. Choose **Add delegated administrator**\.

1. Enter the account number of an organization member account to make the delegated administrator\.

   The account must be a member of your organization\.

1. Choose **Save changes**\.

**To add a delegated administrator \(AWS CLI, AWS API\)**

When you create an analyzer with organization as the zone of trust in a delegated administrator account using the AWS CLI, AWS API \(using the AWS SDKs\) or AWS CloudFormation, you must use AWS Organizations APIs to enable service access for Access Analyzer and register the member account as a delegated administrator\.

1. Enable trusted service access for Access Analyzer in AWS Organizations\. See [How to Enable or Disable Trusted Access](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_integrate_services.html) in the AWS Organizations User Guide\.

1. Register a valid member account of your AWS organization as a delegated administrator using the AWS Organizations [https://docs.aws.amazon.com/organizations/latest/APIReference/API_RegisterDelegatedAdministrator.html](https://docs.aws.amazon.com/organizations/latest/APIReference/API_RegisterDelegatedAdministrator.html) API operation or the `register-delegated-administrator` AWS CLI command\.

After you change the delegated administrator, the new administrator must create analyzers to start monitoring access to the resources in your organization\.