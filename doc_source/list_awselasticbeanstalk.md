# Actions, Resources, and Condition Keys for AWS Elastic Beanstalk<a name="list_awselasticbeanstalk"></a>

AWS Elastic Beanstalk \(service prefix: `elasticbeanstalk`\) provides the following service\-specific resources, actions, and condition context keys for use in IAM permission policies\.

References:
+ Learn how to [configure this service](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/)\.
+ View a [list of the API operations available for this service](http://docs.aws.amazon.com/elasticbeanstalk/latest/api/)\.
+ Learn how to protect this service and its resources by [using IAM](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/access_permissions.html) permission policies\.

**Topics**
+ [Actions Defined by AWS Elastic Beanstalk](#awselasticbeanstalk-actions-as-permissions)
+ [Resources Defined by Elastic Beanstalk](#awselasticbeanstalk-resources-for-iam-policies)
+ [Condition Keys for AWS Elastic Beanstalk](#awselasticbeanstalk-policy-keys)

## Actions Defined by AWS Elastic Beanstalk<a name="awselasticbeanstalk-actions-as-permissions"></a>

You can specify the following actions in the `Action` element of an IAM policy statement\. By using policies, you define the permissions for anyone performing an operation in AWS\. When you use an action in a policy, you usually allow or deny access to the API operation or CLI command with the same name\. However, in some cases, a single action controls access to more than one operation\. Alternatively, some operations require several different actions\. For details about the columns in the following table, see [The Actions Table](reference_policies_actions-resources-contextkeys.md#actions_table)\.


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/list_awselasticbeanstalk.html)

## Resources Defined by Elastic Beanstalk<a name="awselasticbeanstalk-resources-for-iam-policies"></a>

The following resource types are defined by this service and can be used in the `Resource` element of IAM permission policy statements\. Each action in the [Actions table](#awselasticbeanstalk-actions-as-permissions) identifies the resource types that can be specified with that action\. A resource type can also define which condition keys you can include in a policy\. These keys are displayed in the last column of the table\. For details about the columns in the following table, see [The Resource Types Table](reference_policies_actions-resources-contextkeys.md#resources_table)\.


****  

| Resource Types | ARN | Condition Keys | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html) | arn:$\{Partition\}:elasticbeanstalk:$\{Region\}:$\{Account\}:application/$\{ApplicationName\} |  | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html) | arn:$\{Partition\}:elasticbeanstalk:$\{Region\}:$\{Account\}:applicationversion/$\{ApplicationName\}/$\{VersionLabel\} | [elasticbeanstalk:InApplication](#awselasticbeanstalk-elasticbeanstalk_InApplication)  | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html) | arn:$\{Partition\}:elasticbeanstalk:$\{Region\}:$\{Account\}:configurationtemplate/$\{ApplicationName\}/$\{TemplateName\} | [elasticbeanstalk:InApplication](#awselasticbeanstalk-elasticbeanstalk_InApplication)  | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html) | arn:$\{Partition\}:elasticbeanstalk:$\{Region\}:$\{Account\}:environment/$\{ApplicationName\}/$\{EnvironmentName\} | [elasticbeanstalk:InApplication](#awselasticbeanstalk-elasticbeanstalk_InApplication)  | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.arn.html) | arn:$\{Partition\}:elasticbeanstalk:$\{Region\}::solutionstack/$\{SolutionStackName\} |  | 

## Condition Keys for AWS Elastic Beanstalk<a name="awselasticbeanstalk-policy-keys"></a>

AWS Elastic Beanstalk defines the following condition keys that can be used in the `Condition` element of an IAM policy\. You can use these keys to further refine the conditions under which the policy statement applies\. For details about the columns in the following table, see [The Condition Keys Table](reference_policies_actions-resources-contextkeys.md#context_keys_table)\.

To view the global condition keys that are available to all services, see [Available Global Condition Keys](http://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#AvailableKeys) in the *IAM Policy Reference*\.


****  

| Condition Keys | Description | Type | 
| --- | --- | --- | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions) | An application as a dependency or a constraint on an input parameter\. | ARN | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions) | An application version as a dependency or a constraint on an input parameter\. | ARN | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions) | A configuration template as a dependency or a constraint on an input parameter\. | ARN | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions) | An environment as a dependency or a constraint on an input parameter\. | ARN | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions) | A solution stack as a dependency or a constraint on an input parameter\. | ARN | 
| [http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.iam.policies.actions.html#AWSHowTo.iam.policies.conditions) | The application that contains the resource that the action operates on\. | ARN | 