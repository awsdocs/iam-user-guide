# Actions, Resources, and Condition Keys for AWS Glue<a name="list_awsglue"></a>

AWS Glue \(service prefix: `glue`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/glue/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/glue/latest/dg/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/glue/latest/dg/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Glue](#awsglue-actions-as-permissions)
+ [Resources Defined by Glue](#awsglue-resources-for-iam-policies)
+ [Condition Keys for AWS Glue](#awsglue-policy-keys)

## Actions Defined by AWS Glue<a name="awsglue-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  

| Actions | Description | Access Level | Resource Types \(\*required\) | Condition Keys | Dependent Actions | 
| --- | --- | --- | --- | --- | --- | 
|   [ BatchCreatePartition ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchCreatePartition)  | Creates one or more partitions in a batch operation\. | Write |  |  |  | 
|   [ BatchDeleteConnection ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-BatchDeleteConnection)  | Deletes a list of connection definitions from the data catalog\. | Write |  |  |  | 
|   [ BatchDeletePartition ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchDeletePartition)  | Deletes one or more partitions in a batch operation\. | Write |  |  |  | 
|   [ BatchDeleteTable ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-BatchDeleteTable)  | Deletes multiple tables at once\. | Write |  |  |  | 
|   [ BatchGetPartition ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchGetPartition)  | Retrieves partitions in a batch request\. | Read |  |  |  | 
|   [ CreateClassifier ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-CreateClassifier)  | Creates a Classifier in the user's account\. | Write |  |  |  | 
|   [ CreateConnection ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-CreateConnection)  | Creates a connection definition in the data catalog\. | Write |  |  |  | 
|   [ CreateCrawler ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-CreateCrawler)  | Creates a new Crawler with specified targets\. | Write |  |  |  | 
|   [ CreateDatabase ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-CreateDatabase)  | Creates a new database in a data catalog\. | Write |  |  |  | 
|   [ CreateDevEndpoint ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-CreateDevEndpoint)  | Creates a new DevEndpoint\. | Write |  |  |  | 
|   [ CreateJob ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-CreateJob)  | Creates a new job\. | Write |  |  |  | 
|   [ CreatePartition ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-CreatePartition)  | Creates a new partition\. | Write |  |  |  | 
|   [ CreateScript ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-scripts-scripts.html#aws-glue-api-etl-scripts-scripts-CreateScript)  | Transforms a directed acyclic graph \(DAG\) into a Python script\. | Write |  |  |  | 
|   [ CreateTable ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-CreateTable)  | Creates a new table definition in the data catalog\. | Write |  |  |  | 
|   [ CreateTrigger ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-CreateTrigger)  | Creates a new trigger\. | Write |  |  |  | 
|   [ CreateUserDefinedFunction ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-CreateUserDefinedFunction)  | Creates a new function definition in the data catalog\. | Write |  |  |  | 
|   [ DeleteClassifier ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-DeleteClassifier)  | Removes a Classifier from the metadata store\. | Write |  |  |  | 
|   [ DeleteConnection ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-DeleteConnection)  | Deletes a connection from the data catalog\. | Write |  |  |  | 
|   [ DeleteCrawler ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-DeleteCrawler)  | Removes a specified Crawler from the metadata store\. | Write |  |  |  | 
|   [ DeleteDatabase ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-DeleteDatabase)  | Removes a specified database from a data catalog\. | Write |  |  |  | 
|   [ DeleteDevEndpoint ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-DeleteDevEndpoint)  | Deletes a specified DevEndpoint\. | Write |  |  |  | 
|   [ DeleteJob ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-DeleteJob)  | Deletes a specified job\. | Write |  |  |  | 
|   [ DeletePartition ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-DeletePartition)  | Deletes a specified partition\. | Write |  |  |  | 
|   [ DeleteTable ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-DeleteTable)  | Removes a table definition from the data catalog\. | Write |  |  |  | 
|   [ DeleteTrigger ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-DeleteTrigger)  | Deletes a specified trigger\. | Write |  |  |  | 
|   [ DeleteUserDefinedFunction ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-DeleteUserDefinedFunction)  | Deletes an existing function definition from the data catalog\. | Write |  |  |  | 
|   [ GetCatalogImportStatus ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-migration.html#aws-glue-api-catalog-migration-GetCatalogImportStatus)  | Updates an existing function definition in the data catalog\. | Read |  |  |  | 
|   [ GetClassifier ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-GetClassifier)  | Retrieve a Classifier by name\. | Read |  |  |  | 
|   [ GetClassifiers ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-GetClassifiers)  | Lists all Classifier objects in the metadata store\. | Read |  |  |  | 
|   [ GetConnection ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-GetConnection)  | Retrieves a connection definition from the data catalog\. | Read |  |  |  | 
|   [ GetConnections ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-GetConnections)  | Retrieves a list of connection definitions from the data catalog\. | Read |  |  |  | 
|   [ GetCrawler ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawler)  | Retrieves metadata for a specified Crawler\. | Read |  |  |  | 
|   [ GetCrawlerMetrics ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawlerMetrics)  | Retrieves metrics about specified crawlers\. | Read |  |  |  | 
|   [ GetCrawlers ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawlers)  | Retrieves metadata for all Crawlers defined in the customer account\. | Read |  |  |  | 
|   [ GetDatabase ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-GetDatabase)  | Retrieves the definition of a specified database\. | Read |  |  |  | 
|   [ GetDatabases ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-GetDatabases)  | Retrieves all databases defined in a given data catalog\. | Read |  |  |  | 
|   [ GetDataflowGraph ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-scripts-scripts.html#aws-glue-api-etl-scripts-scripts-GetDataflowGraph)  | Transforms a Python script into a directed acyclic graph \(DAG\)\. | Read |  |  |  | 
|   [ GetDevEndpoint ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-GetDevEndpoint)  | Retrieves information about a specified DevEndpoint\. | Read |  |  |  | 
|   [ GetDevEndpoints ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-GetDevEndpoints)  | Retrieves all the DevEndpoints in this AWS account | Read |  |  |  | 
|   [ GetJob ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-GetJob)  | Retrieves an existing job definition\. | Read |  |  |  | 
|   [ GetJobRun ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-GetJobRun)  | Retrieves the metadata for a given job run\. | Read |  |  |  | 
|   [ GetJobRuns ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-GetJobRuns)  | Retrieves metadata for all runs of a given job\. | Read |  |  |  | 
|   [ GetJobs ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-GetJobs)  | Retrieves all current jobs\. | Read |  |  |  | 
|   [ GetMapping ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-scripts-scripts.html#aws-glue-api-etl-scripts-scripts-GetMapping)  | Creates mappings\. | Write |  |  |  | 
|   [ GetPartition ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-GetPartition)  | Retrieves information about a specified partition\. | Read |  |  |  | 
|   [ GetPartitions ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-GetPartitions)  | Retrieves information about the partitions in a table\. | Read |  |  |  | 
|   [ GetPlan ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-scripts-scripts.html#aws-glue-api-etl-scripts-scripts-GetPlan)  | Gets a Python script to perform a specified mapping\. | Read |  |  |  | 
|   [ GetTable ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTable)  | Retrieves the Table definition in a data catalog for a specified table | Read |  |  |  | 
|   [ GetTableVersions ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTableVersions)  | Retrieves a list of strings that identify available versions of a specified table\. | Read |  |  |  | 
|   [ GetTables ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTables)  | Retrieves the definitions of some or all of the tables in a given database\. | Read |  |  |  | 
|   [ GetTrigger ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-GetTrigger)  | Retrieves the definition of a trigger\. | Read |  |  |  | 
|   [ GetTriggers ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-GetTriggers)  | Gets all the triggers associated with a job\. | Read |  |  |  | 
|   [ GetUserDefinedFunction ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-GetUserDefinedFunction)  | Retrieves a specified function definition from the data catalog\. | Read |  |  |  | 
|   [ GetUserDefinedFunctions ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-GetUserDefinedFunctions)  | Retrieves a multiple function definitions from the data catalog\. | Read |  |  |  | 
|   [ ImportCatalogToGlue ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-migration.html#aws-glue-api-catalog-migration-ImportCatalogToGlue)  | Imports an existing Athena data catalog to AWS Glue\. | Write |  |  |  | 
|   [ ResetJobBookmark ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-ResetJobBookmark)  | Resets a bookmark entry\. | Write |  |  |  | 
|   [ StartCrawler ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-StartCrawler)  | Starts a crawl using the specified Crawler\. | Write |  |  |  | 
|   [ StartCrawlerSchedule ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-scheduler.html#aws-glue-api-crawler-scheduler-StartCrawlerSchedule)  | Changes the schedule state of the specified crawler to SCHEDULED\. | Write |  |  |  | 
|   [ StartJobRun ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-StartJobRun)  | Runs a job\. | Write |  |  |  | 
|   [ StartTrigger ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-StartTrigger)  | Starts an existing trigger\. | Write |  |  |  | 
|   [ StopCrawler ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-StopCrawler)  | If the specified Crawler is running, stops the crawl\. | Write |  |  |  | 
|   [ StopCrawlerSchedule ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-scheduler.html#aws-glue-api-crawler-scheduler-StopCrawlerSchedule)  | Sets the schedule state of the specified crawler to NOT\_SCHEDULED\. | Write |  |  |  | 
|   [ StopTrigger ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-StopTrigger)  | Stops a specified trigger | Write |  |  |  | 
|   [ UpdateClassifier ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-UpdateClassifier)  | Modifies an existing Classifier\. | Write |  |  |  | 
|   [ UpdateConnection ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-UpdateConnection)  | Updates a connection definition in the data catalog\. | Write |  |  |  | 
|   [ UpdateCrawler ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-UpdateCrawler)  | Updates a Crawler\. | Write |  |  |  | 
|   [ UpdateDatabase ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-UpdateDatabase)  | Updates an existing database definition in a data catalog\. | Write |  |  |  | 
|   [ UpdateDevEndpoint ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-UpdateDevEndpoint)  | Updates a specified DevEndpoint\. | Write |  |  |  | 
|   [ UpdateJob ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-UpdateJob)  | Updates an existing job definition\. | Write |  |  |  | 
|   [ UpdatePartition ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-UpdatePartition)  | Updates a partition\. | Write |  |  |  | 
|   [ UpdateTable ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-UpdateTable)  | Gets information about the results of the specified query execution\. | Write |  |  |  | 
|   [ UpdateTrigger ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-UpdateTrigger)  | Updates a trigger definition\. | Write |  |  |  | 
|   [ UpdateUserDefinedFunction ](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-UpdateUserDefinedFunction)  | Updates an existing function definition in the data catalog\. | Write |  |  |  | 

## Resources Defined by Glue<a name="awsglue-resources-for-iam-policies"></a>

AWS Glue has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Glue<a name="awsglue-policy-keys"></a>

Glue has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.