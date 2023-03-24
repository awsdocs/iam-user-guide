# Create a long\-lived Amazon EMR cluster and run steps using an AWS SDK<a name="example_cross_LongLivedEmrCluster_section"></a>

The following code example shows how to create a long\-lived Amazon EMR cluster and run several steps\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 Create a long\-lived Amazon EMR cluster that uses Apache Spark to query historical Amazon review data from the [Amazon Customer Reviews Dataset](https://s3.amazonaws.com/amazon-reviews-pds/readme.html)\. Run a job that gets data for top\-rated products in specific categories that contain keywords in their product titles\. Job results are written to an Amazon Simple Storage Service \(Amazon S3\) bucket\.   
+ Create an Amazon S3 bucket and upload a job script\.
+ Create AWS Identity and Access Management \(IAM\) roles\.
+ Create Amazon Elastic Compute Cloud \(Amazon EC2\) security groups\.
+ Create a long\-lived cluster and run several job steps\.
 This example is best viewed on GitHub\. For complete source code and instructions on how to set up and run, see the full example on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/emr)\.   

**Services used in this example**
+ Amazon EC2
+ Amazon EMR
+ IAM
+ Amazon S3

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.