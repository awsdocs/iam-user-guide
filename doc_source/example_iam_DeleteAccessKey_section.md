# Delete an IAM access key using an AWS SDK<a name="example_iam_DeleteAccessKey_section"></a>

The following code examples show how to delete an IAM access key\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
  

```
        /// <summary>
        /// Delete the user, and other resources created for this example.
        /// </summary>
        /// <param name="client">The initialized client object.</param>
        /// <param name=accessKeyId">The Id of the user's access key.</param>"
        /// <param name="userName">The user name of the user to delete.</param>
        /// <param name="policyName">The name of the policy to delete.</param>
        /// <param name="policyArn">The Amazon Resource Name ARN of the Policy to delete.</param>
        /// <param name="roleName">The name of the role that will be deleted.</param>
        public static async Task DeleteResourcesAsync(
            AmazonIdentityManagementServiceClient client,
            string accessKeyId,
            string userName,
            string policyArn,
            string roleName)
        {
            var detachPolicyResponse = await client.DetachRolePolicyAsync(new DetachRolePolicyRequest
            {
                PolicyArn = policyArn,
                RoleName = roleName,
            });

            var delPolicyResponse = await client.DeletePolicyAsync(new DeletePolicyRequest
            {
                PolicyArn = policyArn,
            });

            var delRoleResponse = await client.DeleteRoleAsync(new DeleteRoleRequest
            {
                RoleName = roleName,
            });

            var delAccessKey = await client.DeleteAccessKeyAsync(new DeleteAccessKeyRequest
            {
                AccessKeyId = accessKeyId,
                UserName = userName,
            });

            var delUserResponse = await client.DeleteUserAsync(new DeleteUserRequest
            {
                UserName = userName,
            });

        }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
+  For API details, see [DeleteAccessKey](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DeleteAccessKey) in *AWS SDK for \.NET API Reference*\. 

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

// IAMDeleteAccessKeyAPI defines the interface for the DeleteAccessKey function.
// We use this interface to test the function using a mocked service.
type IAMDeleteAccessKeyAPI interface {
	DeleteAccessKey(ctx context.Context,
		params *iam.DeleteAccessKeyInput,
		optFns ...func(*iam.Options)) (*iam.DeleteAccessKeyOutput, error)
}

// RemoveAccessKey deletes an AWS Identity and Access Management (IAM) access key.
// Inputs:
//     c is the context of the method call, which includes the AWS Region.
//     api is the interface that defines the method call.
//     input defines the input arguments to the service call.
// Output:
//     If successful, a DeleteAccessKeyOutput object containing the result of the service call and nil.
//     Otherwise, nil and an error from the call to DeleteAccessKey.
func RemoveAccessKey(c context.Context, api IAMDeleteAccessKeyAPI, input *iam.DeleteAccessKeyInput) (*iam.DeleteAccessKeyOutput, error) {
	return api.DeleteAccessKey(c, input)
}

func main() {
	keyID := flag.String("k", "", "The ID of the access key")
	userName := flag.String("u", "", "The name of the user")
	flag.Parse()

	if *keyID == "" || *userName == "" {
		fmt.Println("You must supply the key ID and user name (-k KEY-ID -u USER-NAME")
		return
	}

	cfg, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		panic("configuration error, " + err.Error())
	}

	client := iam.NewFromConfig(cfg)

	input := &iam.DeleteAccessKeyInput{
		AccessKeyId: keyID,
		UserName:    userName,
	}

	_, err = RemoveAccessKey(context.TODO(), client, input)
	if err != nil {
		fmt.Println("Error", err)
		return
	}

	fmt.Println("Deleted key with ID " + *keyID + " from user " + *userName)
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [DeleteAccessKey](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DeleteAccessKey) in *AWS SDK for Go API Reference*\. 

------
#### [ Java ]

**SDK for Java 2\.x**  
  

```
    public static void deleteKey(IamClient iam ,String username, String accessKey ) {

        try {
            DeleteAccessKeyRequest request = DeleteAccessKeyRequest.builder()
                    .accessKeyId(accessKey)
                    .userName(username)
                    .build();

            iam.deleteAccessKey(request);
            System.out.println("Successfully deleted access key " + accessKey +
                " from user " + username);

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/iam#readme)\. 
+  For API details, see [DeleteAccessKey](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DeleteAccessKey) in *AWS SDK for Java 2\.x API Reference*\. 

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
Delete the access key\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { DeleteAccessKeyCommand } from "@aws-sdk/client-iam";

// Set the parameters.
export const params = {
  AccessKeyId: "ACCESS_KEY_ID", // ACCESS_KEY_ID
  UserName: "USER_NAME", // USER_NAME
};

export const run = async () => {
  try {
    const data = await iamClient.send(new DeleteAccessKeyCommand(params));
    console.log("Success", data);
    return data;
  } catch (err) {
    console.log("Error", err);
  }
};
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/iam-examples-managing-access-keys.html#iam-examples-managing-access-keys-deleting)\. 
+  For API details, see [DeleteAccessKey](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/deleteaccesskeycommand.html) in *AWS SDK for JavaScript API Reference*\. 

**SDK for JavaScript V2**  
  

```
// Load the AWS SDK for Node.js
var AWS = require('aws-sdk');
// Set the region 
AWS.config.update({region: 'REGION'});

// Create the IAM service object
var iam = new AWS.IAM({apiVersion: '2010-05-08'});

var params = {
  AccessKeyId: 'ACCESS_KEY_ID',
  UserName: 'USER_NAME'
};

iam.deleteAccessKey(params, function(err, data) {
  if (err) {
    console.log("Error", err);
  } else {
    console.log("Success", data);
  }
});
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascript/example_code/iam#code-examples)\. 
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/iam-examples-managing-access-keys.html#iam-examples-managing-access-keys-deleting)\. 
+  For API details, see [DeleteAccessKey](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/iam-2010-05-08/DeleteAccessKey) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
  

```
suspend fun deleteKey(userNameVal: String, accessKey: String) {

    val request = DeleteAccessKeyRequest {
        accessKeyId =accessKey
        userName = userNameVal
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        iamClient.deleteAccessKey(request)
        println( "Successfully deleted access key $accessKey from $userNameVal")
    }
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
+  For API details, see [DeleteAccessKey](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def delete_key(user_name, key_id):
    """
    Deletes a user's access key.

    :param user_name: The user that owns the key.
    :param key_id: The ID of the key to delete.
    """

    try:
        key = iam.AccessKey(user_name, key_id)
        key.delete()
        logger.info(
            "Deleted access key %s for %s.", key.id, key.user_name)
    except ClientError:
        logger.exception("Couldn't delete key %s for %s", key_id, user_name)
        raise
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [DeleteAccessKey](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DeleteAccessKey) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
  

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
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
+  For API details, see [DeleteAccessKey](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeleteAccessKey) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
  

```
pub async fn delete_access_key(
    client: &iamClient,
    user: &User,
    key: &AccessKey,
) -> Result<(), iamError> {
    loop {
        match client
            .delete_access_key()
            .user_name(user.user_name.as_ref().unwrap())
            .access_key_id(key.access_key_id.as_ref().unwrap())
            .send()
            .await
        {
            Ok(_) => {
                break;
            }
            Err(e) => {
                println!("Can't delete the access key: {:?}", e);
                sleep(Duration::from_secs(2)).await;
            }
        }
    }
    Ok(())
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
+  For API details, see [DeleteAccessKey](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.