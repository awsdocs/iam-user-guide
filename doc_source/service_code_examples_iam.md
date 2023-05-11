# Code examples for IAM using AWS SDKs<a name="service_code_examples_iam"></a>

The following code examples show how to use IAM with an AWS software development kit \(SDK\)\. 

*Actions* are code excerpts that show you how to call individual service functions\.

*Scenarios* are code examples that show you how to accomplish a specific task by calling multiple functions within the same service\.

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.

**Get started**

## Hello IAM<a name="example_iam_Hello_section"></a>

The following code examples show how to get started using IAM\.

------
#### [ \.NET ]

**AWS SDK for \.NET**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
  

```
namespace IAMActions;

public class HelloIAM
{
    static async Task Main(string[] args)
    {
        // Getting started with AWS Identity and Access Management (IAM). List
        // the policies for the account.
        var iamClient = new AmazonIdentityManagementServiceClient();

        var listPoliciesPaginator = iamClient.Paginators.ListPolicies(new ListPoliciesRequest());
        var policies = new List<ManagedPolicy>();

        await foreach (var response in listPoliciesPaginator.Responses)
        {
            policies.AddRange(response.Policies);
        }

        Console.WriteLine("Here are the policies defined for your account:\n");
        policies.ForEach(policy =>
        {
            Console.WriteLine($"Created: {policy.CreateDate}\t{policy.PolicyName}\t{policy.Description}");
        });
    }
}
```
+  For API details, see [ListPolicies](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/ListPolicies) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
package main

import (
	"context"
	"fmt"

	"github.com/aws/aws-sdk-go-v2/aws"
	"github.com/aws/aws-sdk-go-v2/config"
	"github.com/aws/aws-sdk-go-v2/service/iam"
)

// main uses the AWS SDK for Go (v2) to create an AWS Identity and Access Management (IAM)
// client and list up to 10 policies in your account.
// This example uses the default settings specified in your shared credentials
// and config files.
func main() {
	sdkConfig, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		fmt.Println("Couldn't load default configuration. Have you set up your AWS account?")
		fmt.Println(err)
		return
	}
	iamClient := iam.NewFromConfig(sdkConfig)
	const maxPols = 10
	fmt.Printf("Let's list up to %v policies for your account.\n", maxPols)
	result, err := iamClient.ListPolicies(context.TODO(), &iam.ListPoliciesInput{
		MaxItems: aws.Int32(maxPols),
	})
	if err != nil {
		fmt.Printf("Couldn't list policies for your account. Here's why: %v\n", err)
		return
	}
	if len(result.Policies) == 0 {
		fmt.Println("You don't have any policies!")
	} else {
		for _, policy := range result.Policies {
			fmt.Printf("\t%v\n", *policy.PolicyName)
		}
	}
}
```
+  For API details, see [ListPolicies](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListPolicies) in *AWS SDK for Go API Reference*\. 

------
#### [ JavaScript ]

**SDK for JavaScript \(v3\)**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
  

```
import { IAMClient, paginateListPolicies } from "@aws-sdk/client-iam";

const client = new IAMClient({});

export const listLocalPolicies = async () => {
  /**
   * In v3, the clients expose paginateOperationName APIs that are written using async generators so that you can use async iterators in a for await..of loop.
   * https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/index.html#paginators
   */
  const paginator = paginateListPolicies(
    { client, pageSize: 10 },
    // List only customer managed policies.
    { Scope: "Local" }
  );

  console.log("IAM policies defined in your account:");
  let policyCount = 0;
  for await (const page of paginator) {
    if (page.Policies) {
      page.Policies.forEach((p) => {
        console.log(`${p.PolicyName}`);
        policyCount++;
      });
    }
  }
  console.log(`Found ${policyCount} policies.`);
};
```
+  For API details, see [ListPolicies](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listpoliciescommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
From src/bin/hello\.rs\.  

```
use aws_sdk_iam::error::SdkError;
use aws_sdk_iam::operation::list_policies::ListPoliciesError;
use clap::Parser;

const PATH_PREFIX_HELP: &str = "The path prefix for filtering the results.";

#[derive(Debug, clap::Parser)]
#[command(about)]
struct HelloScenarioArgs {
    #[arg(long, default_value="/", help=PATH_PREFIX_HELP)]
    pub path_prefix: String,
}

