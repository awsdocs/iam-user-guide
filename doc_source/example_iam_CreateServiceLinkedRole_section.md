# Create an IAM service\-linked role using an AWS SDK<a name="example_iam_CreateServiceLinkedRole_section"></a>

The following code examples show how to create an IAM service\-linked role\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
  

```
    /// <summary>
    /// Create an IAM service-linked role.
    /// </summary>
    /// <param name="serviceName">The name of the AWS Service.</param>
    /// <param name="description">A description of the IAM service-linked role.</param>
    /// <returns>The IAM role that was created.</returns>
    public async Task<Role> CreateServiceLinkedRoleAsync(string serviceName, string description)
    {
        var request = new CreateServiceLinkedRoleRequest
        {
            AWSServiceName = serviceName,
            Description = description
        };

        var response = await _IAMService.CreateServiceLinkedRoleAsync(request);
        return response.Role;
    }
```
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/CreateServiceLinkedRole) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
// RoleWrapper encapsulates AWS Identity and Access Management (IAM) role actions
// used in the examples.
// It contains an IAM service client that is used to perform role actions.
type RoleWrapper struct {
	IamClient *iam.Client
}



// CreateServiceLinkedRole creates a service-linked role that is owned by the specified service.
func (wrapper RoleWrapper) CreateServiceLinkedRole(serviceName string, description string) (*types.Role, error) {
	var role *types.Role
	result, err := wrapper.IamClient.CreateServiceLinkedRole(context.TODO(), &iam.CreateServiceLinkedRoleInput{
		AWSServiceName: aws.String(serviceName),
		Description:    aws.String(description),
	})
	if err != nil {
		log.Printf("Couldn't create service-linked role %v. Here's why: %v\n", serviceName, err)
	} else {
		role = result.Role
	}
	return role, err
}
```
+  For API details, see [CreateServiceLinkedRole](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.CreateServiceLinkedRole) in *AWS SDK for Go API Reference*\. 

------
#### [ JavaScript ]

**SDK for JavaScript \(v3\)**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
Create the client\.  

```
import { IAMClient } from "@aws-sdk/client-iam";
// Set the AWS Region.
const REGION = "REGION"; // For example, "us-east-1".
// Create an IAM service client object.
const iamClient = new IAMClient({ region: REGION });
export { iamClient };
```
Create a service\-linked role\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { CreateServiceLinkedRoleCommand } from "@aws-sdk/client-iam";
// Set the parameters.
const params = {
  AWSServiceName: "AWS_SERVICE_NAME" /* required */,
};

const run = async () => {
  try {
    const data = await iamClient.send(
      new CreateServiceLinkedRoleCommand(params)
    );
    console.log("Success", data);
  } catch (err) {
    console.log("Error", err);
  }
};
run();
```
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/createservicelinkedrolecommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
  

```
$uuid = uniqid();
$service = new IAMService();

    public function createServiceLinkedRole($awsServiceName, $customSuffix = "", $description = "")
    {
        $createServiceLinkedRoleArguments = ['AWSServiceName' => $awsServiceName];
        if ($customSuffix) {
            $createServiceLinkedRoleArguments['CustomSuffix'] = $customSuffix;
        }
        if ($description) {
            $createServiceLinkedRoleArguments['Description'] = $description;
        }
        return $this->iamClient->createServiceLinkedRole($createServiceLinkedRoleArguments);
    }
```
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/CreateServiceLinkedRole) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
  

```
def create_service_linked_role(service_name, description):
    """
    Creates a service-linked role.

    :param service_name: The name of the service that owns the role.
    :param description: A description to give the role.
    :return: The newly created role.
    """
    try:
        response = iam.meta.client.create_service_linked_role(
            AWSServiceName=service_name, Description=description)
        role = iam.Role(response['Role']['RoleName'])
        logger.info("Created service-linked role %s.", role.name)
    except ClientError:
        logger.exception("Couldn't create service-linked role for %s.", service_name)
        raise
    else:
        return role
```
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/CreateServiceLinkedRole) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
  

```
  # Creates a service-linked role.
  #
  # @param service_name [String] The name of the service that owns the role.
  # @param description [String] A description to give the role.
  # @return [Aws::IAM::Role] The newly created role.
  def create_service_linked_role(service_name, description)
    response = @iam_resource.client.create_service_linked_role(
      aws_service_name: service_name, description: description)
    role = @iam_resource.role(response.role.role_name)
    puts("Created service-linked role #{role.name}.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't create service-linked role for #{service_name}. Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    role
  end
```
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/CreateServiceLinkedRole) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
  

```
pub async fn create_service_linked_role(
    client: &iamClient,
    aws_service_name: String,
    custom_suffix: Option<String>,
    description: Option<String>,
) -> Result<CreateServiceLinkedRoleOutput, SdkError<CreateServiceLinkedRoleError>> {
    let response = client
        .create_service_linked_role()
        .aws_service_name(aws_service_name)
        .set_custom_suffix(custom_suffix)
        .set_description(description)
        .send()
        .await?;

    Ok(response)
}
```
+  For API details, see [CreateServiceLinkedRole](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------
#### [ Swift ]

**SDK for Swift**  
This is prerelease documentation for an SDK in preview release\. It is subject to change\.
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/swift/example_code/iam/CreateServiceLinkedRole#code-examples)\. 
  

```
    public func createServiceLinkedRole(service: String, suffix: String? = nil, description: String?)
                    async throws -> IAMClientTypes.Role {
        let input = CreateServiceLinkedRoleInput(
            awsServiceName: service,
            customSuffix: suffix,
            description: description
        )
        do {
            let output = try await client.createServiceLinkedRole(input: input)
            guard let role = output.role else {
                throw ServiceHandlerError.noSuchRole
            }
            return role
        } catch {
            throw error
        }
    }
```
+  For API details, see [CreateServiceLinkedRole](https://awslabs.github.io/aws-sdk-swift/reference/0.x) in *AWS SDK for Swift API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.