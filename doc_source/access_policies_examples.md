# Example IAM identity\-based policies<a name="access_policies_examples"></a>

A [policy](access_policies.md) is an object in AWS that, when associated with an identity or resource, defines their permissions\. AWS evaluates these policies when an IAM principal \(user or role\) makes a request\. Permissions in the policies determine whether the request is allowed or denied\. Most policies are stored in AWS as JSON documents that are attached to an IAM identity \(user, group of users, or role\)\. Identity\-based policies include AWS managed policies, customer managed policies, and inline policies\. To learn how to create an IAM policy using these example JSON policy documents, see [Creating policies on the JSON tab](access_policies_create-console.md#access_policies_create-json-editor)\.

By default all requests are denied, so you must provide access to the services, actions, and resources that you intend for the identity to access\. If you also want to allow access to complete the specified actions in the IAM console, you need to provide additional permissions\.

The following library of policies can help you define permissions for your IAM identities\. After you find the policy that you need, choose **view this policy** to view the JSON for the policy\. You can use the JSON policy document as a template for your own policies\.

**Note**  
If you would like to submit a policy to be included in this reference guide, use the **Feedback** button at the bottom of this page\.

## Example policies: AWS<a name="policy_library_AWS"></a>
+ Allows access during a specific range of dates\. \([View this policy](reference_policies_examples_aws-dates.md)\.\)
+ Allows enabling and disabling AWS Regions\. \([View this policy](reference_policies_examples_aws-enable-disable-regions.md)\.\)
+ Allows MFA\-authenticated users to manage their own credentials on the **My Security Credentials** page\. \([View this policy](reference_policies_examples_aws_my-sec-creds-self-manage.md)\.\)
+ Allows specific access when using MFA during a specific range of dates\. \([View this policy](reference_policies_examples_aws_mfa-dates.md)\.\)
+ Allows users to manage their own credentials on the **My Security Credentials** page\. \([View this policy](reference_policies_examples_aws_my-sec-creds-self-manage-no-mfa.md)\.\)
+ Allows users to manage their own MFA device on the **My Security Credentials** page\. \([View this policy](reference_policies_examples_aws_my-sec-creds-self-manage-mfa-only.md)\.\)
+ Allows users to manage their own password on the **My Security Credentials** page\. \([View this policy](reference_policies_examples_aws_my-sec-creds-self-manage-password-only.md)\.\)
+ Allows users to manage their own password, access keys, and SSH public keys on the **My Security Credentials** page\. \([View this policy](reference_policies_examples_aws_my-sec-creds-self-manage-pass-accesskeys-ssh.md)\.\)
+ Denies access to AWS based on the requested Region\. \([View this policy](reference_policies_examples_aws_deny-requested-region.md)\.\)
+ Denies access to AWS based on the source IP address\. \([View this policy](reference_policies_examples_aws_deny-ip.md)\.\)

## Example policies: AWS Data Pipeline<a name="policy_library_DataPipeline"></a>
+ Denies access to pipelines that a user did not create \([View this policy](reference_policies_examples_datapipeline_not-owned.md)\.\)

## Example policies: Amazon DynamoDB<a name="policy_library_DynamoDB"></a>
+ Allows access to a specific Amazon DynamoDB table \([View this policy](reference_policies_examples_dynamodb_specific-table.md)\.\)
+ Allows access to specific Amazon DynamoDB columns \([View this policy](reference_policies_examples_dynamodb_columns.md)\.\)
+ Allows row\-level access to Amazon DynamoDB based on an Amazon Cognito ID \([View this policy](reference_policies_examples_dynamodb_rows.md)\.\)

## Example policies: Amazon EC2<a name="policy_library_ec2"></a>
+ Allows an Amazon EC2 instance to attach or detach volumes \([View this policy](reference_policies_examples_ec2_volumes-instance.md)\.\)
+ Allows attaching or detaching Amazon EBS volumes to Amazon EC2 instances based on tags \([View this policy](reference_policies_examples_ec2_ebs-owner.md)\.\)
+ Allows launching Amazon EC2 instances in a specific subnet, programmatically and in the console \([View this policy](reference_policies_examples_ec2_instances-subnet.md)\.\)
+ Allows managing Amazon EC2 security groups associated with a specific VPC, programmatically and in the console \([View this policy](reference_policies_examples_ec2_securitygroups-vpc.md)\.\)
+ Allows starting or stopping Amazon EC2 instances a user has tagged, programmatically and in the console \([View this policy](reference_policies_examples_ec2_tag-owner.md)\.\)
+ Allows starting or stopping Amazon EC2 instances based on resource and principal tags, programmatically and in the console \([View this policy](reference_policies_examples_ec2-start-stop-tags.md)\.\)
+ Allows starting or stopping Amazon EC2 instances when the resource and principal tags match \([View this policy](reference_policies_examples_ec2-start-stop-match-tags.md)\.\)
+ Allows full Amazon EC2 access within a specific Region, programmatically and in the console\. \([View this policy](reference_policies_examples_ec2_region.md)\.\)
+ Allows starting or stopping a specific Amazon EC2 instance and modifying a specific security group, programmatically and in the console \([View this policy](reference_policies_examples_ec2_instance-securitygroup.md)\.\)
+ Denies access to specific Amazon EC2 operations without MFA \([View this policy](reference_policies_examples_ec2_require-mfa.md)\.\)
+ Limits terminating Amazon EC2 instances to a specific IP address range \([View this policy](reference_policies_examples_ec2_terminate-ip.md)\.\)

## Example policies: AWS Identity and Access Management \(IAM\)<a name="policy_library_IAM"></a>
+ Allows access to the policy simulator API \([View this policy](reference_policies_examples_iam_policy-sim.md)\.\)
+ Allows access to the policy simulator console \([View this policy](reference_policies_examples_iam_policy-sim-console.md)\.\)
+ Allows assuming any roles that have a specific tag, programmatically and in the console \([View this policy](reference_policies_examples_iam-assume-tagged-role.md)\.\)
+ Allows and denies access to multiple services, programmatically and in the console \([View this policy](reference_policies_examples_iam_multiple-services-console.md)\.\)
+ Allows adding a specific tag to an IAM user with a different specific tag, programmatically and in the console \([View this policy](reference_policies_examples_iam-add-tag.md)\.\)
+ Allows adding a specific tag to any IAM user or role, programmatically and in the console \([View this policy](reference_policies_examples_iam-add-tag-user-role.md)\.\)
+ Allows creating a new user only with specific tags \([View this policy](reference_policies_examples_iam-new-user-tag.md)\.\)
+ Allows generating and retrieving IAM credential reports \([View this policy](reference_policies_examples_iam-credential-report.md)\.\)
+ Allows managing a group's membership, programmatically and in the console \([View this policy](reference_policies_examples_iam_manage-group-membership.md)\.\)
+ Allows managing a specific tag \([View this policy](reference_policies_examples_iam-manage-tags.md)\.\)
+ Allows passing an IAM role to a specific service \([View this policy](reference_policies_examples_iam-passrole-service.md)\.\)
+ Allows read\-only access to the IAM console without reporting \([View this policy](reference_policies_examples_iam_read-only-console-no-reporting.md)\.\)
+ Allows read\-only access to the IAM console \([View this policy](reference_policies_examples_iam_read-only-console.md)\.\)
+ Allows specific users to manage a group, programmatically and in the console \([View this policy](reference_policies_examples_iam_users-manage-group.md)\.\)
+ Allows setting the account password requirements, programmatically and in the console \([View this policy](reference_policies_examples_iam_set-account-pass-policy.md)\.\)
+ Allows using the policy simulator API for users with a specific path \([View this policy](reference_policies_examples_iam_policy-sim-path.md)\.\)
+ Allows using the policy simulator console for users with a specific path \([View this policy](reference_policies_examples_iam_policy-sim-path-console.md)\.\)
+ Allows IAM users to self\-manage an MFA device\. \([View this policy](reference_policies_examples_iam_mfa-selfmanage.md)\.\)
+ Allows IAM users to rotate their own credentials, programmatically and in the console\. \([View this policy](reference_policies_examples_iam_credentials_console.md)\.\)
+ Allows viewing service last accessed information for an AWS Organizations policy in the IAM console\. \([View this policy](reference_policies_examples_iam_service-accessed-data-orgs.md)\.\)
+ Limits managed policies that can be applied to an IAM user, group, or role \([View this policy](reference_policies_examples_iam_limit-managed.md)\.\)

## Example policies: AWS Lambda<a name="policy_library_Lambda"></a>
+ Allows an AWS Lambda function to access an Amazon DynamoDB table \([View this policy](reference_policies_examples_lambda-access-dynamodb.md)\.\)

## Example policies: Amazon RDS<a name="policy_library_RDS"></a>
+ Allows full Amazon RDS database access within a specific Region\. \([View this policy](reference_policies_examples_rds_region.md)\.\)
+ Allows restoring Amazon RDS databases, programmatically and in the console \([View this policy](reference_policies_examples_rds_db-console.md)\.\)
+ Allows tag owners full access to Amazon RDS resources that they have tagged \([View this policy](reference_policies_examples_rds_tag-owner.md)\.\)

## Example policies: Amazon S3<a name="policy_library_S3"></a>
+ Allows an Amazon Cognito user to access objects in their own Amazon S3 bucket \([View this policy](reference_policies_examples_s3_cognito-bucket.md)\.\)
+ Allows federated users to access their own home directory in Amazon S3, programmatically and in the console \([View this policy](reference_policies_examples_s3_federated-home-directory-console.md)\.\)
+ Allows full S3 access, but explicitly denies access to the Production bucket if the administrator has not signed in using MFA within the last thirty minutes \([View this policy](reference_policies_examples_s3_full-access-except-production.md)\.\)
+ Allows IAM users to access their own home directory in Amazon S3, programmatically and in the console \([View this policy](reference_policies_examples_s3_home-directory-console.md)\.\)
+ Allows a user to manage a single Amazon S3 bucket and denies every other AWS action and resource \([View this policy](reference_policies_examples_s3_deny-except-bucket.md)\.\)
+ Allows `Read` and `Write` access to a specific Amazon S3 bucket \([View this policy](reference_policies_examples_s3_rw-bucket.md)\.\)
+ Allows `Read` and `Write` access to a specific Amazon S3 bucket, programmatically and in the console \([View this policy](reference_policies_examples_s3_rw-bucket-console.md)\.\)