# Troubleshooting access denied error messages<a name="troubleshoot_access-denied"></a>

Access denied errors appear when AWS explicitly or implicitly denies an authorization request\. An *explicit denial* occurs when a policy contains a `Deny` statement for the specific AWS action\. An *implicit denial* occurs when there is no applicable `Deny` statement and also no applicable `Allow` statement\. Because an IAM policy denies an IAM principal by default, the policy must explicitly allow the principal to perform an action\. Otherwise, the policy implicitly denies access\. For more information, see [The difference between explicit and implicit denies](reference_policies_evaluation-logic.md#AccessPolicyLanguage_Interplay)\.

Most access denied error messages appear in the format `User user is not authorized to perform action on resource because context`\. In this example, *user* is the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html#identifiers-arns) that doesn't receive access, *action* is the service action that the policy denies, and *resource* is the ARN of the resource on which the policy acts\. The *context* field represents additional context about the policy type that explains why the policy denied access\.

When a policy explicitly denies access because the policy contains a `Deny` statement, then AWS includes the phrase `with an explicit deny in a type policy` in the access denied error message\. When the policy implicitly denies access, then AWS includes the phrase `because no type policy allows the action action` in the access denied error message\. 

If multiple policies of the same policy type deny an authorization request, then AWS doesn't specify the number of policies in the access denied error message\. If multiple policy types deny an authorization request, AWS includes only one of those policy types in the error message\. 

## Access denied error message examples<a name="access-denied-error-examples"></a>

The following examples show the format for different types of access denied error messages\.

### Access denied due to a Service Control Policy<a name="access-denied-scp-examples"></a>

For the following error, check for a `Deny` statement or a missing `Allow` statement for `codecommit:ListRepositories` in your Service Control Policies \(SCPs\)\.

**Note**  
When an SCP denies access, the error message always includes the phrase `due to an explicit deny in a Service Control Policy`, even if the denial is implicit\.

```
User: arn:aws:iam::777788889999:user/JohnDoe is not authorized to perform: 
codecommit:ListRepositories with an explicit deny in a service control policy
```

### Access denied due to a VPC endpoint policy<a name="access-denied-vpc-endpoint-examples"></a>
+ Implicit denial: For the following error, check for a missing `Allow` statement for `codecommit:ListRepositories` in your Virtual Private Cloud \(VPC\) endpoint policies\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  codecommit:ListRepositories because no VPC endpoint policy allows the codecommit:ListRepositories action
  ```
+ Explicit denial: For the following error, check for an explicit `Deny` statement for `codecommit:ListDeployments` in your VPC endpoint policies\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  codedeploy:ListDeployments on resource: arn:aws:codedeploy:us-east-1:123456789012:deploymentgroup:* with an explicit deny in a VPC endpoint policy
  ```

### Access denied due to a permissions boundary<a name="access-denied-permissions-boundary-examples"></a>
+ Implicit denial: For the following error, check for a missing `Allow` statement for `codecommit:ListDeployments` in your permissions boundary\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  codedeploy:ListDeployments on resource: arn:aws:codedeploy:us-east-1:123456789012:deploymentgroup:* because no permissions boundary allows the codedeploy:ListDeployments action
  ```
+ Explicit denial: For the following error, check for an explicit `Deny` statement for `sagemaker:ListModels` in your permissions boundary\.

  ```
  User: arn:aws:iam::777788889999:user/JohnDoe is not authorized to perform: 
  sagemaker:ListModels with an explicit deny in a permissions boundary
  ```

### Access denied due to session policies<a name="access-denied-session-policy-examples"></a>
+ Implicit denial: For the following error, check for a missing `Allow` statement for `codecommit:ListRepositories` in your session policies\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  codecommit:ListRepositories because no session policy allows the codecommit:ListRepositories action
  ```
+ Explicit denial: For the following error, check for an explicit `Deny` statement for `codecommit:ListDeployments` in your session policies\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  codedeploy:ListDeployments on resource: arn:aws:codedeploy:us-east-1:123456789012:deploymentgroup:* with an explicit deny in a sessions policy
  ```

### Access denied due to resource\-based policies<a name="access-denied-resource-based-policy-examples"></a>
+ Implicit denial: For the following error, check for a missing `Allow` statement for `secretsmanager:GetSecretValue` in your resource\-based policy\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  secretsmanager:GetSecretValue because no resource-based policy allows the secretsmanager:GetSecretValue action
  ```
+ Explicit denial: For the following error, check for an explicit `Deny` statement for `secretsmanager:GetSecretValue` in your resource\-based policy\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  secretsmanager:GetSecretValue on resource: arn:aws:secretsmanager:us-east-1:123456789012:secret:* with an explicit deny in a resource-based policy
  ```

### Access denied due to role trust policies<a name="access-denied-role-trust-policy-examples"></a>
+ Implicit denial: For the following error, check for a missing `Allow` statement for `sts:AssumeRole` in your role trust policy\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  sts:AssumeRole because the role trust policy allows the sts:AssumeRole action
  ```
+ Explicit denial: For the following error, check for a missing `Allow` statement for `sts:AssumeRole` in your role trust policy\.

  ```
  User: arn:aws:iam::777788889999:user/JohnDoe is not authorized to perform: 
  sts:AssumeRole with an explicit deny in the role trust policy
  ```

### Access denied due to identity\-based policies<a name="access-denied-identity-based-policy-examples"></a>
+ Implicit denial: For the following error, check for a missing `Allow` statement for `codecommit:ListRepositories` in identity\-based policies attached to user `JohnDoe`\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  codecommit:ListRepositories because no identity-based policy allows the codecommit:ListRepositories action
  ```
+ Explicit denial: For the following error, check for an explicit `Deny` statement for `codedeploy:ListDeployments` in identity\-based policies attached to user `JohnDoe`\.

  ```
  User: arn:aws:iam::123456789012:user/JohnDoe is not authorized to perform: 
  codedeploy:ListDeployments on resource: arn:aws:codedeploy:us-east-1:123456789012:deploymentgroup:* with an explicit deny in an identity-based policy
  ```

### Access denied when a VPC request fails due to another policy<a name="access-denied-vpc-endpoint-examples"></a>

For the following error, check for an explicit `Deny` statement for `SNS:Publish` in your SCPs\.

```
User: arn:aws:sts::111122223333:assumed-role/role-name/role-session-name is not authorized to perform: 
SNS:Publish on resource: arn:aws:sns:us-east-1:444455556666:role-name-2 
with an explicit deny in a VPC endpoint policy transitively through a service control policy
```