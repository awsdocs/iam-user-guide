# Testing IAM policies with the IAM policy simulator<a name="access_policies_testing-policies"></a>

For more information about how and why to use IAM policies, see [Policies and permissions in IAM](access_policies.md)\.

**You can access the IAM Policy Simulator Console at: [https://policysim\.aws\.amazon\.com/](https://policysim.aws.amazon.com/)**

 

With the IAM policy simulator, you can test and troubleshoot identity\-based policies, IAM permissions boundaries, Organizations service control policies, and resource\-based policies\. Here are some common things you can do with the policy simulator:
+ Test policies that are attached to IAM users, groups, or roles in your AWS account\. If more than one policy is attached to the user, group, or role, you can test all the policies, or select individual policies to test\. You can test which actions are allowed or denied by the selected policies for specific resources\.
+ Test and troubleshoot the effect of [permissions boundaries](access_policies_boundaries.md) on IAM entities\. Note: you can only simulate one permissions boundary at a time\.
+ Test policies that are attached to AWS resources, such as Amazon S3 buckets, Amazon SQS queues, Amazon SNS topics, or Amazon S3 Glacier vaults\.
+ If your AWS account is a member of an organization in [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/), then you can test the impact of service control policies \(SCPs\) on your IAM policies and resource policies\.
+ Test new policies that are not yet attached to a user, group, or role by typing or copying them into the simulator\. These are used only in the simulation and are not saved\. Note: you cannot type or copy a resource\-based policy into the simulator\. To use a resource\-based policy in the simulator, you must include the resource in the simulation\. You must also select the check box to include that resource's policy in the simulation\. 
+ Test the policies with selected services, actions, and resources\. For example, you can test to ensure that your policy allows an entity to perform the `ListAllMyBuckets`, `CreateBucket`, and `DeleteBucket` actions in the Amazon S3 service on a specific bucket\.
+ Simulate real\-world scenarios by providing context keys, such as an IP address or date, that are included in `Condition` elements in the policies being tested\. 
+ Identify which specific statement in a policy results in allowing or denying access to a particular resource or action\. 

**Topics**
+ [How the IAM policy simulator works](#policies_policy-simulator-how-it-works)
+ [Permissions required for using the IAM policy simulator](#permissions-required_policy-simulator)
+ [Using the IAM policy simulator \(console\)](#policies_policy-simulator-using)
+ [Using the IAM policy simulator \(AWS CLI and AWS API\)](#policies-simulator-using-api)

## How the IAM policy simulator works<a name="policies_policy-simulator-how-it-works"></a>

The simulator evaluates the policies that you choose and determines the effective permissions for each of the actions that you specify\. The simulator uses the same policy evaluation engine that is used during real requests to AWS services\. But the simulator differs from the live AWS environment in the following ways: 
+ The simulator does not make an actual AWS service request, so you can safely test requests that might make unwanted changes to your live AWS environment\. 
+ Because the simulator does not simulate running the selected actions, it cannot report any response to the simulated request\. The only result returned is whether the requested action would be allowed or denied\. 
+ If you edit a policy inside the simulator, these changes affect only the simulator\. The corresponding policy in your AWS account remains unchanged\.

## Permissions required for using the IAM policy simulator<a name="permissions-required_policy-simulator"></a>

You can use the policy simulator console or the policy simulator API to test policies\. By default, console users can test policies that are not yet attached to a user, group, or role by typing or copying those policies into the simulator\. These policies are used only in the simulation and do not disclose sensitive information\. API users must have permissions to test unattached policies\. You can allow console or API users to test policies that are attached to IAM users, groups, or roles in your AWS account\. To do so, you must provide permission to retrieve those policies\. In order to test resource\-based policies, users must have permission to retrieve the resource's policy\.

For examples of console and API policies that allow a user to simulate policies, see [Example policies: AWS Identity and Access Management \(IAM\)](access_policies_examples.md#policy_library_IAM)\.

### Permissions required for using the policy simulator console<a name="permissions-required_policy-simulator-console"></a>

You can allow users to test policies that are attached to IAM users, groups, or roles in your AWS account\. To do so, you must provide your users with permissions to retrieve those policies\. In order to test resource\-based policies, users must have permission to retrieve the resource's policy\.

To view an example policy that allows using the policy simulator console for policies that are attached to a user, group, or role, see [IAM: Access the policy simulator console](reference_policies_examples_iam_policy-sim-console.md)\. 

To view an example policy that allows using the policy simulator console only for those users with a specific path, see [IAM: Access the policy simulator console based on user path](reference_policies_examples_iam_policy-sim-path-console.md)\.

To create a policy to allow using the policy simulator console for only one type of entity, use the following procedures\.

**To allow console users to simulate policies for users**  
Include the following actions in your policy:
+ `iam:GetGroupPolicy`
+ `iam:GetPolicy`
+ `iam:GetPolicyVersion`
+ `iam:GetUser`
+ `iam:GetUserPolicy`
+ `iam:ListAttachedUserPolicies`
+ `iam:ListGroupsForUser`
+ `iam:ListGroupPolicies`
+ `iam:ListUserPolicies`
+ `iam:ListUsers`

**To allow console users to simulate policies for groups**  
Include the following actions in your policy:
+ `iam:GetGroup`
+ `iam:GetGroupPolicy`
+ `iam:GetPolicy`
+ `iam:GetPolicyVersion`
+ `iam:ListAttachedGroupPolicies`
+ `iam:ListGroupPolicies`
+ `iam:ListGroups`

**To allow console users to simulate policies for roles**  
Include the following actions in your policy:
+ `iam:GetPolicy`
+ `iam:GetPolicyVersion`
+ `iam:GetRole`
+ `iam:GetRolePolicy`
+ `iam:ListAttachedRolePolicies`
+ `iam:ListRolePolicies`
+ `iam:ListRoles`

To test resource\-based policies, users must have permission to retrieve the resource's policy\.

**To allow console users to test resource\-based policies in an Amazon S3 bucket**  
Include the following action in your policy:
+ `s3:GetBucketPolicy`

For example, the following policy uses this action to allow console users to simulate a resource\-based policy in a specific Amazon S3 bucket\.

```
{
        "Version": "2012-10-17",
        "Statement": [
          {
            "Effect": "Allow",
            "Action": "s3:GetBucketPolicy",
            "Resource":"arn:aws:s3:::bucket-name/*"
          }
        ]
      }
```

**To allow console users to test policies for [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/)**  
Include the following actions in your policy:
+ `organizations:DescribePolicy`
+ `organizations:ListPolicies`
+ `organizations:ListPoliciesForTarget`
+ `organizations:ListTargetsForPolicy`

### Permissions required for using the policy simulator API<a name="permissions-required_policy-simulator-api"></a>

The policy simulator API operations [GetContextKeyForCustomPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeyForCustomPolicy.html) and [SimulateCustomPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_SimulateCustomPolicy.html) allow you to test policies that are not yet attached to a user, group, or role\. To test such policies, you pass the policies as strings to the API\. These policies are used only in the simulation and do not disclose sensitive information\. You can also use the API to test policies that are attached to IAM users, groups, or roles in your AWS account\. To do that, you must provide users with permissions to call [GetContextKeyForPrincipalPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeyForPrincipalPolicy.html) and [SimulatePrincipalPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_SimulatePrincipalPolicy.html)\.

To view an example policy that allows using the policy simulator API for attached and unattached policies in the current AWS account, see [IAM: Access the policy simulator API](reference_policies_examples_iam_policy-sim.md)\. 

To create a policy to allow using the policy simulator API for only one type of policy, use the following procedures\.

**To allow API users to simulate policies passed directly to the API as strings**  
Include the following actions in your policy:
+ `iam:GetContextKeysForCustomPolicy`
+ `iam:SimulateCustomPolicy`

**To allow API users to simulate policies attached to IAM users, groups, roles, or resources**  
Include the following actions in your policy:
+ `iam:GetContextKeysForPrincipalPolicy`
+ `iam:SimulatePrincipalPolicy`

For example, to give a user named Bob permission to simulate a policy that is assigned to a user named Alice, give Bob access to the following resource: `arn:aws:iam::777788889999:user/alice`\. 

To view an example policy that allows using the policy simulator API only for those users with a specific path, see [IAM: Access the policy simulator API based on user path](reference_policies_examples_iam_policy-sim-path.md)\.

## Using the IAM policy simulator \(console\)<a name="policies_policy-simulator-using"></a>

By default, users can test policies that are not yet attached to a user, group, or role by typing or copying those policies into the policy simulator console\. These policies are used only in the simulation and do not disclose sensitive information\. 

**To test a policy that is not attached to a user, group, or role \(console\)**

1. Open the IAM policy simulator console at: [https://policysim\.aws\.amazon\.com/](https://policysim.aws.amazon.com/)\.

1. In the **Mode:** menu at the top of the page, choose **New Policy**\.

1. In the **Policy Sandbox**, choose **Create New Policy**\.

1. Type or copy a policy into the simulator, and use the simulator as described in the following steps\.

After you have permission to use the IAM Policy Simulator Console, you can use the simulator to test an IAM user, group, role, or resource policy\.

**To test a policy that is attached to a user, group, or role \(console\)**

1. Open the IAM policy simulator console at [ https://policysim\.aws\.amazon\.com/](https://policysim.aws.amazon.com/)\. 
**Note**  
To sign in to the policy simulator as an IAM user, use your unique sign\-in URL to sign in to the AWS Management Console\. Then go to [https://policysim.aws.amazon.com/](https://policysim.aws.amazon.com/)\. For more information about signing in as an IAM user, see [How IAM users sign in to AWS](id_users_sign-in.md)\.

   The simulator opens in **Existing Policies** mode and lists the IAM users in your account under **Users, Groups, and Roles**\.

1. <a name="polsimstep-selectid"></a>Choose the option that is appropriate to your task:  
****    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html)
**Tip**  
To test a policy that is attached to group, you can launch the IAM policy simulator directly from the [IAM console](https://console.aws.amazon.com/iam/): In the navigation pane, choose **Groups**\. Choose the name of the group that you want to test a policy on, and then choose the **Permissions** tab\. In the **Inline Policies** or **Managed Policies** section, locate the policy that you want to test\. In the **Actions** column for that policy, choose **Simulate Policy**\.  
To test a customer managed policy that is attached to a user: In the navigation pane, choose **Users**\. Choose the name of the user that you want to test a policy on\. Then choose the **Permissions** tab and expand the policy that you want to test\. On the far right, choose **Simulate policy**\. The **IAM Policy Simulator** opens in a new window and displays the selected policy in the **Policies** pane\.

1. \(Optional\) If your account is a member of an organization in [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/), then any service control policies \(SCPs\) that affect the simulated user's account appear in the **Policies** pane\. The **Policies** pane also shows **IAM policies**, **Resource policies** and **Permissions Boundary policies**\. SCPs are JSON policies that specify the maximum permissions for an organization or organizational unit \(OU\)\. The SCP limits permissions for entities in member accounts\. If an SCP blocks a service or action, then no entity in that account can access that service nor perform that action\. This is true even if an administrator explicitly grants permissions to that service or action through an IAM or resource policy\. To remove an SCP from the simulation, clear the check box next to the SCP name\. To view the SCP contents, choose the name of the SCP\.

   If your account is not a member of an organization, then there are no SCPs to simulate\.

1. \(Optional\) You can test a policy that is set as a [permissions boundary](access_policies_boundaries.md) for an IAM entity \(user or role\), but not for groups\. If a permissions boundary policy is currently set for the entity, it appears in the **Policies** pane\. You can set only one permissions boundary for an entity\. To test a different permissions boundary, you can create a custom permissions boundary\. To do this, choose **Create New Policy**\. A new **Policies** pane opens\. In the menu, choose **Custom IAM Permissions Boundary Policy**\. Enter a name for the new policy and type or copy a policy into the space below\. Choose **Apply** to save the policy\. Next, choose **Back** to return to the original **Policies** pane\. Then select the check box next to the permissions boundary you want to use for the simulation\.  

1. <a name="polsimstep-polsubset"></a>\(Optional\) You can test only a subset of policies attached to a user, group, or role\. To do so, in the **Policies** pane clear the check box next to each policy that you want to exclude\.

1. <a name="polsimstep-service"></a>Under **Policy Simulator**, choose **Select service** and then choose the service to test\. Then choose **Select actions** and select one or more actions to test\. Although the menus show the available selections for only one service at a time, all the services and actions that you have selected appear in **Action Settings and Results**\. 

1. \(Optional\) If any of the policies that you choose in [Step 2](#polsimstep-selectid) and [Step 5](#polsimstep-polsubset) include conditions with [AWS *global condition keys*](reference_policies_condition-keys.md), then supply values for those keys\. You can do this by expanding the **Global Settings** section and typing values for the key names displayed there\.
**Warning**  
If you leave the value for a condition key empty, then that key is ignored during the simulation\. In some cases, this results in an error, and the simulation fails to run\. In other cases, the simulation runs, but the results might not be reliable\. In those cases, the simulation does not match the real\-world conditions that include a value for the condition key or variable\.

1. \(Optional\) Each selected action appears in the **Action Settings and Results** list with **Not simulated** shown in the **Permission** column until you actually run the simulation\. Before you run the simulation, you can configure each action with a resource\. To configure individual actions for a specific scenario, choose the arrow to expand the action's row\. If the action supports resource\-level permissions, you can type the [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns) of the specific resource whose access you want to test\. By default, each resource is set to a wildcard \(\*\)\. You can also specify a value for any [condition context keys](reference_policies_actions-resources-contextkeys.html)\. As noted previously, keys with empty values are ignored, which can cause simulation failures or unreliable results\.

   1. Choose the arrow next to the action name to expand each row and configure any additional information required to accurately simulate the action in your scenario\. If the action requires any resource\-level permissions, you can type the [Amazon Resource Name \(ARN\)](reference_identifiers.md#identifiers-arns) of the specific resource that you want to simulate access to\. By default, each resource is set to a wildcard \(\*\)\.

   1. If the action supports resource\-level permissions but does not require them, then you can choose **Add Resource** to select the resource type that you want to add to the simulation\. 

   1. If any of the selected policies include a `Condition` element that references a context key for this action's service, then that key name is displayed under the action\. You can specify the value to be used during the simulation of that action for the specified resource\.
<a name="resource-scenarios"></a>
**Actions that require different groups of resource types**  
Some actions require different resource types under different circumstances\. Each group of resource types is associated with a scenario\. If one of these applies to your simulation, select it and the simulator requires the resource types appropriate for that scenario\. The following list shows each of the supported scenario options and the resources that you must define to run the simulation\.

   Each of the following Amazon EC2 scenarios requires that you specify `instance`, `image`, and `security-group` resources\. If your scenario includes an EBS volume, then you must specify that `volume` as a resource\. If the Amazon EC2 scenario includes a virtual private cloud \(VPC\), then you must supply the `network-interface` resource\. If it includes an IP subnet, then you must specify the `subnet` resource\. For more information on the Amazon EC2 scenario options, see [Supported Platforms](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-supported-platforms.html) in the *Amazon EC2 User Guide*\.
   + **EC2\-Classic\-InstanceStore**

     instance, image, security\-group
   + **EC2\-Classic\-EBS**

     instance, image, security\-group, volume
   + **EC2\-VPC\-InstanceStore**

     instance, image, security\-group, network\-interface
   + **EC2\-VPC\-InstanceStore\-Subnet**

     instance, image, security\-group, network\-interface, subnet
   + **EC2\-VPC\-EBS**

     instance, image, security\-group, network\-interface, volume
   + **EC2\-VPC\-EBS\-Subnet**

     instance, image, security\-group, network\-interface, subnet, volume

1. <a name="polsimstep-respol"></a>\(Optional\) If you want to include a resource\-based policy in your simulation, then you must first select the actions that you want to simulate on that resource in [Step 6](#polsimstep-service)\. Expand the rows for the selected actions, and type the ARN of the resource with a policy that you want to simulate\. Then select **Include Resource Policy** next to the **ARN** text box\. The IAM policy simulator currently supports resource\-based policies from only the following services: Amazon S3 \(resource\-based policies only; ACLs are not currently supported\), Amazon SQS, Amazon SNS, and unlocked S3 Glacier vaults \(locked vaults are not currently supported\)\.

1. Choose **Run Simulation** in the upper\-right corner\.

   The **Permission** column in each row of **Action Settings and Results** displays the result of the simulation of that action on the specified resource\.

1. Choose **Run Simulation** in the upper\-right corner\.

   The **Permission** column in each row of **Action Settings and Results** displays the result of the simulation of that action on the specified resource\.

1. To see which statement in a policy explicitly allowed or denied an action, choose the ***N* matching statement\(s\)** link in the **Permissions** column to expand the row\. Then choose the **Show statement** link\. The **Policies** pane shows the relevant policy with the statement that affected the simulation result highlighted\.
**Note**  
If an action is *implicitly* denied—that is, if the action is denied only because it is not explicitly allowed—the **List** and **Show statement** options are not displayed\.

### Troubleshooting IAM policy simulator console messages<a name="iam-policy-simulator-messages"></a>

The following table lists the informational and warning messages you might encounter when using the IAM policy simulator\. The table also provides steps you can take to resolve them\. 


****  

| Message | Steps to resolve | 
| --- | --- | 
| This policy has been edited\. Changes will not be saved to your account\.  |   **No action required\.**  This message is informational\. If you edit an existing policy in the IAM policy simulator, your change does not affect your AWS account\. The simulator allows you to make changes to policies for testing purposes only\.  | 
| Cannot get the resource policy\. Reason: detailed error message | The simulator is not able to access a requested resource\-based policy\. Ensure that the specified resource ARN is correct and that the user running the simulation has permission to read the resource's policy\. | 
| One or more policies require values in the simulation settings\. The simulation might fail without these values\.  |  This message appears if the policy you are testing contains condition keys or variables but you have not provided any values for these keys or variables in **Simulation Settings**\. To dismiss this message, choose **Simulation Settings**, Then enter a value for each condition key or variable\.  | 
| You have changed policies\. These results are no longer valid\.  |  This message appears if you have changed the selected policy while results are displayed in the **Results** pane\. Results shown in the **Results** pane are not updated dynamically\. To dismiss this message, choose **Run Simulation** again to display new simulation results based on the changes made in the **Policies** pane\.  | 
| The resource you typed for this simulation does not match this service\.  |  This message appears if you have typed an Amazon Resource Name \(ARN\) in the **Simulation Settings** pane that does not match the service that you chose for the current simulation\. For example, this message appears if you specify an ARN for an Amazon DynamoDB resource but you chose Amazon Redshift as the service to simulate\. To dismiss this message, do one of the following:  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_testing-policies.html)  | 
| This action belongs to a service that supports special access control mechanisms in addition to resource\-based policies, such as Amazon S3 ACLs or S3 Glacier vault lock policies\. The policy simulator does not support these mechanisms, so the results can differ from your production environment\.  |   **No action required\.**  This message is informational\. In the current version, the simulator evaluates policies attached to users and groups, and can evaluate resource\-based policies for Amazon S3, Amazon SQS, Amazon SNS, and S3 Glacier\. The policy simulator does not support all access control mechanisms supported by other AWS services\.  | 
| DynamoDB FGAC is currently not supported\.  |   **No action required\.**  This informational message refers to *fine\-grained access control*\. Fine\-grained access control is the ability to use IAM policy conditions to determine who can access individual data items and attributes in DynamoDB tables and indexes\. It also refers to the actions that can be performed on these tables and indexes\. The current version of the IAM policy simulator does not support this type of policy condition\. For more information on DynamoDB fine\-grained access control, see [Fine\-Grained Access Control for DynamoDB](http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/FGAC_DDB.html)\.  | 
| You have policies that do not comply with the policy syntax\. You can use the Policy Validator to review and accept the recommended updates to your policies\.  |  This message appears at the top of the policy list if you have policies that do not comply with the IAM policy grammar\. In order to simulate these policies, follow the instructions at [Validating IAM policy grammar](access_policies_policy-validator.md) to identify and fix these policies\.  | 
|  This policy must be updated to comply with the latest policy syntax rules\.  |  This message is displayed if you have policies that do not comply with the IAM policy grammar\. In order to simulate these policies, follow the instructions at [Validating IAM policy grammar](access_policies_policy-validator.md) to identify and fix these policies\.  | 

## Using the IAM policy simulator \(AWS CLI and AWS API\)<a name="policies-simulator-using-api"></a>

Policy simulator commands typically require calling API operations to do two things:

1. Evaluate the policies and return the list of context keys that they reference\. You need to know what context keys are referenced so that you can supply values for them in the next step\.

1. Simulate the policies, providing a list of actions, resources, and context keys that are used during the simulation\.

For security reasons, the API operations have been broken into two groups:
+ API operations that simulate only policies that are passed directly to the API as strings\. This set includes [GetContextKeysForCustomPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForCustomPolicy.html) and [SimulateCustomPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_SimulateCustomPolicy.html)\.
+ API operations that simulate the policies that are attached to a specified IAM user, group, role, or resource\. Because these API operations can reveal details of permissions assigned to other IAM entities, you should consider restricting access to these API operations\. This set includes [GetContextKeysForPrincipalPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForPrincipalPolicy.html) and [SimulatePrincipalPolicy](https://docs.aws.amazon.com/IAM/latest/APIReference/API_SimulatePrincipalPolicy.html)\. For more information about restricting access to API operations, see [Example policies: AWS Identity and Access Management \(IAM\)](access_policies_examples.md#policy_library_IAM)\.

In both cases, the API operations simulate the effect of one or more policies on a list of actions and resources\. Each action is paired with each resource and the simulation determines whether the policies allow or deny that action for that resource\. You can also provide values for any context keys that your policies reference\. You can get the list of context keys that the policies reference by first calling [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForCustomPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForCustomPolicy.html) or [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForPrincipalPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForPrincipalPolicy.html)\. If you don't provide a value for a context key, the simulation still runs\. But the results might not be reliable because the simulator cannot include that context key in the evaluation\.

**To get the list of context keys \(AWS CLI, AWS API\)**  
Use the following to evaluate a list of policies and return a list of context keys that are used in the policies\.
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/get-context-keys-for-custom-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-context-keys-for-custom-policy.html) and [https://docs.aws.amazon.com/cli/latest/reference/iam/get-context-keys-for-principal-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/get-context-keys-for-principal-policy.html)
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForCustomPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForCustomPolicy.html) and [https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForPrincipalPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_GetContextKeysForPrincipalPolicy.html)

**To simulate IAM policies \(AWS CLI, AWS API\)**  
Use the following to simulate IAM policies to determine a user's effective permissions\.
+ AWS CLI: [https://docs.aws.amazon.com/cli/latest/reference/iam/simulate-custom-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/simulate-custom-policy.html) and [https://docs.aws.amazon.com/cli/latest/reference/iam/simulate-principal-policy.html](https://docs.aws.amazon.com/cli/latest/reference/iam/simulate-principal-policy.html)
+ AWS API: [https://docs.aws.amazon.com/IAM/latest/APIReference/API_SimulateCustomPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_SimulateCustomPolicy.html) and [https://docs.aws.amazon.com/IAM/latest/APIReference/API_SimulatePrincipalPolicy.html](https://docs.aws.amazon.com/IAM/latest/APIReference/API_SimulatePrincipalPolicy.html)