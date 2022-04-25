# List inline policies for an IAM role using an AWS SDK<a name="example_iam_ListRolePolicies_section"></a>

The following code examples show how to list inline policies for an IAM role\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
  

```
using Amazon.IdentityManagement;
using Amazon.IdentityManagement.Model;
using System;

var client = new AmazonIdentityManagementServiceClient();
var request = new ListRolePoliciesRequest
{
    RoleName = "LambdaS3Role",
};

var response = new ListRolePoliciesResponse();

do
{
    response = await client.ListRolePoliciesAsync(request);

    if (response.PolicyNames.Count > 0)
    {
        response.PolicyNames.ForEach(policyName =>
        {
            Console.WriteLine($"{policyName}");
        });
    }

    // As long as response.IsTruncated is true, set request.Marker equal
    // to response.Marker and call ListRolesAsync again.
    if (response.IsTruncated)
    {
        request.Marker = response.Marker;
    }
} while (response.IsTruncated);
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
+  For API details, see [ListRolePolicies](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/ListRolePolicies) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
  

```
	// ListRolePolicies

	rolePoliciesList, err := service.ListRolePolicies(context.Background(), &iam.ListRolePoliciesInput{
		RoleName: aws.String(ExampleRoleName),
	})

	if err != nil {
		panic("Couldn't list policies for role: " + err.Error())
	}

	for _, rolePolicy := range rolePoliciesList.PolicyNames {
		fmt.Printf("Policy ARN: %v", rolePolicy)
	}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [ListRolePolicies](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListRolePolicies) in *AWS SDK for Go API Reference*\. 

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
List the policies\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import {ListRolePoliciesCommand} from "@aws-sdk/client-iam";

// Set the parameters.
export const params = {
    RoleName: 'ROLE_NAME', /* This is a number value. Required */
    Marker: 'MARKER', /* This is a string value. Optional */
    MaxItems: 'MAX_ITEMS' /* This is a number value. Optional */
};

export const run = async () => {
    try {
        const results = await iamClient.send(new ListRolePoliciesCommand(params));
        console.log("Success", results);
        return results;
    } catch (err) {
        console.log("Error", err);
    }
}
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For API details, see [ListRolePolicies](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listrolepoliciescommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
  

```
$uuid = uniqid();
$service = new IamService();

    public function listRolePolicies($roleName, $marker = "", $maxItems = 0)
    {
        $listRolePoliciesArguments = ['RoleName' => $roleName];
        if ($marker) {
            $listRolePoliciesArguments['Marker'] = $marker;
        }
        if ($maxItems) {
            $listRolePoliciesArguments['MaxItems'] = $maxItems;
        }
        return $this->customWaiter(function () use ($listRolePoliciesArguments) {
            return $this->iamClient->listRolePolicies($listRolePoliciesArguments);
        });
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListRolePolicies](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/ListRolePolicies) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def list_policies(role_name):
    """
    Lists inline policies for a role.

    :param role_name: The name of the role to query.
    """
    try:
        role = iam.Role(role_name)
        for policy in role.policies.all():
            logger.info("Got inline policy %s.", policy.name)
    except ClientError:
        logger.exception("Couldn't list inline policies for %s.", role_name)
        raise
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListRolePolicies](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/ListRolePolicies) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
  

```
pub async fn list_role_policies(
    client: &iamClient,
    role_name: &str,
    marker: Option<String>,
    max_items: Option<i32>,
) -> Result<ListRolePoliciesOutput, SdkError<ListRolePoliciesError>> {
    let response = client
        .list_role_policies()
        .role_name(role_name)
        .set_marker(marker)
        .set_max_items(max_items)
        .send()
        .await?;

    Ok(response)
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
+  For API details, see [ListRolePolicies](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.