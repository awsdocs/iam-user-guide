# List policies attached to an IAM role using an AWS SDK<a name="example_iam_ListAttachedRolePolicies_section"></a>

The following code examples show how to list policies attached to an IAM role\.

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
var request = new ListAttachedRolePoliciesRequest
{
    MaxItems = 10,
    RoleName = "testAssumeRole",
};

var response = await client.ListAttachedRolePoliciesAsync(request);

do
{
    response.AttachedPolicies.ForEach(policy =>
    {
        Console.WriteLine($"{policy.PolicyName} with ARN: {policy.PolicyArn}");
    });

    if (response.IsTruncated)
    {
        request.Marker = response.Marker;
        response = await client.ListAttachedRolePoliciesAsync(request);
    }

} while (response.IsTruncated);
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
+  For API details, see [ListAttachedRolePolicies](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/ListAttachedRolePolicies) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Go ]

**SDK for Go V2**  
  

```
	// ListAttachedRolePolicies

	attachedPoliciesList, err := service.ListAttachedRolePolicies(context.Background(), &iam.ListAttachedRolePoliciesInput{
		RoleName: aws.String(ExampleRoleName),
	})

	if err != nil {
		panic("Couldn't call ListAttachedRolePolicies: " + err.Error())
	}

	fmt.Println("➡️ List attached role policies for " + ExampleRoleName)

	for _, attachedPolicy := range attachedPoliciesList.AttachedPolicies {
		fmt.Printf("attached policy: %v\n (%v) \n", attachedPolicy.PolicyArn, attachedPolicy.PolicyName)
	}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
+  For API details, see [ListAttachedRolePolicies](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.ListAttachedRolePolicies) in *AWS SDK for Go API Reference*\. 

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
List the policies that are attached to a role\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import {ListAttachedRolePoliciesCommand} from "@aws-sdk/client-iam";

// Set the parameters.
export const params = {
    RoleName: 'ROLE_NAME' /* required */
};

export const run = async () => {
    try {
        const data = await iamClient.send(new ListAttachedRolePoliciesCommand(params));
        console.log("Success", data.AttachedPolicies);
    } catch (err) {
        console.log("Error", err);
    }
}
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For API details, see [ListAttachedRolePolicies](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/listattachedrolepoliciescommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ PHP ]

**SDK for PHP**  
  

```
$uuid = uniqid();
$service = new IamService();

    public function listAttachedRolePolicies($roleName, $pathPrefix = "", $marker = "", $maxItems = 0)
    {
        $listAttachRolePoliciesArguments = ['RoleName' => $roleName];
        if ($pathPrefix) {
            $listAttachRolePoliciesArguments['PathPrefix'] = $pathPrefix;
        }
        if ($marker) {
            $listAttachRolePoliciesArguments['Marker'] = $marker;
        }
        if ($maxItems) {
            $listAttachRolePoliciesArguments['MaxItems'] = $maxItems;
        }
        return $this->iamClient->listAttachedRolePolicies($listAttachRolePoliciesArguments);
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListAttachedRolePolicies](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/ListAttachedRolePolicies) in *AWS SDK for PHP API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def list_attached_policies(role_name):
    """
    Lists policies attached to a role.

    :param role_name: The name of the role to query.
    """
    try:
        role = iam.Role(role_name)
        for policy in role.attached_policies.all():
            logger.info("Got policy %s.", policy.arn)
    except ClientError:
        logger.exception("Couldn't list attached policies for %s.", role_name)
        raise
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [ListAttachedRolePolicies](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/ListAttachedRolePolicies) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
  

```
  # Deletes a role. If the role has policies attached, they are detached and
  # deleted before the role is deleted.
  #
  # @param role [Aws::IAM::Role] The role to delete.
  def delete_role(role)
    role.attached_policies.each do |policy|
      name = policy.policy_name
      policy.detach_role(role_name: role.name)
      policy.delete
      puts("Deleted policy #{name}.")
    end
    name = role.name
    role.delete
    puts("Deleted role #{name}.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't detach policies and delete role #{role.name}. Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  end
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
+  For API details, see [ListAttachedRolePolicies](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/ListAttachedRolePolicies) in *AWS SDK for Ruby API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.