#[tokio::main]
async fn main() -> Result<(), SdkError<ListPoliciesError>> {
    let sdk_config = aws_config::load_from_env().await;
    let client = aws_sdk_iam::Client::new(&sdk_config);

    let args = HelloScenarioArgs::parse();

    iam_service::list_policies(client, args.path_prefix).await?;

    Ok(())
}
```
From src/iam\-service\-lib\.rs\.  

```
pub async fn list_policies(
    client: iamClient,
    path_prefix: String,
) -> Result<Vec<String>, SdkError<ListPoliciesError>> {
    let mut list_policies = client
        .list_policies()
        .path_prefix(path_prefix)
        .scope(PolicyScopeType::Local)
        .into_paginator()
        .send();

    let mut v = Vec::new();

    while let Some(list_policies_output) = list_policies.next().await {
        match list_policies_output {
            Ok(list_policies) => {
                if let Some(policies) = list_policies.policies() {
                    for policy in policies {
                        let policy_name = policy
                            .policy_name()
                            .unwrap_or("Missing policy name.")
                            .to_string();
                        println!("{}", policy_name);
                        v.push(policy_name);
                    }
                }
            }

            Err(err) => return Err(err),
        }
    }

    Ok(v)
}
```
+  For API details, see [ListPolicies](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

**Contents**
+ [Actions](service_code_examples_iam_actions.md)
  + [Add a user to a group](example_iam_AddUserToGroup_section.md)
  + [Attach a policy to a role](example_iam_AttachRolePolicy_section.md)
  + [Attach a policy to a user](example_iam_AttachUserPolicy_section.md)
  + [Attach an inline policy to a role](example_iam_PutRolePolicy_section.md)
  + [Create a SAML provider](example_iam_CreateSAMLProvider_section.md)
  + [Create a group](example_iam_CreateGroup_section.md)
  + [Create a policy](example_iam_CreatePolicy_section.md)
  + [Create a policy version](example_iam_CreatePolicyVersion_section.md)
  + [Create a role](example_iam_CreateRole_section.md)
  + [Create a service\-linked role](example_iam_CreateServiceLinkedRole_section.md)
  + [Create a user](example_iam_CreateUser_section.md)
  + [Create an access key](example_iam_CreateAccessKey_section.md)
  + [Create an alias for an account](example_iam_CreateAccountAlias_section.md)
  + [Create an inline policy for a group](example_iam_PutGroupPolicy_section.md)
  + [Create an inline policy for a user](example_iam_PutUserPolicy_section.md)
  + [Delete SAML provider](example_iam_DeleteSAMLProvider_section.md)
  + [Delete a group](example_iam_DeleteGroup_section.md)
  + [Delete a group policy](example_iam_DeleteGroupPolicy_section.md)
  + [Delete a policy](example_iam_DeletePolicy_section.md)
  + [Delete a role](example_iam_DeleteRole_section.md)
  + [Delete a role policy](example_iam_DeleteRolePolicy_section.md)
  + [Delete a server certificate](example_iam_DeleteServerCertificate_section.md)
  + [Delete a service\-linked role](example_iam_DeleteServiceLinkedRole_section.md)
  + [Delete a user](example_iam_DeleteUser_section.md)
  + [Delete an access key](example_iam_DeleteAccessKey_section.md)
  + [Delete an account alias](example_iam_DeleteAccountAlias_section.md)
  + [Delete an inline policy from a user](example_iam_DeleteUserPolicy_section.md)
  + [Detach a policy from a role](example_iam_DetachRolePolicy_section.md)
  + [Detach a policy from a user](example_iam_DetachUserPolicy_section.md)
  + [Generate a credential report](example_iam_GenerateCredentialReport_section.md)
  + [Get a credential report](example_iam_GetCredentialReport_section.md)
  + [Get a detailed authorization report for your account](example_iam_GetAccountAuthorizationDetails_section.md)
  + [Get a policy](example_iam_GetPolicy_section.md)
  + [Get a policy version](example_iam_GetPolicyVersion_section.md)
  + [Get a role](example_iam_GetRole_section.md)
  + [Get a server certificate](example_iam_GetServerCertificate_section.md)
  + [Get a service\-linked role's deletion status](example_iam_GetServiceLinkedRoleDeletionStatus_section.md)
  + [Get a summary of account usage](example_iam_GetAccountSummary_section.md)
  + [Get a user](example_iam_GetUser_section.md)
  + [Get data about the last use of an access key](example_iam_GetAccessKeyLastUsed_section.md)
  + [Get the account password policy](example_iam_GetAccountPasswordPolicy_section.md)
  + [List SAML providers](example_iam_ListSAMLProviders_section.md)
  + [List a user's access keys](example_iam_ListAccessKeys_section.md)
  + [List account aliases](example_iam_ListAccountAliases_section.md)
  + [List groups](example_iam_ListGroups_section.md)
  + [List inline policies for a role](example_iam_ListRolePolicies_section.md)
  + [List inline policies for a user](example_iam_ListUserPolicies_section.md)
  + [List policies](example_iam_ListPolicies_section.md)
  + [List policies attached to a role](example_iam_ListAttachedRolePolicies_section.md)
  + [List roles](example_iam_ListRoles_section.md)
  + [List server certificates](example_iam_ListServerCertificates_section.md)
  + [List users](example_iam_ListUsers_section.md)
  + [Remove a user from a group](example_iam_RemoveUserFromGroup_section.md)
  + [Update a server certificate](example_iam_UpdateServerCertificate_section.md)
  + [Update a user](example_iam_UpdateUser_section.md)
  + [Update an access key](example_iam_UpdateAccessKey_section.md)
  + [Upload a server certificate](example_iam_UploadServerCertificate_section.md)
+ [Scenarios](service_code_examples_iam_scenarios.md)
  + [Create a group and add a user](example_iam_Scenario_GroupBasics_section.md)
  + [Create a user and assume a role](example_iam_Scenario_CreateUserAssumeRole_section.md)
  + [Create read\-only and read\-write users](example_iam_Scenario_UserPolicies_section.md)
  + [Manage access keys](example_iam_Scenario_ManageAccessKeys_section.md)
  + [Manage policies](example_iam_Scenario_PolicyManagement_section.md)
  + [Manage roles](example_iam_Scenario_RoleManagement_section.md)
  + [Manage your account](example_iam_Scenario_AccountManagement_section.md)
  + [Roll back a policy version](example_iam_Scenario_RollbackPolicyVersion_section.md)