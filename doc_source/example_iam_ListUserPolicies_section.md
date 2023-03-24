# List inline IAM policies for a user using an AWS SDK<a name="example_iam_ListUserPolicies_section"></a>

The following code example shows how to list inline IAM policies for a user\. 

**Warning**  
To avoid security risks, don't use IAM users for authentication when developing purpose\-built software or working with real data\. Instead, use federation with an identity provider such as [AWS IAM Identity Center \(successor to AWS Single Sign\-On\)](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Go ]

**SDK for Go V2**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
// UserWrapper encapsulates user actions used in the examples.
// It contains an IAM service client that is used to perform user actions.
type UserWrapper struct {
	IamClient *iam.Client
}



// ListUserPolicies lists the inline policies for the specified user.
func (wrapper UserWrapper) ListUserPolicies(userName string) ([]string, error) {
	var policies []string
	result, err := wrapper.IamClient.ListUserPolicies(context.TODO(), &iam.ListUserPoliciesInput{
		UserName: aws.String(userName),
	})
	if err != nil {
		log.Printf("Couldn't list policies for user %v. Here's why: %v\n", userName, err)
	} else {
		policies = result.PolicyNames
	}
	return policies, err
}
```
+  For API details, see [ListUserPolicies](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListUserPolicies) in *AWS SDK for Go API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.