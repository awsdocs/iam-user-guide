# Create an IAM service\-linked role using an AWS SDK<a name="example_iam_CreateServiceLinkedRole_section"></a>

The following code examples show how to create an IAM service\-linked role\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Go ]

**SDK for Go V2**  
  

```
	// CreateServiceLinkedRole

	fmt.Println("➡️ Create SLR for " + ExampleSLRService)
	createSlrResult, err := service.CreateServiceLinkedRole(context.Background(), &iam.CreateServiceLinkedRoleInput{
		AWSServiceName: aws.String(ExampleSLRService),
		Description:    aws.String(ExampleSLRDescription),
	})

	// NOTE: We don't consider this an error as running this example multiple times will cause an error.
	if err != nil {
		fmt.Printf("Couldn't create service-linked role: %v\n", err.Error())
	} else {

		fmt.Printf("Created service-linked role with ARN: %s\n", *createSlrResult.Role.Arn)
	}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [CreateServiceLinkedRole](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.CreateServiceLinkedRole) in *AWS SDK for Go API Reference*\. 

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
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/createservicelinkedrolecommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
  

```
$uuid = uniqid();
$service = new IamService();

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
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/CreateServiceLinkedRole) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

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
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/CreateServiceLinkedRole) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
  

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
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
+  For API details, see [CreateServiceLinkedRole](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/CreateServiceLinkedRole) in *AWS SDK for Ruby API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.