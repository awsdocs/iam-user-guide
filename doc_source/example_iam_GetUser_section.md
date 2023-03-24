# Get an IAM user using an AWS SDK<a name="example_iam_GetUser_section"></a>

The following code examples show how to get an IAM user\. 

**Warning**  
To avoid security risks, don't use IAM users for authentication when developing purpose\-built software or working with real data\. Instead, use federation with an identity provider such as [AWS IAM Identity Center \(successor to AWS Single Sign\-On\)](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
  

```
    /// <summary>
    /// Get information about an IAM user.
    /// </summary>
    /// <param name="userName">The username of the user.</param>
    /// <returns>An IAM user object.</returns>
    public async Task<User> GetUserAsync(string userName)
    {
        var response = await _IAMService.GetUserAsync(new GetUserRequest { UserName = userName });
        return response.User;
    }
```
+  For API details, see [GetUser](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/GetUser) in *AWS SDK for \.NET API Reference*\. 

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