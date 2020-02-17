# Archive Rules<a name="access-analyzer-archive-rules"></a>

Archive rules automatically archive new findings that meet the criteria you define when you create the rule\. For example, you can create an archive rule to automatically archive any findings for a specific S3 bucket that you regularly grant access to\. Or if you grant access to multiple resources to a specific principal, you can create a rule that automatically archives any new finding generated for access granted to that principal\. This lets you focus only on active findings that may indicate a security risk\.

Use the information provided in the finding details to identify the specific resource and external entity to use when creating or editing a rule\. When you create an archive rule, only new findings that match the rule criteria are automatically archived\. Existing findings are not automatically archived\. When you create a rule, you can include up to 20 values per criterion in the rule\.

**Note**  
When you create or edit an archive rule, Access Analyzer does not validate the values you include in the filter for the rule\. For example, if you add a rule to match an AWS Account, Access Analyzer accepts any value in the field, even if it is not a valid AWS account number\.

**To create an archive rule**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. Choose **Access analyzer**, then choose **Archive rules**\.

1. Choose **Create archive rule**\.

1. Enter a name for the rule if you want to change the default name\.

1. In the **Rule** section, under **Criteria**, select a property to match for the rule\.

1. Choose an operator for the property value, such as **contains**\.

   The operators available depend on the property you choose\.

1. Optionally, add additional values for the property, or add additional criteria for the rule\.

   To add another value for a criterion, choose **Add another value**\. To add another criterion for the rule, choose the **Add** button\.

1. When finished added criteria and values, choose **Create archive rule**\.

For example, to create a rule that automatically archives any findings for S3 buckets: choose **Resource type**, and then choose **is** for the operator\. Next choose **S3 bucket** from the **Select resource type** list, and then choose **Add**\.

Continue to define criteria to customize the rule as appropriate for your environment, and then choose **Create archive rule**\.

If you are create a new rule and add multiple criteria, you can remove a single criterion from the rule by choosing **Remove this criterion**\. You can remove a value added for a criterion by choosing **Remove value**\.

**To edit an archive rule**

1. Choose name of the rule to edit in the **Name**\.

   You can edit only one archive rule at a time\.

1. Add new or remove the existing criteria and values for each criterion\.

1. Choose **Save changes**\.

**To delete an archive rule**

1. Select the check box for the rules to delete\.

   You can delete one, many, or all rules at the same time\.

1. Choose **Delete**\.

1. Type **delete** in the **Delete archive rule** confirmation dialog, and then choose **Delete**\.

The rules are deleted only from the analyzer in the current Region\. You must delete archive rules separately for each analyzer that you created in other Regions\.