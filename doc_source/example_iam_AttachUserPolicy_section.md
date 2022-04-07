# Attach an IAM policy to a user using an AWS SDK<a name="example_iam_AttachUserPolicy_section"></a>

The following code examples show how to attach an IAM policy to a user\.

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

// IAMAttachRolePolicyAPI defines the interface for the AttachRolePolicy function.
// We use this interface to test the function using a mocked service.
type IAMAttachRolePolicyAPI interface {
	AttachRolePolicy(ctx context.Context,
		params *iam.AttachRolePolicyInput,
		optFns ...func(*iam.Options)) (*iam.AttachRolePolicyOutput, error)
}

// AttachDynamoFullPolicy attaches an Amazon DynamoDB full-access policy to an AWS Identity and Access Management (IAM) role.
// Inputs:
//     c is the context of the method call, which includes the AWS Region.
//     api is the interface that defines the method call.
//     input defines the input arguments to the service call.
// Output:
//     If successful, an AttachRolePolicyOutput object containing the result of the service call and nil.
//     Otherwise, nil and an error from the call to AttachRolePolicy.
func AttachDynamoFullPolicy(c context.Context, api IAMAttachRolePolicyAPI, input *iam.AttachRolePolicyInput) (*iam.AttachRolePolicyOutput, error) {
	return api.AttachRolePolicy(c, input)
}

func main() {
	roleName := flag.String("r", "", "The name of the IAM role")
	policyName := flag.String("p", "", "The name of the policy to attach to the role")
	flag.Parse()

	if *roleName == "" || *policyName == "" {
		fmt.Println("You must supply a role and policy name (-r ROLE -p POLICY)")
		return
	}

	cfg, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		panic("configuration error, " + err.Error())
	}

	client := iam.NewFromConfig(cfg)

	policyArn := "arn:aws:iam::aws:policy/" + *policyName

	input := &iam.AttachRolePolicyInput{
		PolicyArn: &policyArn,
		RoleName:  roleName,
	}

	_, err = AttachDynamoFullPolicy(context.TODO(), client, input)
	if err != nil {
		fmt.Println("Unable to attach policy " + *policyName + " to role " + *roleName)
		return
	}

	fmt.Println("Policy " + *policyName + " attached to role " + *roleName)
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [AttachUserPolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.AttachUserPolicy) in *AWS SDK for Go API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def attach_policy(user_name, policy_arn):
    """
    Attaches a policy to a user.

    :param user_name: The name of the user.
    :param policy_arn: The Amazon Resource Name (ARN) of the policy.
    """
    try:
        iam.User(user_name).attach_policy(PolicyArn=policy_arn)
        logger.info("Attached policy %s to user %s.", policy_arn, user_name)
    except ClientError:
        logger.exception("Couldn't attach policy %s to user %s.", policy_arn, user_name)
        raise
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [AttachUserPolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/AttachUserPolicy) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.