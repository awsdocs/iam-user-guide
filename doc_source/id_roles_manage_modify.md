# Modifying a role<a name="id_roles_manage_modify"></a>

You can use the AWS Management Console, the AWS CLI, or the IAM API to make changes to a role\.

**Topics**
+ [View role access](#roles-modify_prerequisites)
+ [Generate a policy based on access information](#roles-modify_gen-policy)
+ [Modifying a role \(console\)](roles-managingrole-editing-console.md)
+ [Modifying a role \(AWS CLI\)](roles-managingrole-editing-cli.md)
+ [Modifying a role \(AWS API\)](roles-managingrole-editing-api.md)

## View role access<a name="roles-modify_prerequisites"></a>

Before you change the permissions for a role, you should review its recent service\-level activity\. This is important because you don't want to remove access from a principal \(person or application\) who is using it\. For more information about viewing last accessed information, see [Refining permissions in AWS using last accessed information](access_policies_access-advisor.md)\.

## Generate a policy based on access information<a name="roles-modify_gen-policy"></a>

You might sometimes grant permissions to an IAM entity \(user or role\) beyond what they require\. To help you refine the permissions that you grant, you can generate an IAM policy that is based on the access activity for an entity\. IAM Access Analyzer reviews your AWS CloudTrail logs and generates a policy template that contains the permissions that have been used by the entity in your specified date range\. You can use the template to create a managed policy with fine\-grained permissions and then attach it to the IAM entity\. That way, you grant only the permissions that the user or role needs to interact with AWS resources for your specific use case\. To learn more, see [Generate policies based on access activity](access_policies_generate-policy.md)\.