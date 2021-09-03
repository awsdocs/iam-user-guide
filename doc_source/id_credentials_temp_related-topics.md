# Additional resources for temporary security credentials<a name="id_credentials_temp_related-topics"></a>

The following scenarios and applications can guide you in using temporary security credentials: 
+  [About web identity federation](id_roles_providers_oidc.md)\. This section discusses how to configure IAM roles when you use web identity federation and the `AssumeRoleWithWebIdentity` API\. 
+ [Configuring MFA\-protected API access](id_credentials_mfa_configure-api-require.md)\. This topic explains how to use roles to require multi\-factor authentication \(MFA\) to protect sensitive API actions in your account\.
+ [Token Vending Machine for Identity Registration](https://aws.amazon.com/code/7351543942956566)\. This sample Java web application uses the `GetFederationToken` API to serve temporary security credentials to remote clients\.

For more information on policies and permissions in AWS see the following topics:
+ [Access management for AWS resources](access.md)
+ [Policy evaluation logic](reference_policies_evaluation-logic.md)\.
+ [Managing Access Permissions to Your Amazon S3 Resources](https://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html) in *Amazon Simple Storage Service Developer Guide*\.
+  To learn whether principals in accounts outside of your zone of trust \(trusted organization or account\) have access to assume your roles, see [What is IAM Access Analyzer?](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)\.