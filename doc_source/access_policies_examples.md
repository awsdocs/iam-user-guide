# Example Policies<a name="access_policies_examples"></a>

A policy is an entity in AWS that, when attached to an identity or resource, defines their permissions\. AWS evaluates these policies when a principal, such as a user, makes a request\. Permissions in the policies determine whether the request is allowed or denied\. Policies are stored in AWS as JSON documents that are attached to principals as *identity\-based policies* or to resources as *resource\-based policies*\. You can attach an identity\-based policy to a principal \(or identity\), such as an IAM group, user, or role\. Identity\-based policies inlcude AWS managed policies, customer managed policies, and inline policies\. To learn how to create an IAM policy using these example JSON policy documents, see [[ERROR] BAD/MISSING LINK TEXT](access_policies_create.md#access_policies_create-json-editor)\.

By default all requests are denied, so you must provide access to the services, actions, and resources that you intend for the identity to access\. If you also want to allow access to complete the specified actions in the IAM console, you need to provide additional permissions\.

The following library of policies can help you define permissions for your IAM identities\. After you find the policy that you need, choose **View this policy** to view the JSON for the policy\. You can use the JSON policy document as a template for your own policies\.

**Note**  
If you would like to submit a policy to be included in this reference guide, use the **Feedback** button at the bottom of this page\.

## Example Policies: AWS<a name="policy_library_AWS"></a>

+ Allows access during a specific range of dates \(View this policy\)

+ Allows specific access when using MFA during a specific range of dates \(View this policy\)

+ Denies access to AWS based on the source IP address \(View this policy\)

## Example Policies: AWS CodeCommit<a name="policy_library_CodeCommit"></a>

+ Allows `Read` access to an AWS CodeCommit repository, programmatically and in the console \(View this policy\)

## Example Policies: AWS Data Pipeline<a name="policy_library_DataPipeline"></a>

+ Denies access to pipelines that a user did not create \(View this policy\)

## Example Policies: Amazon DynamoDB<a name="policy_library_DynamoDB"></a>

+ Allows access to a specific Amazon DynamoDB table \(View this policy\)

+ Allows access to specific Amazon DynamoDB columns \(View this policy\)

+ Allows row\-level access to Amazon DynamoDB based on an Amazon Cognito ID \(View this policy\)

## Example Policies: Amazon EC2<a name="policy_library_ec2"></a>

+ Allows an Amazon EC2 instance to attach or detach volumes \(View this policy\)

+ Allows attaching or detaching Amazon EBS volumes to Amazon EC2 instances based on tags \(View this policy\)

+ Allows launching Amazon EC2 instances in a specific subnet, programmatically and in the console \(View this policy\)

+ Allows managing Amazon EC2 security groups associated with a specific VPC, programmatically and in the console \(View this policy\)

+ Allows starting or stopping Amazon EC2 instances a user has tagged, programmatically and in the console \(View this policy\)

+ Allows full Amazon EC2 access within a specific region, programmatically and in the console \(View this policy\)

+ Allows starting or stopping a specific Amazon EC2 instance and modifying a specific security group, programmatically and in the console \(View this policy\)

+ Limits terminating Amazon EC2 instances to a specific IP address range \(View this policy\)

## Example Policies: AWS Identity and Access Management \(IAM\)<a name="policy_library_IAM"></a>

+ Allows access to the policy simulator API \(View this policy\)

+ Allows access to the policy simulator console \(View this policy\)

+ Allows using the policy simulator API for users with a specific path \(View this policy\)

+ Allows using the policy simulator console for users with a specific path \(View this policy\)

+ Allows IAM users to self\-manage an MFA device \(View this policy\)

+ Allows IAM users to rotate their own credentials, programmatically and in the console \(View this policy\)

+ Limits managed policies that can be applied to a new IAM user, group, or role \(View this policy\)

## Example Policies: Amazon RDS<a name="policy_library_RDS"></a>

+ Allows full Amazon RDS database access within a specific region \(View this policy\)

+ Allows restoring Amazon RDS databases, programmatically and in the console \(View this policy\)

+ Allows tag owners full access to Amazon RDS resources that they have tagged \(View this policy\)

## Example Policies: Amazon S3<a name="policy_library_S3"></a>

+ Allows an Amazon Cognito user to access objects in their own Amazon S3 bucket \(View this policy\)

+ Allows IAM users to access their own home directory in Amazon S3, programmatically and in the console \(View this policy\)

+ Allows a user to manage a single Amazon S3 bucket and denies every other AWS action and resource \(View this policy\)

+ Allows `Read` and `Write` access to a specific Amazon S3 bucket \(View this policy\)

+ Allows `Read` and `Write` access to a specific Amazon S3 bucket, programmatically and in the console \(View this policy\)