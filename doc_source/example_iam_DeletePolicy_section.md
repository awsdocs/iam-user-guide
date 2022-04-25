# Delete an IAM policy using an AWS SDK<a name="example_iam_DeletePolicy_section"></a>

The following code examples show how to delete an IAM policy\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Java ]

**SDK for Java 2\.x**  
  

```
    public static void deleteIAMPolicy(IamClient iam,String policyARN) {

        try {
            DeletePolicyRequest request = DeletePolicyRequest.builder()
                   .policyArn(policyARN)
                   .build();

            iam.deletePolicy(request);
            System.out.println("Successfully deleted the policy");

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
        System.out.println("Done");
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/iam#readme)\. 
+  For API details, see [DeletePolicy](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DeletePolicy) in *AWS SDK for Java 2\.x API Reference*\. 

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
Delete the policy\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { DeletePolicyCommand } from "@aws-sdk/client-iam";

// Set the parameters.
const params = { PolicyArn: "POLICY_ARN"};

const run = async () => {
    try {
        const data = await iamClient.send(new DeletePolicyCommand(params));
        console.log("Success. Policy deleted.", data);

    } catch (err) {
        console.log("Error", err);
    }
};
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam/#code-examples)\. 
+  For API details, see [DeletePolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/deletepolicycommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
  

```
suspend fun deleteIAMPolicy(policyARNVal: String?) {

    val request = DeletePolicyRequest {
        policyArn = policyARNVal
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
       iamClient.deletePolicy(request)
        println("Successfully deleted $policyARNVal")

    }
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
+  For API details, see [DeletePolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def delete_policy(policy_arn):
    """
    Deletes a policy.

    :param policy_arn: The ARN of the policy to delete.
    """
    try:
        iam.Policy(policy_arn).delete()
        logger.info("Deleted policy %s.", policy_arn)
    except ClientError:
        logger.exception("Couldn't delete policy %s.", policy_arn)
        raise
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [DeletePolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DeletePolicy) in *AWS SDK for Python \(Boto3\) API Reference*\. 

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
+  For API details, see [DeletePolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeletePolicy) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
  

```
pub async fn delete_policy(client: &iamClient, policy: Policy) -> Result<(), iamError> {
    client
        .delete_policy()
        .policy_arn(policy.arn.unwrap())
        .send()
        .await?;
    Ok(())
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
+  For API details, see [DeletePolicy](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.