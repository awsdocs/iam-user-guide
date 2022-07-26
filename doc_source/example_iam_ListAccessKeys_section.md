# List a user's IAM access keys using an AWS SDK<a name="example_iam_ListAccessKeys_section"></a>

The following code examples show how to list a user's IAM access keys\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Go ]

**SDK for Go V2**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
package main

import (
	"context"
	"flag"
	"fmt"

	"github.com/aws/aws-sdk-go-v2/aws"
	"github.com/aws/aws-sdk-go-v2/config"
	"github.com/aws/aws-sdk-go-v2/service/iam"
)

// IAMListAccessKeysAPI defines the interface for the ListAccessKeys function.
// We use this interface to test the function using a mocked service.
type IAMListAccessKeysAPI interface {
	ListAccessKeys(ctx context.Context,
		params *iam.ListAccessKeysInput,
		optFns ...func(*iam.Options)) (*iam.ListAccessKeysOutput, error)
}

//  GetAccessKeys retrieves up to the AWS Identity and Access Management (IAM) access keys for a user.
// Inputs:
//     c is the context of the method call, which includes the AWS Region.
//     api is the interface that defines the method call.
//     input defines the input arguments to the service call.
// Output:
//     If successful, a ListAccessKeysOutput object containing the result of the service call and nil.
//     Otherwise, nil and an error from the call to ListAccessKeys.
func GetAccessKeys(c context.Context, api IAMListAccessKeysAPI, input *iam.ListAccessKeysInput) (*iam.ListAccessKeysOutput, error) {
	return api.ListAccessKeys(c, input)
}

func main() {
	maxItems := flag.Int("m", 10, "The maximum number of access keys to show")
	userName := flag.String("u", "", "The name of the user")
	flag.Parse()

	if *userName == "" {
		fmt.Println("You must supply the name of a user (-u USER)")
		return
	}

	if *maxItems < 0 {
		*maxItems = 10
	}

	cfg, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		panic("configuration error, " + err.Error())
	}

	client := iam.NewFromConfig(cfg)

	input := &iam.ListAccessKeysInput{
		MaxItems: aws.Int32(int32(*maxItems)),
		UserName: userName,
	}

	result, err := GetAccessKeys(context.TODO(), client, input)
	if err != nil {
		fmt.Println("Got an error retrieving user access keys:")
		fmt.Println(err)
		return
	}

	for _, key := range result.AccessKeyMetadata {
		fmt.Println("Status for access key " + *key.AccessKeyId + ": " + string(key.Status))
	}
}
```
+  For API details, see [ListAccessKeys](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListAccessKeys) in *AWS SDK for Go API Reference*\. 

------
#### [ Java ]

**SDK for Java 2\.x**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/iam#readme)\. 
  

```
    public static void listKeys( IamClient iam,String userName ){

        try {
            boolean done = false;
            String newMarker = null;

            while (!done) {
                ListAccessKeysResponse response;

                if(newMarker == null) {
                    ListAccessKeysRequest request = ListAccessKeysRequest.builder()
                    .userName(userName)
                    .build();

                    response = iam.listAccessKeys(request);

                } else {
                    ListAccessKeysRequest request = ListAccessKeysRequest.builder()
                        .userName(userName)
                        .marker(newMarker)
                        .build();

                    response = iam.listAccessKeys(request);
                }

                for (AccessKeyMetadata metadata : response.accessKeyMetadata()) {
                    System.out.format("Retrieved access key %s", metadata.accessKeyId());
            }

            if (!response.isTruncated()) {
                done = true;
            } else {
                newMarker = response.marker();
            }
        }

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }
```
+  For API details, see [ListAccessKeys](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/ListAccessKeys) in *AWS SDK for Java 2\.x API Reference*\. 

------
#### [ JavaScript ]

**SDK for JavaScript V3**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
Create the client\.  

```
import { IAMClient } from "@aws-sdk/client-iam";
// Set the AWS Region.
const REGION = "REGION"; // For example, "us-east-1".
// Create an IAM service client object.
const iamClient = new IAMClient({ region: REGION });
export { iamClient };
```
List the access keys\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { ListAccessKeysCommand } from "@aws-sdk/client-iam";

// Set the parameters.
export const params = {
  MaxItems: 5,
  UserName: "IAM_USER_NAME", //IAM_USER_NAME
};

export const run = async () => {
  try {
    const data = await iamClient.send(new ListAccessKeysCommand(params));
    console.log("Success", data);
    return data;
  } catch (err) {
    console.log("Error", err);
  }
};
run();
```
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/iam-examples-managing-access-keys.html#iam-examples-managing-access-keys-listing)\. 
+  For API details, see [ListAccessKeys](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listaccesskeyscommand.html) in *AWS SDK for JavaScript API Reference*\. 

**SDK for JavaScript V2**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascript/example_code/iam#code-examples)\. 
  

```
// Load the AWS SDK for Node.js
var AWS = require('aws-sdk');
// Set the region 
AWS.config.update({region: 'REGION'});

// Create the IAM service object
var iam = new AWS.IAM({apiVersion: '2010-05-08'});

var params = {
  MaxItems: 5,
  UserName: 'IAM_USER_NAME'
};

iam.listAccessKeys(params, function(err, data) {
  if (err) {
    console.log("Error", err);
  } else {
    console.log("Success", data);
  }
});
```
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/iam-examples-managing-access-keys.html#iiam-examples-managing-access-keys-listing)\. 
+  For API details, see [ListAccessKeys](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/iam-2010-05-08/ListAccessKeys) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
  

```
suspend fun listKeys(userNameVal: String?) {

      val request = ListAccessKeysRequest {
          userName = userNameVal
      }
      IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        val response = iamClient.listAccessKeys(request)
            response.accessKeyMetadata?.forEach { md ->
                println("Retrieved access key ${md.accessKeyId}")
            }
      }
}
```
+  For API details, see [ListAccessKeys](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
  

```
def list_keys(user_name):
    """
    Lists the keys owned by the specified user.

    :param user_name: The name of the user.
    :return: The list of keys owned by the user.
    """
    try:
        keys = list(iam.User(user_name).access_keys.all())
        logger.info("Got %s access keys for %s.", len(keys), user_name)
    except ClientError:
        logger.exception("Couldn't get access keys for %s.", user_name)
        raise
    else:
        return keys
```
+  For API details, see [ListAccessKeys](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/ListAccessKeys) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
  

```
  # Deletes a user. If the user has inline policies or access keys, they are deleted
  # before the user is deleted.
  #
  # @param user [Aws::IAM::User] The user to delete.
  def delete_user(user)
    user.policies.each do |policy|
      name = policy.name
      policy.delete
      puts("Deleted user policy #{name}.")
    end
    user.access_keys.each do |key|
      key.delete
      puts("Deleted access key for user #{user.name}.")
    end
    name = user.name
    user.delete
    puts("Deleted user #{name}.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't detach policies and delete user #{user.name}. Here's why:")
    puts("\t#{e.code}: #{e.message}")
  end
```
+  For API details, see [ListAccessKeys](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/ListAccessKeys) in *AWS SDK for Ruby API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.