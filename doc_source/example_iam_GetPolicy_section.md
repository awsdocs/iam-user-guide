# Get an IAM policy using an AWS SDK<a name="example_iam_GetPolicy_section"></a>

The following code examples show how to get an IAM policy\.

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
var request = new GetPolicyRequest
{
    PolicyArn = "POLICY_ARN",
};

var response = await client.GetPolicyAsync(request);

Console.Write($"{response.Policy.PolicyName} was created on ");
Console.WriteLine($"{response.Policy.CreateDate}");
```
+  For API details, see [GetPolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/GetPolicy) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
	// GetPolicy

	getPolicyResponse, err := service.GetPolicy(context.Background(), &iam.GetPolicyInput{
		PolicyArn: policyArn,
	})

	if err != nil {
		panic("Couldn't get policy from ARN: " + err.Error())
	}

	fmt.Printf("policy: %s, name %s\n",
		*getPolicyResponse.Policy.Arn,
		*getPolicyResponse.Policy.PolicyName)
```
+  For API details, see [GetPolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.GetPolicy) in *AWS SDK for Go API Reference*\. 

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
Get the policy\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { GetPolicyCommand } from "@aws-sdk/client-iam";

// Set the parameters.
const params = {
  PolicyArn: "POLICY_ARN" /* required */,
};

const run = async () => {
  try {
    const data = await iamClient.send(new GetPolicyCommand(params));
    console.log("Success", data.Policy);
  } catch (err) {
    console.log("Error", err);
  }
};
run();
```
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/iam-examples-policies.html#iam-examples-policies-getting)\. 
+  For API details, see [GetPolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/getpolicycommand.html) in *AWS SDK for JavaScript API Reference*\. 

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
  PolicyArn: 'arn:aws:iam::aws:policy/AWSLambdaExecute'
};

iam.getPolicy(params, function(err, data) {
  if (err) {
    console.log("Error", err);
  } else {
    console.log("Success", data.Policy.Description);
  }
});
```
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/iam-examples-policies.html#iam-examples-policies-getting)\. 
+  For API details, see [GetPolicy](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/iam-2010-05-08/GetPolicy) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
  

```
suspend fun getIAMPolicy(policyArnVal: String?) {

    val request = GetPolicyRequest {
        policyArn = policyArnVal
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        val response = iamClient.getPolicy(request)
        println("Successfully retrieved policy ${response.policy?.policyName}")
    }
}
```
+  For API details, see [GetPolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
  

```
$uuid = uniqid();
$service = new IamService();

    public function getPolicy($policyArn)
    {
        return $this->customWaiter(function () use ($policyArn) {
            return $this->iamClient->getPolicy(['PolicyArn' => $policyArn]);
        });
    }
```
+  For API details, see [GetPolicy](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/GetPolicy) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
  

```
def get_default_policy_statement(policy_arn):
    """
    Gets the statement of the default version of the specified policy.

    :param policy_arn: The ARN of the policy to look up.
    :return: The statement of the default policy version.
    """
    try:
        policy = iam.Policy(policy_arn)
        # To get an attribute of a policy, the SDK first calls get_policy.
        policy_doc = policy.default_version.document
        policy_statement = policy_doc.get('Statement', None)
        logger.info("Got default policy doc for %s.", policy.policy_name)
        logger.info(policy_doc)
    except ClientError:
        logger.exception("Couldn't get default policy statement for %s.", policy_arn)
        raise
    else:
        return policy_statement
```
+  For API details, see [GetPolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/GetPolicy) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
  

```
  # Gets data about a policy.
  #
  # @param policy_arn [String] The ARN of the policy to look up.
  # @return [Aws::IAM::Policy] The retrieved policy.
  def get_policy(policy_arn)
    policy = @iam_resource.policy(policy_arn)
    puts("Got policy '#{policy.policy_name}'. Its ID is: #{policy.policy_id}.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't get policy '#{policy_arn}'. Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    policy
  end
```
+  For API details, see [GetPolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/GetPolicy) in *AWS SDK for Ruby API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.