# Delete an IAM role using an AWS SDK<a name="example_iam_DeleteRole_section"></a>

The following code examples show how to delete an IAM role\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

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
Delete the role\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import { DeleteRoleCommand } from "@aws-sdk/client-iam";

// Set the parameters.
const params = {
    RoleName: "ROLE_NAME"
}

const run = async () => {
    try {
        const data = await iamClient.send(new DeleteRoleCommand(params));
        console.log("Success. Role deleted.", data);
    } catch (err) {
        console.log("Error", err);
    }
};
run();
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
+  For API details, see [DeleteRole](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/deleterolecommand.html) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
  

```
def delete_role(role_name):
    """
    Deletes a role.

    :param role_name: The name of the role to delete.
    """
    try:
        iam.Role(role_name).delete()
        logger.info("Deleted role %s.", role_name)
    except ClientError:
        logger.exception("Couldn't delete role %s.", role_name)
        raise
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
+  For API details, see [DeleteRole](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DeleteRole) in *AWS SDK for Python \(Boto3\) API Reference*\. 

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
+  For API details, see [DeleteRole](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeleteRole) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
  

```
pub async fn delete_role(client: &iamClient, role: &Role) -> Result<(), iamError> {
    let role = role.clone();
    loop {
        match client
            .delete_role()
            .role_name(role.role_name.as_ref().unwrap())
            .send()
            .await
        {
            Ok(_) => {
                break;
            }
            Err(_) => {
                sleep(Duration::from_secs(2)).await;
            }
        }
    }
    Ok(())
}
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
+  For API details, see [DeleteRole](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.