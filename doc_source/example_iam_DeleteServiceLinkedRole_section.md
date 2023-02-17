# Delete an IAM service\-linked role using an AWS SDK<a name="example_iam_DeleteServiceLinkedRole_section"></a>

The following code examples show how to delete an IAM service\-linked role\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ Go ]

**SDK for Go V2**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
// RoleWrapper encapsulates AWS Identity and Access Management (IAM) role actions
// used in the examples.
// It contains an IAM service client that is used to perform role actions.
type RoleWrapper struct {
	IamClient *iam.Client
}



// DeleteServiceLinkedRole deletes a service-linked role.
func (wrapper RoleWrapper) DeleteServiceLinkedRole(roleName string) error {
	_, err := wrapper.IamClient.DeleteServiceLinkedRole(context.TODO(), &iam.DeleteServiceLinkedRoleInput{
		RoleName: aws.String(roleName)},
	)
	if err != nil {
		log.Printf("Couldn't delete service-linked role %v. Here's why: %v\n", roleName, err)
	}
	return err
}
```
+  For API details, see [DeleteServiceLinkedRole](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DeleteServiceLinkedRole) in *AWS SDK for Go API Reference*\. 

------
#### [ Ruby ]

**SDK for Ruby**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
  

```
  # Deletes a service-linked role from the account.
  #
  # @param role [Aws::IAM::Role] The role to delete.
  def delete_service_linked_role(role)
    response = @iam_resource.client.delete_service_linked_role(role_name: role.name)
    task_id = response.deletion_task_id
    while true
      response = @iam_resource.client.get_service_linked_role_deletion_status(
        deletion_task_id: task_id)
      status = response.status
      puts("Deletion of #{role.name} #{status}.")
      if %w(SUCCEEDED FAILED).include?(status)
        break
      else
        sleep(3)
      end
    end
rescue Aws::Errors::ServiceError => e
  # If AWS has not yet fully propagated the role, it deletes the role but
  # returns NoSuchEntity.
  if e.code != "NoSuchEntity"
    puts("Couldn't delete #{role.name}. Here's why:")
    puts("\t#{e.code}: #{e.message}")
    raise
  end
  end
```
+  For API details, see [DeleteServiceLinkedRole](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeleteServiceLinkedRole) in *AWS SDK for Ruby API Reference*\. 

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
  

```
pub async fn delete_service_linked_role(
    client: &iamClient,
    role_name: &str,
) -> Result<(), iamError> {
    client
        .delete_service_linked_role()
        .role_name(role_name)
        .send()
        .await?;

    Ok(())
}
```
+  For API details, see [DeleteServiceLinkedRole](https://docs.rs/releases/search?query=aws-sdk) in *AWS SDK for Rust API reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.