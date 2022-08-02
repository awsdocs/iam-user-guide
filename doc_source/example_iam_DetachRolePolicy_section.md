# Detach an IAM policy from a role using an AWS SDK<a name="example_iam_DetachRolePolicy_section"></a>

The following code examples show how to detach an IAM policy from a role\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
  

```
        /// <summary>
        /// Delete the user, and other resources created for this example.
        /// </summary>
        /// <param name="client">The initialized client object.</param>
        /// <param name=accessKeyId">The Id of the user's access key.</param>"
        /// <param name="userName">The user name of the user to delete.</param>
        /// <param name="policyName">The name of the policy to delete.</param>
        /// <param name="policyArn">The Amazon Resource Name ARN of the Policy to delete.</param>
        /// <param name="roleName">The name of the role that will be deleted.</param>
        public static async Task DeleteResourcesAsync(
            AmazonIdentityManagementServiceClient client,
            string accessKeyId,
            string userName,
            string policyArn,
            string roleName)
        {
            var detachPolicyResponse = await client.DetachRolePolicyAsync(new DetachRolePolicyRequest
            {
                PolicyArn = policyArn,
                RoleName = roleName,
            });

            var delPolicyResponse = await client.DeletePolicyAsync(new DeletePolicyRequest
            {
                PolicyArn = policyArn,
            });

            var delRoleResponse = await client.DeleteRoleAsync(new DeleteRoleRequest
            {
                RoleName = roleName,
            });

            var delAccessKey = await client.DeleteAccessKeyAsync(new DeleteAccessKeyRequest
            {
                AccessKeyId = accessKeyId,
                UserName = userName,
            });

            var delUserResponse = await client.DeleteUserAsync(new DeleteUserRequest
            {
                UserName = userName,
            });

        }
```
+  For API details, see [DetachRolePolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DetachRolePolicy) in *AWS SDK for \.NET API Reference*\. 

------
#### [ Java ]

**SDK for Java 2\.x**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/iam#readme)\. 
  

```
    public static void detachPolicy(IamClient iam, String roleName, String policyArn ) {

        try {
            DetachRolePolicyRequest request = DetachRolePolicyRequest.builder()
                .roleName(roleName)
                .policyArn(policyArn)
                .build();

            iam.detachRolePolicy(request);
            System.out.println("Successfully detached policy " + policyArn +
                " from role " + roleName);

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }
```
+  For API details, see [DetachRolePolicy](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DetachRolePolicy) in *AWS SDK for Java 2\.x API Reference*\. 

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
Detach the policy\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient } from "./libs/iamClient.js";
import {
  ListAttachedRolePoliciesCommand,
  DetachRolePolicyCommand,
} from "@aws-sdk/client-iam";

// Set the parameters.
export const params = { RoleName: "ROLE_NAME" }; //ROLE_NAME

export const run = async () => {
  try {
    const data = await iamClient.send(
      new ListAttachedRolePoliciesCommand(params)
    );
    return data;
    const myRolePolicies = data.AttachedPolicies;
    myRolePolicies.forEach(function (val, index, array) {
      if (myRolePolicies[index].PolicyName === "AmazonDynamoDBFullAccess") {
         const params = {
          PolicyArn: "arn:aws:iam::aws:policy/AmazonDynamoDBFullAccess",
          paramsRoleList,
        };
        try {
          const results = iamClient.send(
            new DetachRolePolicyCommand(paramsRoleList)
          );
          console.log("Policy detached from role successfully");
          process.exit();
        } catch (err) {
          console.log("Unable to detach policy from role", err);
        }
      } else {
      }
    });
  } catch (err) {
    console.log("User " + "USER_NAME" + " does not exist.");
  }
};
run();
```
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/iam-examples-policies.html#iam-examples-policies-detaching-role-policy)\. 
+  For API details, see [DetachRolePolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/detachrolepolicycommand.html) in *AWS SDK for JavaScript API Reference*\. 

**SDK for JavaScript V2**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascript/example_code/iam#code-examples)\. 
  

```
// Load the AWS SDK for Node.js
var AWS = require('aws-sdk');
// Set the region 
AWS.config.update({region: 'REGION'});

// Create the IAM service object
var iam = new AWS.IAM({apiVersion: '2010-05-08'});

var paramsRoleList = {
  RoleName: process.argv[2]
};

iam.listAttachedRolePolicies(paramsRoleList, function(err, data) {
  if (err) {
    console.log("Error", err);
  } else {
    var myRolePolicies = data.AttachedPolicies;
    myRolePolicies.forEach(function (val, index, array) {
      if (myRolePolicies[index].PolicyName === 'AmazonDynamoDBFullAccess') {
        var params = {
          PolicyArn: 'arn:aws:iam::aws:policy/AmazonDynamoDBFullAccess',
          RoleName: process.argv[2]
        };
        iam.detachRolePolicy(params, function(err, data) {
          if (err) {
            console.log("Unable to detach policy from role", err);
          } else {
            console.log("Policy detached from role successfully");
            process.exit();
          }
        });
      }
    });
  }
});
```
+  For more information, see [AWS SDK for JavaScript Developer Guide](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/iam-examples-policies.html#iam-examples-policies-detaching-role-policy)\. 
+  For API details, see [DetachRolePolicy](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/iam-2010-05-08/DetachRolePolicy) in *AWS SDK for JavaScript API Reference*\. 

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
  

```
suspend fun detachPolicy(roleNameVal: String, policyArnVal: String) {

    val request = DetachRolePolicyRequest {
        roleName = roleNameVal
        policyArn = policyArnVal
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        iamClient.detachRolePolicy(request)
        println("Successfully detached policy $policyArnVal from role $roleNameVal")
    }
}
```
+  For API details, see [DetachRolePolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation) in *AWS SDK for Kotlin API reference*\. 

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
Detach a policy from a role using the Boto3 Policy object\.  

```
def detach_from_role(role_name, policy_arn):
    """
    Detaches a policy from a role.

    :param role_name: The name of the role. **Note** this is the name, not the ARN.
    :param policy_arn: The ARN of the policy.
    """
    try:
        iam.Policy(policy_arn).detach_role(RoleName=role_name)
        logger.info("Detached policy %s from role %s.", policy_arn, role_name)
    except ClientError:
        logger.exception(
            "Couldn't detach policy %s from role %s.", policy_arn, role_name)
        raise
```
Detach a policy from a role using the Boto3 Role object\.  

```
def detach_policy(role_name, policy_arn):
    """
    Detaches a policy from a role.

    :param role_name: The name of the role. **Note** this is the name, not the ARN.
    :param policy_arn: The ARN of the policy.
    """
    try:
        iam.Role(role_name).detach_policy(PolicyArn=policy_arn)
        logger.info("Detached policy %s from role %s.", policy_arn, role_name)
    except ClientError:
        logger.exception(
            "Couldn't detach policy %s from role %s.", policy_arn, role_name)
        raise
```
+  For API details, see [DetachRolePolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DetachRolePolicy) in *AWS SDK for Python \(Boto3\) API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
  

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
+  For API details, see [DetachRolePolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DetachRolePolicy) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
  

```
pub async fn detach_role_policy(
    client: &iamClient,
    role_name: &str,
    policy_arn: &str,
) -> Result<(), iamError> {
    client
        .detach_role_policy()
        .role_name(role_name)
        .policy_arn(policy_arn)
        .send()
        .await?;

    Ok(())
}
```
+  For API details, see [DetachRolePolicy](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.