# List IAM account aliases using an AWS SDK<a name="example_iam_ListAccountAliases_section"></a>

The following code examples show how to list IAM account aliases\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Go ]

**SDK for Go V2**  
  

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

// IAMListAccountAliasesAPI defines the interface for the ListAccountAliases function.
// We use this interface to test the function using a mocked service.
type IAMListAccountAliasesAPI interface {
	ListAccountAliases(ctx context.Context,
		params *iam.ListAccountAliasesInput,
		optFns ...func(*iam.Options)) (*iam.ListAccountAliasesOutput, error)
}

// GetAccountAliases retrieves the aliases for your AWS Identity and Access Management (IAM) account.
// Inputs:
//     c is the context of the method call, which includes the AWS Region.
//     api is the interface that defines the method call.
//     input defines the input arguments to the service call.
// Output:
//     If successful, a ListAccountAliasesOutput object containing the result of the service call and nil.
//     Otherwise, nil and an error from the call to ListAccountAliases.
func GetAccountAliases(c context.Context, api IAMListAccountAliasesAPI, input *iam.ListAccountAliasesInput) (*iam.ListAccountAliasesOutput, error) {
	return api.ListAccountAliases(c, input)
}

func main() {
	maxItems := flag.Int("m", 10, "Maximum number of aliases to list")
	flag.Parse()

	if *maxItems < 0 {
		*maxItems = 10
	}

	cfg, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		panic("configuration error, " + err.Error())
	}

	client := iam.NewFromConfig(cfg)

	input := &iam.ListAccountAliasesInput{
		MaxItems: aws.Int32(int32(*maxItems)),
	}

	result, err := GetAccountAliases(context.TODO(), client, input)
	if err != nil {
		fmt.Println("Got an error retrieving account aliases")
		fmt.Println(err)
		return
	}

	for i, alias := range result.AccountAliases {
		fmt.Printf("Alias %d: %s\n", i, alias)
	}
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [ListAccountAliases](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListAccountAliases) in *AWS SDK for Go API Reference*\. 

------
#### [ Java ]

**SDK for Java 2\.x**  
  

```
    public static void listAliases(IamClient iam) {

        try {
            ListAccountAliasesResponse response = iam.listAccountAliases();

            for (String alias : response.accountAliases()) {
                System.out.printf("Retrieved account alias %s", alias);
            }

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/iam#readme)\. 
+  For API details, see [ListAccountAliases](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/ListAccountAliases) in *AWS SDK for Java 2\.x API Reference*\. 

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
List the account aliases\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { ListAccountAliasesCommand } from "@aws-sdk/client-iam";

// Set the parameters.
export const params = { MaxItems: 5 };

export const run = async () => {
  try {
    const data = await iamClient.send(new ListAccountAliasesCommand(params));
    console.log("Success", data);
    return data;
  } catch (err) {
    console.log("Error", err);
  }
};
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/iam-examples-account-aliases.html#iam-examples-account-aliases-listing)\. 
+  For API details, see [ListAccountAliases](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listaccountaliasescommand.html) in *AWS SDK for JavaScript API Reference*\. 

**SDK for JavaScript V2**  
  

```
// Load the AWS SDK for Node.js
var AWS = require('aws-sdk');
// Set the region 
AWS.config.update({region: 'REGION'});

// Create the IAM service object
var iam = new AWS.IAM({apiVersion: '2010-05-08'});

iam.listAccountAliases({MaxItems: 10}, function(err, data) {
  if (err) {
    console.log("Error", err);
  } else {
    console.log("Success", data);
  }
});
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascript/example_code/iam#code-examples)\. 
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/iam-examples-account-aliases.html4#iam-examples-account-aliases-listing)\. 
+  For API details, see [ListAccountAliases](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/iam-2010-05-08/ListAccountAliases) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
  

```
suspend  fun listAliases() {

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
      val response = iamClient.listAccountAliases(ListAccountAliasesRequest{})
        response.accountAliases?.forEach { alias ->
            println("Retrieved account alias $alias")
        }

    }
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
+  For API details, see [ListAccountAliases](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def list_aliases():
    """
    Gets the list of aliases for the current account. An account has at most one alias.

    :return: The list of aliases for the account.
    """
    try:
        response = iam.meta.client.list_account_aliases()
        aliases = response['AccountAliases']
        if len(aliases) > 0:
            logger.info("Got aliases for your account: %s.", ','.join(aliases))
        else:
            logger.info("Got no aliases for your account.")
    except ClientError:
        logger.exception("Couldn't list aliases for your account.")
        raise
    else:
        return response['AccountAliases']
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListAccountAliases](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/ListAccountAliases) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.