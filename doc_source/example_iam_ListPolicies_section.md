# List IAM policies using an AWS SDK<a name="example_iam_ListPolicies_section"></a>

The following code examples show how to list IAM policies\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
  

```
using Amazon.IdentityManagement;
using Amazon.IdentityManagement.Model;
using System;

var client = new AmazonIdentityManagementServiceClient();

var request = new ListPoliciesRequest
{
    MaxItems = 10,
};

var response = new ListPoliciesResponse();

do
{
    response = await client.ListPoliciesAsync(request);
    response.Policies.ForEach(policy =>
    {
        Console.Write($"{policy.PolicyName} ");
        Console.Write($"with ID: {policy.PolicyId} ");
        Console.Write($"and ARN: {policy.Arn}. ");
        Console.WriteLine($"It was created on {policy.CreateDate}.");
    });

    if (response.IsTruncated)
    {
        request.Marker = response.Marker;
    }
} while (response.IsTruncated);
```
+  For API details, see [ListPolicies](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/ListPolicies) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
	// ListPolicies

	policyListResponse, err := service.ListPolicies(context.Background(), &iam.ListPoliciesInput{})

	if err != nil {
		panic("Couldn't get list of policies! " + err.Error())
	}

	fmt.Print("PolicyName\tARN")
	for _, policy := range policyListResponse.Policies {
		fmt.Printf("%s\t%s\n", *policy.PolicyName, *policy.Arn)
	}
```
+  For API details, see [ListPolicies](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListPolicies) in *AWS SDK for Go API Reference*\. 

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
List the policies\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import {ListPoliciesCommand} from "@aws-sdk/client-iam";

// Set the parameters.
export const params = {
    Marker: 'MARKER',
    MaxItems: 'MAX_ITEMS',
    OnlyAttached: "ONLY_ATTACHED", /* Options are "true" or "false"*/
    PathPrefix: 'PATH_PREFIX',
    PolicyUsageFilter: "POLICY_USAGE_FILTER", /* Options are "PermissionsPolicy" or "PermissionsBoundary"*/
    Scope: "SCOPE" /* Options are "All", "AWS", "Local"*/
};

export const run = async () => {
    try {
        const results = await iamClient.send(new ListPoliciesCommand(params));
        console.log("Success", results);
        return results;
    } catch (err) {
        console.log("Error", err);
    }
};
run();
```
+  For API details, see [ListPolicies](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listpoliciescommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
  

```
$uuid = uniqid();
$service = new IamService();

    public function listPolicies($pathPrefix = "", $marker = "", $maxItems = 0)
    {
        $listPoliciesArguments = [];
        if ($pathPrefix) {
            $listPoliciesArguments["PathPrefix"] = $pathPrefix;
        }
        if ($marker) {
            $listPoliciesArguments["Marker"] = $marker;
        }
        if ($maxItems) {
            $listPoliciesArguments["MaxItems"] = $maxItems;
        }

        return $this->iamClient->listPolicies($listPoliciesArguments);
    }
```
+  For API details, see [ListPolicies](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/ListPolicies) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
  

```
def list_policies(scope):
    """
    Lists the policies in the current account.

    :param scope: Limits the kinds of policies that are returned. For example,
                  'Local' specifies that only locally managed policies are returned.
    :return: The list of policies.
    """
    try:
        policies = list(iam.policies.filter(Scope=scope))
        logger.info("Got %s policies in scope '%s'.", len(policies), scope)
    except ClientError:
        logger.exception("Couldn't get policies for scope '%s'.", scope)
        raise
    else:
        return policies
```
+  For API details, see [ListPolicies](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/ListPolicies) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
  

```
  # Lists up to a specified number of policies in the account.
  #
  # @param count [Integer] The maximum number of policies to list.
  # @return [Array] The Amazon Resource Names (ARNs) of the policies listed.
  def list_policies(count)
    policy_arns = []
    @iam_resource.policies.limit(count).each_with_index do |policy, index|
      puts("\t#{index + 1}: #{policy.policy_name}: #{policy.arn}")
      policy_arns.append(policy.arn)
    end
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't list policies for the account. Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    policy_arns
  end
```
+  For API details, see [ListPolicies](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/ListPolicies) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
  

```
pub async fn list_policies(
    client: &iamClient,
    path_prefix: Option<String>,
    marker: Option<String>,
    max_items: Option<i32>,
) -> Result<ListPoliciesOutput, SdkError<ListPoliciesError>> {
    let response = client
        .list_policies()
        .set_path_prefix(path_prefix)
        .set_marker(marker)
        .set_max_items(max_items)
        .send()
        .await?;

    Ok(response)
}
```
+  For API details, see [ListPolicies](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.