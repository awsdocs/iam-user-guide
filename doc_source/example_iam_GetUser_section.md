# Get an IAM user using an AWS SDK<a name="example_iam_GetUser_section"></a>

The following code example shows how to get an IAM user\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Go ]

**SDK for Go V2**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
// UserWrapper encapsulates AWS Identity and Access Management (IAM) user actions
// used in the examples.
// It contains an IAM service client that is used to perform user actions.
type UserWrapper struct {
	IamClient *iam.Client
}



// GetUser gets data about a user.
func (wrapper UserWrapper) GetUser(userName string) (*types.User, error) {
	var user *types.User
	result, err := wrapper.IamClient.GetUser(context.TODO(), &iam.GetUserInput{
		UserName: aws.String(userName),
	})
	if err != nil {
		var apiError smithy.APIError
		if errors.As(err, &apiError) {
			switch apiError.(type) {
			case *types.NoSuchEntityException:
				log.Printf("User %v does not exist.\n", userName)
				err = nil
			default:
				log.Printf("Couldn't get user %v. Here's why: %v\n", userName, err)
			}
		}
	} else {
		user = result.User
	}
	return user, err
}
```
+  For API details, see [GetUser](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.GetUser) in *AWS SDK for Go API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.