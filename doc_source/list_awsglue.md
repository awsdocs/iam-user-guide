# Actions, Resources, and Condition Keys for AWS Glue<a name="list_awsglue"></a>

AWS Glue \(service prefix: `glue`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](https://docs.aws.amazon.com/glue/latest/dg/)\.
+ View a [list of the API operations available for this service](https://docs.aws.amazon.com/glue/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](https://docs.aws.amazon.com/glue/latest/dg/authentication-and-access-control.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Glue](#awsglue-actions-as-permissions)
+ [Resources Defined by AWS Glue](#awsglue-resources-for-iam-policies)
+ [Condition Keys for AWS Glue](#awsglue-policy-keys)

## Actions Defined by AWS Glue<a name="awsglue-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. Use policies to grant permissions to perform an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\.

The **Resource** column indicates whether each action supports resource\-level permissions\. If there is no value for this column, you must specify all resources \("\*"\) in the `Resource` element of your policy statement\. If the column includes a resource type, then you can specify an ARN of that type in a statement with that action\. Required resources are indicated in the table with an asterisk \(\*\)\. If you specify a resource\-level permission ARN in a statement using this action, then it must be of this type\. Some actions support multiple resource types\. If the resource type is optional \(not indicated as required\), then you can choose to use one but not the other\.

For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchCreatePartition ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchCreatePartition)  | Grants permission to create one or more partitions | Write |  |  |  | 
|   [ BatchDeleteConnection ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-BatchDeleteConnection)  | Grants permission to delete one or more connections | Write |  |  |  | 
|   [ BatchDeletePartition ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchDeletePartition)  | Grants permission to delete one or more partitions | Write |  |  |  | 
|   [ BatchDeleteTable ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-BatchDeleteTable)  | Grants permission to delete one or more tables | Write |  |  |  | 
|   [ BatchDeleteTableVersion ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-DeleteTableVersion)  | Grants permission to delete one or more versions of a table | Read |  |  |  | 
|   [ BatchGetCrawlers ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-BatchGetCrawlers)  | Grants permission to retrieve one or more crawlers | Read |  |  |  | 
|   [ BatchGetDevEndpoints ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-dev-endpoint.html#aws-glue-api-dev-endpoint-BatchGetDevEndpoints)  | Grants permission to retrieve one or more development endpoints | Read |  |  |  | 
|   [ BatchGetJobs ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-BatchGetJobs)  | Grants permission to retrieve one or more jobs | Read |  |  |  | 
|   [ BatchGetPartition ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchGetPartition)  | Grants permission to retrieve one or more partitions | Read |  |  |  | 
|   [ BatchGetTriggers ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-BatchGetTriggers)  | Grants permission to retrieve one or more triggers | Read |  |  |  | 
|   [ BatchGetWorkflows ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-BatchGetWorkflows)  | Grants permission to retrieve one or more workflows | Read |  |  |  | 
|   [ BatchStopJobRun ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-BatchStopStartJobRun)  | Grants permission to stop one or more job runs for a job | Write |  |  |  | 
|   [ CreateClassifier ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-CreateClassifier)  | Grants permission to create a classifier | Write |  |  |  | 
|   [ CreateConnection ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-CreateConnection)  | Grants permission to create a connection | Write |  |  |  | 
|   [ CreateCrawler ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-CreateCrawler)  | Grants permission to create a crawler | Write |  |  |  | 
|   [ CreateDatabase ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-CreateDatabase)  | Grants permission to create a database | Write |  |  |  | 
|   [ CreateDevEndpoint ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-dev-endpoint.html#aws-glue-api-dev-endpoint-CreateDevEndpoint)  | Grants permission to create a development endpoint | Write |  |  |  | 
|   [ CreateJob ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-CreateJob)  | Grants permission to create a job | Write |  |  |  | 
|   [ CreatePartition ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-CreatePartition)  | Grants permission to create a partition | Write |  |  |  | 
|   [ CreateScript ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-script-generation.html#aws-glue-api-etl-script-generation-CreateScript)  | Grants permission to create a script | Write |  |  |  | 
|   [ CreateSecurityConfiguration ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-CreateSecurityConfiguration)  | Grants permission to create a security configuration | Write |  |  |  | 
|   [ CreateTable ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-CreateTable)  | Grants permission to create a table | Write |  |  |  | 
|   [ CreateTrigger ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-CreateTrigger)  | Grants permission to create a trigger | Write |  |  |  | 
|   [ CreateUserDefinedFunction ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-CreateUserDefinedFunction)  | Grants permission to create a function definition | Write |  |  |  | 
|   [ CreateWorkflow ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-CreateWorkflow)  | Grants permission to create a workflow | Write |  |  |  | 
|   [ DeleteClassifier ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-DeleteClassifier)  | Grants permission to delete a classifier | Write |  |  |  | 
|   [ DeleteConnection ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-DeleteConnection)  | Grants permission to delete a connection | Write |  |  |  | 
|   [ DeleteCrawler ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-DeleteCrawler)  | Grants permission to delete a crawler | Write |  |  |  | 
|   [ DeleteDatabase ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-DeleteDatabase)  | Grants permission to delete a database | Write |  |  |  | 
|   [ DeleteDevEndpoint ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-dev-endpoint.html#aws-glue-api-dev-endpoint-DeleteDevEndpoint)  | Grants permission to delete a development endpoint | Write |  |  |  | 
|   [ DeleteJob ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-DeleteJob)  | Grants permission to delete a job | Write |  |  |  | 
|   [ DeletePartition ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-DeletePartition)  | Grants permission to delete a partition | Write |  |  |  | 
|   [ DeleteResourcePolicy ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-DeleteResourcePolicy)  | Grants permission to delete a resource policy | Write |   [ catalog\* ](#awsglue-catalog)   |  |  | 
|   [ DeleteSecurityConfiguration ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-DeleteSecurityConfiguration)  | Grants permission to delete a security configuration | Write |  |  |  | 
|   [ DeleteTable ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-DeleteTable)  | Grants permission to delete a table | Write |  |  |  | 
|   [ DeleteTableVersion ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-DeleteTableVersion)  | Grants permission to delete a version of a table | Read |  |  |  | 
|   [ DeleteTrigger ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-DeleteTrigger)  | Grants permission to delete a trigger | Write |  |  |  | 
|   [ DeleteUserDefinedFunction ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-DeleteUserDefinedFunction)  | Grants permission to delete a function definition | Write |  |  |  | 
|   [ DeleteWorkflow ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-DeleteWorkflow)  | Grants permission to delete a workflow | Write |  |  |  | 
|   [ GetCatalogImportStatus ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-migration.html#aws-glue-api-catalog-migration-GetCatalogImportStatus)  | Grants permission to retrieve the catalog import status | Read |  |  |  | 
|   [ GetClassifier ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-GetClassifier)  | Grants permission to retrieve a classifier | Read |  |  |  | 
|   [ GetClassifiers ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-GetClassifiers)  | Grants permission to list all classifiers | Read |  |  |  | 
|   [ GetConnection ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-GetConnection)  | Grants permission to retrieve a connection | Read |  |  |  | 
|   [ GetConnections ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-GetConnections)  | Grants permission to retrieve a list of connections | Read |  |  |  | 
|   [ GetCrawler ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawler)  | Grants permission to retrieve a crawler | Read |  |  |  | 
|   [ GetCrawlerMetrics ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawlerMetrics)  | Grants permission to retrieve metrics about crawlers | Read |  |  |  | 
|   [ GetCrawlers ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawlers)  | Grants permission to retrieve all crawlers | Read |  |  |  | 
|   [ GetDataCatalogEncryptionSettings ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-GetDataCatalogEncryptionSettings)  | Grants permission to retrieve catalog encryption settings | Read |  |  |  | 
|   [ GetDatabase ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-GetDatabase)  | Grants permission to retrieve a database | Read |  |  |  | 
|   [ GetDatabases ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-GetDatabases)  | Grants permission to retrieve all databases | Read |  |  |  | 
|   [ GetDataflowGraph ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-script-generation.html#aws-glue-api-etl-script-generation-GetDataflowGraph)  | Grants permission to transform a script into a directed acyclic graph \(DAG\) | Read |  |  |  | 
|   [ GetDevEndpoint ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-dev-endpoint.html#aws-glue-api-dev-endpoint-GetDevEndpoint)  | Grants permission to retrieve a development endpoint | Read |  |  |  | 
|   [ GetDevEndpoints ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-dev-endpoint.html#aws-glue-api-dev-endpoint-GetDevEndpoints)  | Grants permission to retrieve all development endpoints | Read |  |  |  | 
|   [ GetJob ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-GetJob)  | Grants permission to retrieve a job | Read |  |  |  | 
|   [ GetJobRun ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-GetJobRun)  | Grants permission to retrieve a job run | Read |  |  |  | 
|   [ GetJobRuns ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-GetJobRuns)  | Grants permission to retrieve all job runs of a job | Read |  |  |  | 
|   [ GetJobs ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-GetJobs)  | Grants permission to retrieve all current jobs | Read |  |  |  | 
|   [ GetMapping ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-script-generation.html#aws-glue-api-etl-script-generation-GetMapping)  | Grants permission to create a mapping | Write |  |  |  | 
|   [ GetPartition ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-GetPartition)  | Grants permission to retrieve a partition | Read |  |  |  | 
|   [ GetPartitions ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-GetPartitions)  | Grants permission to retrieve the partitions of a table | Read |  |  |  | 
|   [ GetPlan ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-script-generation.html#aws-glue-api-etl-script-generation-GetPlan)  | Grants permission to retrieve a mapping for a script | Read |  |  |  | 
|   [ GetResourcePolicy ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-GetResourcePolicy)  | Grants permission to retrieve a resource policy | Read |   [ catalog\* ](#awsglue-catalog)   |  |  | 
|   [ GetSecurityConfiguration ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-GetSecurityConfiguration)  | Grants permission to retrieve a security configuration | Read |  |  |  | 
|   [ GetSecurityConfigurations ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-GetSecurityConfigurations)  | Grants permission to retrieve one or more security configurations | Read |  |  |  | 
|   [ GetTable ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTable)  | Grants permission to retrieve a table | Read |  |  |  | 
|   [ GetTableVersion ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTableVersion)  | Grants permission to retrieve a version of a table | Read |  |  |  | 
|   [ GetTableVersions ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTableVersions)  | Grants permission to retrieve a list of versions of a table | Read |  |  |  | 
|   [ GetTables ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTables)  | Grants permission to retrieve the tables in a database | Read |  |  |  | 
|   [ GetTags ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-tags.html#aws-glue-api-tags-UntagResource)  | Grants permission to retrieve all tags associated with a resource | Read |  |  |  | 
|   [ GetTrigger ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-GetTrigger)  | Grants permission to retrieve a trigger | Read |  |  |  | 
|   [ GetTriggers ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-GetTriggers)  | Grants permission to retrieve the triggers associated with a job | Read |  |  |  | 
|   [ GetUserDefinedFunction ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-GetUserDefinedFunction)  | Grants permission to retrieve a function definition\. | Read |  |  |  | 
|   [ GetUserDefinedFunctions ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-GetUserDefinedFunctions)  | Grants permission to retrieve multiple function definitions | Read |  |  |  | 
|   [ GetWorkflow ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-GetWorkflow)  | Grants permission to retrieve a workflow | Read |  |  |  | 
|   [ GetWorkflowRun ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-GetWorkflowRun)  | Grants permission to retrieve a workflow run | Read |  |  |  | 
|   [ GetWorkflowRunProperties ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-GetWorkflowRunProperties)  | Grants permission to retrieve workflow run properties | Read |  |  |  | 
|   [ GetWorkflowRuns ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-GetWorkflowRuns)  | Grants permission to retrieve all runs of a workflow | Read |  |  |  | 
|   [ ImportCatalogToGlue ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-migration.html#aws-glue-api-catalog-migration-ImportCatalogToGlue)  | Grants permission to import an Athena data catalog into AWS Glue | Write |  |  |  | 
|   [ ListCrawlers ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-ListCrawlers)  | Grants permission to retrieve all crawlers | List |  |  |  | 
|   [ ListDevEndpoints ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-dev-endpoint.html#aws-glue-api-dev-endpoint-ListDevEndpoints)  | Grants permission to retrieve all development endpoints | List |  |  |  | 
|   [ ListJobs ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-ListJobs)  | Grants permission to retrieve all current jobs | List |  |  |  | 
|   [ ListTriggers ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-ListTriggers)  | Grants permission to retrieve all triggers | List |  |  |  | 
|   [ ListWorkflows ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-ListWorkflows)  | Grants permission to retrieve all workflows | List |  |  |  | 
|   [ PutDataCatalogEncryptionSettings ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-PutDataCatalogEncryptionSettings)  | Grants permission to update catalog encryption settings | Write |  |  |  | 
|   [ PutResourcePolicy ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-security.html#aws-glue-api-jobs-security-PutResourcePolicy)  | Grants permission to update a resource policy | Write |   [ catalog\* ](#awsglue-catalog)   |  |  | 
|   [ PutWorkflowRunProperties ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-PutWorkflowRunProperties)  | Grants permission to update workflow run properties | Write |  |  |  | 
|   [ ResetJobBookmark ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-ResetJobBookmark)  | Grants permission to reset a job bookmark | Write |  |  |  | 
|   [ StartCrawler ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-StartCrawler)  | Grants permission to start a crawler | Write |  |  |  | 
|   [ StartCrawlerSchedule ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-scheduler.html#aws-glue-api-crawler-scheduler-StartCrawlerSchedule)  | Grants permission to change the schedule state of a crawler to SCHEDULED | Write |  |  |  | 
|   [ StartJobRun ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-StartJobRun)  | Grants permission to start running a job | Write |  |  |  | 
|   [ StartTrigger ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-StartTrigger)  | Grants permission to start a trigger | Write |  |  |  | 
|   [ StartWorkflowRun ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-StartWorkflowRun)  | Grants permission to start running a workflow | Write |  |  |  | 
|   [ StopCrawler ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-StopCrawler)  | Grants permission to stop a running crawler | Write |  |  |  | 
|   [ StopCrawlerSchedule ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-scheduler.html#aws-glue-api-crawler-scheduler-StopCrawlerSchedule)  | Grants permission to set the schedule state of a crawler to NOT\_SCHEDULED | Write |  |  |  | 
|   [ StopTrigger ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-StopTrigger)  | Grants permission to stop a trigger | Write |  |  |  | 
|   [ TagResource ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-tags.html#aws-glue-api-tags-TagResource)  | Grants permission to add tags to a resource | Read |  |  |  | 
|   [ UntagResource ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-tags.html#aws-glue-api-tags-UntagResource)  | Grants permission to remove tags associated with a resource | Read |  |  |  | 
|   [ UpdateClassifier ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-UpdateClassifier)  | Grants permission to update a classifier | Write |  |  |  | 
|   [ UpdateConnection ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-UpdateConnection)  | Grants permission to update a connection | Write |  |  |  | 
|   [ UpdateCrawler ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-UpdateCrawler)  | Grants permission to update a crawler | Write |  |  |  | 
|   [ UpdateDatabase ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-UpdateDatabase)  | Grants permission to update a database | Write |  |  |  | 
|   [ UpdateDevEndpoint ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-dev-endpoint.html#aws-glue-api-dev-endpoint-UpdateDevEndpoint)  | Grants permission to update a development endpoint | Write |  |  |  | 
|   [ UpdateJob ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-UpdateJob)  | Grants permission to update a job | Write |  |  |  | 
|   [ UpdatePartition ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-UpdatePartition)  | Grants permission to update a partition | Write |  |  |  | 
|   [ UpdateTable ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-UpdateTable)  | Grants permission to update a table | Write |  |  |  | 
|   [ UpdateTrigger ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-UpdateTrigger)  | Grants permission to update a trigger | Write |  |  |  | 
|   [ UpdateUserDefinedFunction ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-UpdateUserDefinedFunction)  | Grants permission to update a function definition | Write |  |  |  | 
|   [ UpdateWorkflow ](https://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-workflow.html#aws-glue-api-workflow-UpdateWorkflow)  | Grants permission to update a workflow | Write |  |  |  | 

## Resources Defined by AWS Glue<a name="awsglue-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awsglue-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
|   [ catalog ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:catalog/$\{CatalogName\}  |  | 
|   [ database ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:database/$\{DatabaseName\}  |  | 
|   [ table ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:table/$\{TableName\}  |  | 
|   [ partition ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:partition/$\{PartitionName\}  |  | 
|   [ tableversion ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:tableVersion/$\{TableVersionName\}  |  | 
|   [ connection ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:connection/$\{ConnectionName\}  |  | 
|   [ userdefinedfunction ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:userDefinedFunction/$\{UserDefinedFunctionName\}  |  | 
|   [ devendpoint ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:devendpoint/$\{DevEndpointName\}  |  | 
|   [ job ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:job/$\{JobName\}  |  | 
|   [ trigger ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:trigger/$\{TriggerName\}  |  | 
|   [ crawler ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:crawler/$\{CrawlerName\}  |  | 
|   [ workflow ](https://docs.aws.amazon.com/glue/latest/dg/glue-specifying-resource-arns.html)  |  arn:$\{Partition\}:glue:$\{Region\}:$\{Account\}:workflow/$\{WorkflowName\}  |  | 

## Condition Keys for AWS Glue<a name="awsglue-policy-keys"></a>

Glue has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.