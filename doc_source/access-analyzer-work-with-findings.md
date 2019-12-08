# Working with Findings<a name="access-analyzer-work-with-findings"></a>

Findings are generated only once for each instance of a resource that is shared outside of your zone of trust\. Each time a resource\-based policy is modified, Access Analyzer analyzes the policy\. If the updated policy shares a resource that is already identified in a finding, but with different permissions or conditions, a new finding is generated for that instance of the resource sharing\. If the access in the first finding is removed, that finding is updated to a status of Resolved\.

The status of all findings remains Active until you archive them or remove the access that generated the finding\. When you remove the access, the finding status is updated to Resolved\.

**Note**  
It may take up to 30 minutes after a policy is modified for Access Analyzer to analyze the resource and then update the finding\.

You should review all of the findings in your account to determine whether the sharing is expected and approved\. If the sharing identified in the finding is expected, you can archive the finding\. When you archive a finding, the status is changed to Archived, and the finding is removed from the Active findings list\. The finding is not deleted\. You can view your archived findings at any time\. Work through all of the findings in your account until you have zero active findings\. After you get to zero findings, you know that any new Active findings that are generated are from a recent change in your environment\.