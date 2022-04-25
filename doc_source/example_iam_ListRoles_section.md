# List IAM roles using an AWS SDK<a name="example_iam_ListRoles_section"></a>

The following code examples show how to list IAM roles\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
  

```
using System;
using Amazon.IdentityManagement;
using Amazon.IdentityManagement.Model;

var client = new AmazonIdentityManagementServiceClient();

// Without the MaxItems value, the ListRolesAsync method will
// return information for up to 100 roles. If there are more
// than the MaxItems value or more than 100 roles, the response
// value IsTruncated will be true.
var request = new ListRolesRequest
{
    MaxItems = 10,
};

var response = new ListRolesResponse();

do
{
    response = await client.ListRolesAsync(request);
    response.Roles.ForEach(role =>
    {
        Console.WriteLine($"{role.RoleName} - ARN {role.Arn}");
    });

    // As long as response.IsTruncated is true, set request.Marker equal
    // to response.Marker and call ListRolesAsync again.
    if (response.IsTruncated)
    {
        request.Marker = response.Marker;
    }
} while (response.IsTruncated);
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
+  For API details, see [ListRoles](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/ListRoles) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
  

```
	// ListRoles

	roles, err := service.ListRoles(context.Background(), &iam.ListRolesInput{})

	if err != nil {
		panic("Could not list roles: " + err.Error())
	}

	fmt.Println("☑️ list roles")
	for _, idxRole := range roles.Roles {

		fmt.Printf("%s\t%s\t%s\t",
			*idxRole.RoleId,
			*idxRole.RoleName,
			*idxRole.Arn)
		if idxRole.Description != nil {
			fmt.Print(*idxRole.Description)
		}
		fmt.Print("\n")
	}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [ListRoles](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListRoles) in *AWS SDK for Go API Reference*\. 

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
List the roles\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { ListRolesCommand } from "@aws-sdk/client-iam";

// Set the parameters.
const params = {
    Marker: 'MARKER', // This is a string value.
    MaxItems: 'MAX_ITEMS' // This is a number value.
};

const run = async () => {
        try {
            const results = await iamClient.send(new ListRolesCommand(params));
            console.log("Success", results);
            return results;
        } catch (err) {
            console.log("Error", err);
        }
};
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For API details, see [ListRoles](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listrolescommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
  

```
$uuid = uniqid();
$service = new IamService();

    /**
     * @param string $pathPrefix
     * @param string $marker
     * @param int $maxItems
     * @return Result
     * $roles = $service->listRoles();
     */
    public function listRoles($pathPrefix = "", $marker = "", $maxItems = 0)
    {
        $listRolesArguments = [];
        if ($pathPrefix) {
            $listRolesArguments["PathPrefix"] = $pathPrefix;
        }
        if ($marker) {
            $listRolesArguments["Marker"] = $marker;
        }
        if ($maxItems) {
            $listRolesArguments["MaxItems"] = $maxItems;
        }
        return $this->iamClient->listRoles($listRolesArguments);
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListRoles](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/ListRoles) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def list_roles(count):
    """
    Lists the specified number of roles for the account.

    :param count: The number of roles to list.
    """
    try:
        roles = list(iam.roles.limit(count=count))
        for role in roles:
            logger.info("Role: %s", role.name)
    except ClientError:
        logger.exception("Couldn't list roles for the account.")
        raise
    else:
        return roles
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListRoles](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/ListRoles) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
  

```
  # Lists up to a specified number of roles for the account.
  #
  # @param count [Integer] The maximum number of roles to list.
  # @return [Array] The names of the listed roles.
  def list_roles(count)
    role_names = []
    @iam_resource.roles.limit(count).each_with_index do |role, index|
      puts("\t#{index + 1}: #{role.name}")
      role_names.append(role.name)
    end
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't list roles for the account. Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    role_names
  end
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
+  For API details, see [ListRoles](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/ListRoles) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
  

```
pub async fn list_roles(
    client: &iamClient,
    path_prefix: Option<String>,
    marker: Option<String>,
    max_items: Option<i32>,
) -> Result<ListRolesOutput, SdkError<ListRolesError>> {
    let response = client
        .list_roles()
        .set_path_prefix(path_prefix)
        .set_marker(marker)
        .set_max_items(max_items)
        .send()
        .await?;
    Ok(response)
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
+  For API details, see [ListRoles](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.