# List IAM users using an AWS SDK<a name="example_iam_ListUsers_section"></a>

The following code examples show how to list IAM users\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
  

```
using System;
using Amazon.IdentityManagement;
using Amazon.IdentityManagement.Model;

var client = new AmazonIdentityManagementServiceClient();
var request = new ListUsersRequest
{
    MaxItems = 10,
};
var response = await client.ListUsersAsync(request);

do
{
    response.Users.ForEach(user =>
    {
        Console.WriteLine($"{user.UserName} created on {user.CreateDate}.");
        Console.WriteLine($"ARN: {user.Arn}\n");
    });

    request.Marker = response.Marker;
    response = await client.ListUsersAsync(request);
} while (response.IsTruncated);
```
+  For API details, see [ListUsers](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/ListUsers) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
	// ListUsers

	fmt.Println("➡️ List users")

	userListResult, err := service.ListUsers(context.Background(), &iam.ListUsersInput{})
	if err != nil {
		panic("Couldn't list users: " + err.Error())
	}
	for _, userResult := range userListResult.Users {
		fmt.Printf("%s\t%s\n", *userResult.UserName, *userResult.Arn)
	}
```
+  For API details, see [ListUsers](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListUsers) in *AWS SDK for Go API Reference*\. 

------
#### [ Java ]

**SDK for Java 2\.x**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/iam#readme)\. 
  

```
    public static void listAllUsers(IamClient iam ) {

        try {

            boolean done = false;
            String newMarker = null;

            while(!done) {
                ListUsersResponse response;
                if (newMarker == null) {
                    ListUsersRequest request = ListUsersRequest.builder().build();
                    response = iam.listUsers(request);
                } else {
                    ListUsersRequest request = ListUsersRequest.builder()
                        .marker(newMarker)
                        .build();

                    response = iam.listUsers(request);
                }

                for(User user : response.users()) {
                    System.out.format("\n Retrieved user %s", user.userName());
                    AttachedPermissionsBoundary permissionsBoundary = user.permissionsBoundary();
                    if (permissionsBoundary != null)
                        System.out.format("\n Permissions boundary details %s", permissionsBoundary.permissionsBoundaryTypeAsString());
                }

                if(!response.isTruncated()) {
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
+  For API details, see [ListUsers](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/ListUsers) in *AWS SDK for Java 2\.x API Reference*\. 

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
List the users\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { ListUsersCommand } from "@aws-sdk/client-iam";

// Set the parameters.
export const params = { MaxItems: 10 };

export const run = async () => {
  try {
    const data = await iamClient.send(new ListUsersCommand(params));
    return data;
    const users = data.Users || [];
    users.forEach(function (user) {
      console.log("User " + user.UserName + " created", user.CreateDate);
    });
  } catch (err) {
    console.log("Error", err);
  }
};
run();
```
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/iam-examples-managing-users.html#iam-examples-managing-users-listing-users)\. 
+  For API details, see [ListUsers](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listuserscommand.html) in *AWS SDK for JavaScript API Reference*\. 

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
  MaxItems: 10
};

iam.listUsers(params, function(err, data) {
  if (err) {
    console.log("Error", err);
  } else {
    var users = data.Users || [];
    users.forEach(function(user) {
      console.log("User " + user.UserName + " created", user.CreateDate);
    });
  }
});
```
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/iam-examples-managing-users.html#iam-examples-managing-users-listing-users)\. 
+  For API details, see [ListUsers](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/iam-2010-05-08/ListUsers) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
  

```
suspend fun listAllUsers() {

        IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
            val response = iamClient.listUsers(ListUsersRequest { })
            response.users?.forEach { user ->
                println("Retrieved user ${user.userName}")
            }
        }
 }
```
+  For API details, see [ListUsers](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
  

```
$uuid = uniqid();
$service = new IamService();

    public function listUsers($pathPrefix = "", $marker = "", $maxItems = 0)
    {
        $listUsersArguments = [];
        if ($pathPrefix) {
            $listUsersArguments["PathPrefix"] = $pathPrefix;
        }
        if ($marker) {
            $listUsersArguments["Marker"] = $marker;
        }
        if ($maxItems) {
            $listUsersArguments["MaxItems"] = $maxItems;
        }

        return $this->iamClient->listUsers($listUsersArguments);
    }
```
+  For API details, see [ListUsers](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/ListUsers) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
  

```
def list_users():
    """
    Lists the users in the current account.

    :return: The list of users.
    """
    try:
        users = list(iam.users.all())
        logger.info("Got %s users.", len(users))
    except ClientError:
        logger.exception("Couldn't get users.")
        raise
    else:
        return users
```
+  For API details, see [ListUsers](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/ListUsers) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
  

```
  # Lists up to a specified number of users in the account.
  #
  # @param count [Integer] The maximum number of users to list.
  def list_users(count)
    @iam_resource.users.limit(count).each do |user|
      puts("\t#{user.name}")
    end
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't list users for the account. Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  end
```
+  For API details, see [ListUsers](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/ListUsers) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
  

```
pub async fn list_users(
    client: &iamClient,
    path_prefix: Option<String>,
    marker: Option<String>,
    max_items: Option<i32>,
) -> Result<ListUsersOutput, SdkError<ListUsersError>> {
    let response = client
        .list_users()
        .set_path_prefix(path_prefix)
        .set_marker(marker)
        .set_max_items(max_items)
        .send()
        .await?;
    Ok(response)
}
```
+  For API details, see [ListUsers](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.