# Create an IAM access key using an AWS SDK<a name="example_iam_CreateAccessKey_section"></a>

The following code examples show how to create an IAM access key\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
  

```
        /// <summary>
        /// Create a new AccessKey for the user.
        /// </summary>
        /// <param name="client">The initialized IAM client object.</param>
        /// <param name="userName">The name of the user for whom to create the key.</param>
        /// <returns>A new IAM access key for the user.</returns>
        public static async Task<AccessKey> CreateAccessKeyAsync(
            AmazonIdentityManagementServiceClient client,
            string userName)
        {
            var request = new CreateAccessKeyRequest
            {
                UserName = userName,
            };

            var response = await client.CreateAccessKeyAsync(request);

            if (response.AccessKey is not null)
            {
                Console.WriteLine($"Successfully created Access Key for {userName}.");
            }

            return response.AccessKey;
        }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
+  For API details, see [CreateAccessKey](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/CreateAccessKey) in *AWS SDK for \.NET API Reference*\. 

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

// IMACreateAccessKeyAPI defines the interface for the CreateAccessKey function.
// We use this interface to test the function using a mocked service.
type IAMCreateAccessKeyAPI interface {
	CreateAccessKey(ctx context.Context,
		params *iam.CreateAccessKeyInput,
		optFns ...func(*iam.Options)) (*iam.CreateAccessKeyOutput, error)
}

// MakeAccessKey creates a new AWS Identity and Access Management (IAM) access key for a user.
// Inputs:
//     c is the context of the method call, which includes the AWS Region.
//     api is the interface that defines the method call.
//     input defines the input arguments to the service call.
// Output:
//     If successful, a CreateAccessKeyOutput object containing the result of the service call and nil.
//     Otherwise, nil and an error from the call to CreateAccessKey.
func MakeAccessKey(c context.Context, api IAMCreateAccessKeyAPI, input *iam.CreateAccessKeyInput) (*iam.CreateAccessKeyOutput, error) {
	return api.CreateAccessKey(c, input)
}

func main() {
	userName := flag.String("u", "", "The name of the user")
	flag.Parse()

	if *userName == "" {
		fmt.Println("You must supply a user name (-u USER)")
		return
	}

	cfg, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		panic("configuration error, " + err.Error())
	}

	client := iam.NewFromConfig(cfg)

	input := &iam.CreateAccessKeyInput{
		UserName: userName,
	}

	result, err := MakeAccessKey(context.TODO(), client, input)
	if err != nil {
		fmt.Println("Got an error creating a new access key")
		fmt.Println(err)
		return
	}

	fmt.Println("Created new access key with ID: " + *result.AccessKey.AccessKeyId + " and secret key: " + *result.AccessKey.SecretAccessKey)
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [CreateAccessKey](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.CreateAccessKey) in *AWS SDK for Go API Reference*\. 

------
#### [ Java ]

**SDK for Java 2\.x**  
  

```
    public static String createIAMAccessKey(IamClient iam,String user) {

        try {
            CreateAccessKeyRequest request = CreateAccessKeyRequest.builder()
                .userName(user).build();

            CreateAccessKeyResponse response = iam.createAccessKey(request);
           String keyId = response.accessKey().accessKeyId();
           return keyId;

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
        return "";
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/iam#readme)\. 
+  For API details, see [CreateAccessKey](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/CreateAccessKey) in *AWS SDK for Java 2\.x API Reference*\. 

------
#### [ JavaScript ]

**SDK for JavaScript V3**  
Create the client\.  

```
import { IAMClient } from "@aws-sdk/client-iam";
// Set the AWS Region.
const REGION = "REGION"; // For example, "us-east-1".
// Create an IAM service client object.
const iamClient = new IAMClient({ region: REGION });
export { iamClient };
```
Create the access key\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { CreateAccessKeyCommand } from "@aws-sdk/client-iam";

// Set the parameters.
export const params = {UserName: "IAM_USER_NAME"}; //IAM_USER_NAME

export const run = async () => {
  try {
    const data = await iamClient.send(new CreateAccessKeyCommand(params));
    console.log("Success", data);
    return data;
  } catch (err) {
    console.log("Error", err);
  }
};
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/iam-examples-managing-access-keys.html#iam-examples-managing-access-keys-creating)\. 
+  For API details, see [CreateAccessKey](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/createaccesskeycommand.html) in *AWS SDK for JavaScript API Reference*\. 

**SDK for JavaScript V2**  
  

```
// Load the AWS SDK for Node.js
var AWS = require('aws-sdk');
// Set the region 
AWS.config.update({region: 'REGION'});

// Create the IAM service object
var iam = new AWS.IAM({apiVersion: '2010-05-08'});

iam.createAccessKey({UserName: 'IAM_USER_NAME'}, function(err, data) {
  if (err) {
    console.log("Error", err);
  } else {
    console.log("Success", data.AccessKey);
  }
});
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascript/example_code/iam#code-examples)\. 
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/iam-examples-managing-access-keys.html#iam-examples-managing-access-keys-creating)\. 
+  For API details, see [CreateAccessKey](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/iam-2010-05-08/CreateAccessKey) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
  

```
suspend  fun createIAMAccessKey(user: String?): String {

    val request = CreateAccessKeyRequest {
        userName = user
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        val response = iamClient.createAccessKey(request)
        return response.accessKey?.accessKeyId.toString()
     }
 }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
+  For API details, see [CreateAccessKey](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def create_key(user_name):
    """
    Creates an access key for the specified user. Each user can have a
    maximum of two keys.

    :param user_name: The name of the user.
    :return: The created access key.
    """
    try:
        key_pair = iam.User(user_name).create_access_key_pair()
        logger.info(
            "Created access key pair for %s. Key ID is %s.",
            key_pair.user_name, key_pair.id)
    except ClientError:
        logger.exception("Couldn't create access key pair for %s.", user_name)
        raise
    else:
        return key_pair
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [CreateAccessKey](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/CreateAccessKey) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
  

```
  # Creates an access key for a user.
  #
  # @param user [Aws::IAM::User] The user that owns the key.
  # @return [Aws::IAM::AccessKeyPair] The newly created access key.
  def create_access_key_pair(user)
    user_key = user.create_access_key_pair
    puts("Created access key pair for user.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't create access keys for user #{user.name}.")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    user_key
  end
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
+  For API details, see [CreateAccessKey](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/CreateAccessKey) in *AWS SDK for Ruby API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.