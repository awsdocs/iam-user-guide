# List SAML providers for IAM using an AWS SDK<a name="example_iam_ListSAMLProviders_section"></a>

The following code examples show how to list SAML providers for IAM\.

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

var response = await client.ListSAMLProvidersAsync(new ListSAMLProvidersRequest());

response.SAMLProviderList.ForEach(samlProvider =>
{
    Console.WriteLine($"{samlProvider.Arn} created on: {samlProvider.CreateDate}");
});
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
+  For API details, see [ListSAMLProviders](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/ListSAMLProviders) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
  

```
	// ListSAMLProviders

	samlProviderList, err := service.ListSAMLProviders(context.Background(), &iam.ListSAMLProvidersInput{})

	if err != nil {
		panic("Couldn't list saml providers: " + err.Error())
	}

	for _, provider := range samlProviderList.SAMLProviderList {
		fmt.Printf("%s %s -> %s", *provider.Arn, *provider.CreateDate, *provider.ValidUntil)
	}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [ListSAMLProviders](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListSAMLProviders) in *AWS SDK for Go API Reference*\. 

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
List the SAML providers\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import {ListSAMLProvidersCommand} from "@aws-sdk/client-iam";

export const run = async () => {
    try {
        const results = await iamClient.send(new ListSAMLProvidersCommand({}));
        console.log("Success", results);
        return results;
    } catch (err) {
        console.log("Error", err);
    }
}
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For API details, see [ListSAMLProviders](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listsamlproviderscommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
  

```
$uuid = uniqid();
$service = new IamService();

    public function listSAMLProviders()
    {
        return $this->iamClient->listSAMLProviders();
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListSAMLProviders](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/ListSAMLProviders) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def list_saml_providers(count):
    """
    Lists the SAML providers for the account.

    :param count: The maximum number of providers to list.
    """
    try:
        found = 0
        for provider in iam.saml_providers.limit(count):
            logger.info('Got SAML provider %s.', provider.arn)
            found += 1
        if found == 0:
            logger.info("Your account has no SAML providers.")
    except ClientError:
        logger.exception("Couldn't list SAML providers.")
        raise
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListSAMLProviders](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/ListSAMLProviders) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
  

```
  # Lists up to a specified number of SAML providers for the account.
  #
  # @param count [Integer] The maximum number of providers to list.
  def list_saml_providers(count)
    @iam_resource.saml_providers.limit(count).each do |provider|
      puts("\t#{provider.arn}")
    end
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't list SAML providers. Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  end
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
+  For API details, see [ListSAMLProviders](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/ListSAMLProviders) in *AWS SDK for Ruby API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.