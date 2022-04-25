# Detach an IAM policy from a user using an AWS SDK<a name="example_iam_DetachUserPolicy_section"></a>

The following code examples show how to detach an IAM policy from a user\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Go ]

**SDK for Go V2**  
  

```
package main

import (
	"context"
	"flag"
	"fmt"

	"github.com/aws/aws-sdk-go-v2/config"
	"github.com/aws/aws-sdk-go-v2/service/iam"
)

// IAMDetachRolePolicyAPI defines the interface for the DetachRolePolicy function.
// We use this interface to test the function using a mocked service.
type IAMDetachRolePolicyAPI interface {
	DetachRolePolicy(ctx context.Context,
		params *iam.DetachRolePolicyInput,
		optFns ...func(*iam.Options)) (*iam.DetachRolePolicyOutput, error)
}

// DetachDynamoFullPolicy detaches an Amazon DynamoDB full-access policy from an AWS Identity and Access Management (IAM) role.
// Inputs:
//     c is the context of the method call, which includes the AWS Region.
//     api is the interface that defines the method call.
//     input defines the input arguments to the service call.
// Output:
//     If successful, a DetachRolePolicyOutput object containing the result of the service call and nil.
//     Otherwise, nil and an error from the call to DetachRolePolicy.
func DetachDynamoFullPolicy(c context.Context, api IAMDetachRolePolicyAPI, input *iam.DetachRolePolicyInput) (*iam.DetachRolePolicyOutput, error) {
	return api.DetachRolePolicy(c, input)
}

func main() {
	roleName := flag.String("r", "", "The name of the IAM role")
	flag.Parse()

	if *roleName == "" {
		fmt.Println("You must supply a role name (-r ROLE)")
		return
	}

	cfg, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		panic("configuration error, " + err.Error())
	}

	client := iam.NewFromConfig(cfg)

	policyArn := "arn:aws:iam::aws:policy/AmazonDynamoDBFullAccess"
	input := &iam.DetachRolePolicyInput{
		PolicyArn: &policyArn,
		RoleName:  roleName,
	}

	_, err = DetachDynamoFullPolicy(context.TODO(), client, input)
	if err != nil {
		fmt.Println("Unable to detach DynamoDB full-access role policy from role")
		return
	}
	fmt.Println("Role detached successfully")
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [DetachUserPolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DetachUserPolicy) in *AWS SDK for Go API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def detach_policy(user_name, policy_arn):
    """
    Detaches a policy from a user.

    :param user_name: The name of the user.
    :param policy_arn: The Amazon Resource Name (ARN) of the policy.
    """
    try:
        iam.User(user_name).detach_policy(PolicyArn=policy_arn)
        logger.info("Detached policy %s from user %s.", policy_arn, user_name)
    except ClientError:
        logger.exception(
            "Couldn't detach policy %s from user %s.", policy_arn, user_name)
        raise
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [DetachUserPolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DetachUserPolicy) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
  

```
pub async fn detach_user_policy(
    client: &iamClient,
    user_name: &str,
    policy_arn: &str,
) -> Result<(), iamError> {
    client
        .detach_user_policy()
        .user_name(user_name)
        .policy_arn(policy_arn)
        .send()
        .await?;

    Ok(())
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
+  For API details, see [DetachUserPolicy](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.