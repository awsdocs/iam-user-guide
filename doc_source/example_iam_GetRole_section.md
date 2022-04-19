# Get an IAM role using an AWS SDK<a name="example_iam_GetRole_section"></a>

The following code examples show how to get an IAM role\.

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

var response = await client.GetRoleAsync(new GetRoleRequest
{
    RoleName = "LambdaS3Role",
});

if (response.Role is not null)
{
    Console.WriteLine($"{response.Role.RoleName} with ARN: {response.Role.Arn}");
    Console.WriteLine($"{response.Role.Description}");
    Console.WriteLine($"Created: {response.Role.CreateDate} Last used on: { response.Role.RoleLastUsed}");
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
+  For API details, see [GetRole](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/GetRole) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
  

```
	// GetRole

	getRoleResult, err := service.GetRole(context.Background(), &iam.GetRoleInput{
		RoleName: aws.String(ExampleRoleName),
	})

	if err != nil {
		panic("Couldn't get role! " + err.Error())
	}

	fmt.Println("☑️ GetRole results: ")
	fmt.Println("ARN: ", *getRoleResult.Role.Arn)
	fmt.Println("Name: ", *getRoleResult.Role.RoleName)
	fmt.Println("Created On: ", *getRoleResult.Role.CreateDate)
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [GetRole](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.GetRole) in *AWS SDK for Go API Reference*\. 

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
Get the role\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { GetRoleCommand } from "@aws-sdk/client-iam";

// Set the parameters.
const params = {
  RoleName: "ROLE_NAME" /* required */
};

const run = async () => {
  try {
    const data = await iamClient.send(new GetRoleCommand(params));
    console.log("Success", data.Role);
  } catch (err) {
    console.log("Error", err);
  }
};
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For API details, see [GetRole](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/getrolecommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
  

```
$uuid = uniqid();
$service = new IamService();

    public function getRole($roleName)
    {
        return $this->customWaiter(function () use ($roleName) {
            return $this->iamClient->getRole(['RoleName' => $roleName]);
        });
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [GetRole](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/GetRole) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def get_role(role_name):
    """
    Gets a role by name.

    :param role_name: The name of the role to retrieve.
    :return: The specified role.
    """
    try:
        role = iam.Role(role_name)
        role.load()  # calls GetRole to load attributes
        logger.info("Got role with arn %s.", role.arn)
    except ClientError:
        logger.exception("Couldn't get role named %s.", role_name)
        raise
    else:
        return role
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [GetRole](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/GetRole) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
  

```
  # Gets data about a role.
  #
  # @param name [String] The name of the role to look up.
  # @return [Aws::IAM::Role] The retrieved role.
  def get_role(name)
    role = @iam_resource.role(name)
    puts("Got data for role '#{role.name}'. Its ARN is '#{role.arn}'.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't get data for role '#{name}' Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    role
  end
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
+  For API details, see [GetRole](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/GetRole) in *AWS SDK for Ruby API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.