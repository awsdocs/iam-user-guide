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
| [BatchCreatePartition](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchCreatePartition) | Creates one or more partitions in a batch operation\. |   |  |  |  | 
| [BatchDeleteConnection](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-BatchDeleteConnection) | Deletes a list of connection definitions from the data catalog\. |   |  |  |  | 
| [BatchDeletePartition](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchDeletePartition) | Deletes one or more partitions in a batch operation\. |   |  |  |  | 
| [BatchDeleteTable](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-BatchDeleteTable) | Deletes multiple tables at once\. |   |  |  |  | 
| [BatchGetPartition](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-BatchGetPartition) | Retrieves partitions in a batch request\. |   |  |  |  | 
| [CreateClassifier](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-CreateClassifier) | Creates a Classifier in the user's account\. |   |  |  |  | 
| [CreateConnection](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-CreateConnection) | Creates a connection definition in the data catalog\. |   |  |  |  | 
| [CreateCrawler](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-CreateCrawler) | Creates a new Crawler with specified targets\. |   |  |  |  | 
| [CreateDatabase](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-CreateDatabase) | Creates a new database in a data catalog\. |   |  |  |  | 
| [CreateDevEndpoint](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-CreateDevEndpoint) | Creates a new DevEndpoint\. |   |  |  |  | 
| [CreateJob](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-CreateJob) | Creates a new job\. |   |  |  |  | 
| [CreatePartition](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-CreatePartition) | Creates a new partition\. |   |  |  |  | 
| [CreateScript](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-scripts-scripts.html#aws-glue-api-etl-scripts-scripts-CreateScript) | Transforms a directed acyclic graph \(DAG\) into a Python script\. |   |  |  |  | 
| [CreateTable](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-CreateTable) | Creates a new table definition in the data catalog\. |   |  |  |  | 
| [CreateTrigger](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-CreateTrigger) | Creates a new trigger\. |   |  |  |  | 
| [CreateUserDefinedFunction](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-CreateUserDefinedFunction) | Creates a new function definition in the data catalog\. |   |  |  |  | 
| [DeleteClassifier](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-DeleteClassifier) | Removes a Classifier from the metadata store\. |   |  |  |  | 
| [DeleteConnection](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-DeleteConnection) | Deletes a connection from the data catalog\. |   |  |  |  | 
| [DeleteCrawler](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-DeleteCrawler) | Removes a specified Crawler from the metadata store\. |   |  |  |  | 
| [DeleteDatabase](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-DeleteDatabase) | Removes a specified database from a data catalog\. |   |  |  |  | 
| [DeleteDevEndpoint](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-DeleteDevEndpoint) | Deletes a specified DevEndpoint\. |   |  |  |  | 
| [DeleteJob](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-DeleteJob) | Deletes a specified job\. |   |  |  |  | 
| [DeletePartition](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-DeletePartition) | Deletes a specified partition\. |   |  |  |  | 
| [DeleteTable](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-DeleteTable) | Removes a table definition from the data catalog\. |   |  |  |  | 
| [DeleteTrigger](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-DeleteTrigger) | Deletes a specified trigger\. |   |  |  |  | 
| [DeleteUserDefinedFunction](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-DeleteUserDefinedFunction) | Deletes an existing function definition from the data catalog\. |   |  |  |  | 
| [GetCatalogImportStatus](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-migration.html#aws-glue-api-catalog-migration-GetCatalogImportStatus) | Updates an existing function definition in the data catalog\. |   |  |  |  | 
| [GetClassifier](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-GetClassifier) | Retrieve a Classifier by name\. |   |  |  |  | 
| [GetClassifiers](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-GetClassifiers) | Lists all Classifier objects in the metadata store\. |   |  |  |  | 
| [GetConnection](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-GetConnection) | Retrieves a connection definition from the data catalog\. |   |  |  |  | 
| [GetConnections](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-GetConnections) | Retrieves a list of connection definitions from the data catalog\. |   |  |  |  | 
| [GetCrawler](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawler) | Retrieves metadata for a specified Crawler\. |   |  |  |  | 
| [GetCrawlerMetrics](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawlerMetrics) | Retrieves metrics about specified crawlers\. |   |  |  |  | 
| [GetCrawlers](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-GetCrawlers) | Retrieves metadata for all Crawlers defined in the customer account\. |   |  |  |  | 
| [GetDatabase](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-GetDatabase) | Retrieves the definition of a specified database\. |   |  |  |  | 
| [GetDatabases](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-GetDatabases) | Retrieves all databases defined in a given data catalog\. |   |  |  |  | 
| [GetDataflowGraph](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-scripts-scripts.html#aws-glue-api-etl-scripts-scripts-GetDataflowGraph) | Transforms a Python script into a directed acyclic graph \(DAG\)\. |   |  |  |  | 
| [GetDevEndpoint](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-GetDevEndpoint) | Retrieves information about a specified DevEndpoint\. |   |  |  |  | 
| [GetDevEndpoints](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-GetDevEndpoints) | Retrieves all the DevEndpoints in this AWS account |   |  |  |  | 
| [GetJob](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-GetJob) | Retrieves an existing job definition\. |   |  |  |  | 
| [GetJobRun](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-GetJobRun) | Retrieves the metadata for a given job run\. |   |  |  |  | 
| [GetJobRuns](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-GetJobRuns) | Retrieves metadata for all runs of a given job\. |   |  |  |  | 
| [GetJobs](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-GetJobs) | Retrieves all current jobs\. |   |  |  |  | 
| [GetMapping](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-scripts-scripts.html#aws-glue-api-etl-scripts-scripts-GetMapping) | Creates mappings\. |   |  |  |  | 
| [GetPartition](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-GetPartition) | Retrieves information about a specified partition\. |   |  |  |  | 
| [GetPartitions](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-GetPartitions) | Retrieves information about the partitions in a table\. |   |  |  |  | 
| [GetPlan](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-etl-scripts-scripts.html#aws-glue-api-etl-scripts-scripts-GetPlan) | Gets a Python script to perform a specified mapping\. |   |  |  |  | 
| [GetTable](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTable) | Retrieves the Table definition in a data catalog for a specified table |   |  |  |  | 
| [GetTableVersions](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTableVersions) | Retrieves a list of strings that identify available versions of a specified table\. |   |  |  |  | 
| [GetTables](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-GetTables) | Retrieves the definitions of some or all of the tables in a given database\. |   |  |  |  | 
| [GetTrigger](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-GetTrigger) | Retrieves the definition of a trigger\. |   |  |  |  | 
| [GetTriggers](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-GetTriggers) | Gets all the triggers associated with a job\. |   |  |  |  | 
| [GetUserDefinedFunction](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-GetUserDefinedFunction) | Retrieves a specified function definition from the data catalog\. |   |  |  |  | 
| [GetUserDefinedFunctions](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-GetUserDefinedFunctions) | Retrieves a multiple function definitions from the data catalog\. |   |  |  |  | 
| [ImportCatalogToGlue](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-migration.html#aws-glue-api-catalog-migration-ImportCatalogToGlue) | Imports an existing Athena data catalog to AWS Glue\. |   |  |  |  | 
| [ResetJobBookmark](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-ResetJobBookmark) | Resets a bookmark entry\. |   |  |  |  | 
| [StartCrawler](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-StartCrawler) | Starts a crawl using the specified Crawler\. |   |  |  |  | 
| [StartCrawlerSchedule](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-scheduler.html#aws-glue-api-crawler-scheduler-StartCrawlerSchedule) | Changes the schedule state of the specified crawler to SCHEDULED\. |   |  |  |  | 
| [StartJobRun](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-runs.html#aws-glue-api-jobs-runs-StartJobRun) | Runs a job\. |   |  |  |  | 
| [StartTrigger](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-StartTrigger) | Starts an existing trigger\. |   |  |  |  | 
| [StopCrawler](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-StopCrawler) | If the specified Crawler is running, stops the crawl\. |   |  |  |  | 
| [StopCrawlerSchedule](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-scheduler.html#aws-glue-api-crawler-scheduler-StopCrawlerSchedule) | Sets the schedule state of the specified crawler to NOT\_SCHEDULED\. |   |  |  |  | 
| [StopTrigger](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-StopTrigger) | Stops a specified trigger |   |  |  |  | 
| [UpdateClassifier](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-classifiers.html#aws-glue-api-crawler-classifiers-UpdateClassifier) | Modifies an existing Classifier\. |   |  |  |  | 
| [UpdateConnection](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-connections.html#aws-glue-api-catalog-connections-UpdateConnection) | Updates a connection definition in the data catalog\. |   |  |  |  | 
| [UpdateCrawler](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-crawler-crawling.html#aws-glue-api-crawler-crawling-UpdateCrawler) | Updates a Crawler\. |   |  |  |  | 
| [UpdateDatabase](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-databases.html#aws-glue-api-catalog-databases-UpdateDatabase) | Updates an existing database definition in a data catalog\. |   |  |  |  | 
| [UpdateDevEndpoint](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-dev-endpoint.html#aws-glue-api-jobs-dev-endpoint-UpdateDevEndpoint) | Updates a specified DevEndpoint\. |   |  |  |  | 
| [UpdateJob](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-job.html#aws-glue-api-jobs-job-UpdateJob) | Updates an existing job definition\. |   |  |  |  | 
| [UpdatePartition](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-partitions.html#aws-glue-api-catalog-partitions-UpdatePartition) | Updates a partition\. |   |  |  |  | 
| [UpdateTable](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-tables.html#aws-glue-api-catalog-tables-UpdateTable) | Gets information about the results of the specified query execution\. |   |  |  |  | 
| [UpdateTrigger](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-jobs-trigger.html#aws-glue-api-jobs-trigger-UpdateTrigger) | Updates a trigger definition\. |   |  |  |  | 
| [UpdateUserDefinedFunction](http://docs.aws.amazon.com/glue/latest/dg/aws-glue-api-catalog-functions.html#aws-glue-api-catalog-functions-UpdateUserDefinedFunction) | Updates an existing function definition in the data catalog\. |   |  |  |  | 

## Resources Defined by Glue<a name="awsglue-resources-for-iam-policies"></a>

Glue has no service\-defined resources that can be used as the `Resource` element of an IAM policy statement\.

## Condition Keys for AWS Glue<a name="awsglue-policy-keys"></a>

Glue has no service\-specific context keys that can be used in the `Condition` element of policy statements\. For the list of the global context keys that are available to all services, see [Available Keys for Conditions](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.