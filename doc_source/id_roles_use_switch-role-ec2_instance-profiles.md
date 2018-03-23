# Using Instance Profiles<a name="id_roles_use_switch-role-ec2_instance-profiles"></a>

An instance profile is a container for an IAM role that you can use to pass role information to an EC2 instance when the instance starts\.

## Managing Instance Profiles using the AWS Management Console<a name="instance-profiles-manage-console"></a>

If you use the AWS Management Console to create a role for Amazon EC2, the console automatically creates an instance profile and gives it the same name as the role\. When you then use the Amazon EC2 console to launch an instance with an IAM role, you can select a role to associate with the instance\. In the console, the list that's displayed is actually a list of instance profile names\. The console does not create an instance profile for a role that is not associated with Amazon EC2\.

## Managing Instance Profiles using the AWS CLI, Tools for Windows PowerShell, and AWS API<a name="instance-profiles-manage-cli-api"></a>

If you manage your roles from the AWS CLI, Tools for Windows PowerShell, or the AWS API, you create roles and instance profiles as separate actions\. You can give the roles and instance profiles different names, so you have to know the names of your instance profiles as well as the names of roles they contain so that you can choose the correct instance profile when you launch an EC2 instance\. 

**Note**  
An instance profile can contain only one IAM role, although a role can be included in multiple instance profiles\. This limit of one role per instance cannot be increased\. You can remove the existing role and then add a different role to an instance profile\. You must then wait for the change to appear across all of AWS because of [eventual consistency](https://en.wikipedia.org/wiki/Eventual_consistency)\. To force the change, you must [disassociate the instance profile](http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DisassociateIamInstanceProfile.html) and then [associate the instance profile](http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_AssociateIamInstanceProfile.html), or you can stop your instance and then restart it\. 

You can use the following commands to work with instance profiles in an AWS account\.

Create an instance profile
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/create-instance-profile.html](http://docs.aws.amazon.com/cli/latest/reference/iam/create-instance-profile.html)
+ Tools for Windows PowerShell: `[New\-IAMInstanceProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=New-IAMInstanceProfile.html&tocid=New-IAMInstanceProfile)`
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateInstanceProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_CreateInstanceProfile.html) 

Add a role to an instance profile
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/add-role-to-instance-profile.html](http://docs.aws.amazon.com/cli/latest/reference/iam/add-role-to-instance-profile.html) 
+ Tools for Windows PowerShell: `[Add\-IAMRoleToInstanceProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Add-IAMRoleToInstanceProfile.html&tocid=Add-IAMRoleToInstanceProfile)`
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_AddRoleToInstanceProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_AddRoleToInstanceProfile.html) 

List instance profiles
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/list-instance-profiles.html](http://docs.aws.amazon.com/cli/latest/reference/iam/list-instance-profiles.html), [http://docs.aws.amazon.com/cli/latest/reference/iam/list-instance-profiles-for-role.html](http://docs.aws.amazon.com/cli/latest/reference/iam/list-instance-profiles-for-role.html) 
+ Tools for Windows PowerShell: `[Get\-IAMInstanceProfiles](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMInstanceProfiles.html&tocid=Get-IAMInstanceProfiles)`
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListInstanceProfiles.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListInstanceProfiles.html), [http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListInstanceProfilesForRole.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_ListInstanceProfilesForRole.html) 

Get information about an instance profile
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/get-instance-profile.html](http://docs.aws.amazon.com/cli/latest/reference/iam/get-instance-profile.html) 
+ Tools for Windows PowerShell: `[Get\-IAMInstanceProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-IAMInstanceProfile.html&tocid=Get-IAMInstanceProfile)`
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetInstanceProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_GetInstanceProfile.html) 

Remove a role from an instance profile
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/remove-role-from-instance-profile.html](http://docs.aws.amazon.com/cli/latest/reference/iam/remove-role-from-instance-profile.html) 
+ Tools for Windows PowerShell: `[Remove\-IAMRoleFromInstanceProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMRoleFromInstanceProfile.html&tocid=Remove-IAMRoleFromInstanceProfile)`
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveRoleFromInstanceProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_RemoveRoleFromInstanceProfile.html) 

Delete an instance profile
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/iam/delete-instance-profile.html](http://docs.aws.amazon.com/cli/latest/reference/iam/delete-instance-profile.html) 
+ Tools for Windows PowerShell: `[Remove\-IAMInstanceProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Remove-IAMInstanceProfile.html&tocid=Remove-IAMInstanceProfile)`
+ AWS API: [http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteInstanceProfile.html](http://docs.aws.amazon.com/IAM/latest/APIReference/API_DeleteInstanceProfile.html) 

You can also attach a role to an already running EC2 instance by using the following commands\. For more information, see [IAM Roles for Amazon EC2](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html#attach-iam-role)\.

Attach an instance profile with a role to a stopped or running EC2 instance
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/ec2/associate-iam-instance-profile.html](http://docs.aws.amazon.com/cli/latest/reference/ec2/associate-iam-instance-profile.html) 
+ Tools for Windows PowerShell: `[Register\-Ec2IamInstanceProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Register-EC2IamInstanceProfile.html&tocid=Register-EC2IamInstanceProfile)`
+ AWS API: [http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_AssociateIamInstanceProfile.html](http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_AssociateIamInstanceProfile.html) 

Get information about an instance profile attached to an EC2 instance
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/ec2/describe-iam-instance-profile-associations.html](http://docs.aws.amazon.com/cli/latest/reference/ec2/describe-iam-instance-profile-associations.html) 
+ Tools for Windows PowerShell: `[Get\-EC2IamInstanceProfileAssociation](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Get-EC2IamInstanceProfileAssociation.html&tocid=Get-EC2IamInstanceProfileAssociation)`
+ AWS API: [http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeIamInstanceProfileAssociations.html](http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeIamInstanceProfileAssociations.html) 

Detach an instance profile with a role from a stopped or running EC2 instance
+ AWS CLI: [http://docs.aws.amazon.com/cli/latest/reference/ec2/disassociate-iam-instance-profile.html](http://docs.aws.amazon.com/cli/latest/reference/ec2/disassociate-iam-instance-profile.html) 
+ Tools for Windows PowerShell: `[Unregister\-Ec2IamInstanceProfile](http://docs.aws.amazon.com/powershell/latest/reference/Index.html?page=Unregister-EC2IamInstanceProfile.html&tocid=Unregister-EC2IamInstanceProfile)`
+ AWS API: [http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DisassociateIamInstanceProfile.html](http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DisassociateIamInstanceProfile.html) 