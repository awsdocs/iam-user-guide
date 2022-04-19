# Delete an IAM role policy using an AWS SDK<a name="example_iam_DeleteRolePolicy_section"></a>

The following code example shows how to delete an IAM role policy\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
  

```
    using System;
    using System.Threading.Tasks;
    using Amazon.IdentityManagement;
    using Amazon.IdentityManagement.Model;

    public class DeleteRolePolicy
    {
        /// <summary>
        /// Initializes the IAM client object and then calls DeleteRolePolicyAsync
        /// to delete the Policy attached to the Role.
        /// </summary>
        public static async Task Main()
        {
            var client = new AmazonIdentityManagementServiceClient();
            var response = await client.DeleteRolePolicyAsync(new DeleteRolePolicyRequest
            {
                PolicyName = "ExamplePolicy",
                RoleName = "Test-Role",
            });

            if (response.HttpStatusCode == System.Net.HttpStatusCode.OK)
            {
                Console.WriteLine("Policy successfully deleted.");
            }
            else
            {
                Console.WriteLine("Could not delete pollicy.");
            }
        }
    }
```
+  Find instructions and more code on [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM#code-examples)\. 
+  For API details, see [DeleteRolePolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DeleteRolePolicy) in *AWS SDK for \.NET API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.