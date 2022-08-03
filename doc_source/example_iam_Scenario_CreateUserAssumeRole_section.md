# Create an IAM user and assume a role with AWS STS using an AWS SDK<a name="example_iam_Scenario_CreateUserAssumeRole_section"></a>

The following code examples show how to:
+ Create a user who has no permissions\.
+ Create a role that grants permission to list Amazon S3 buckets for the account\.
+ Add a policy to let the user assume the role\.
+ Assume the role and list Amazon S3 buckets using temporary credentials\.
+ Delete the policy, role, and user\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ \.NET ]

**AWS SDK for \.NET**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/dotnetv3/IAM/IAM_Basics_Scenario#code-examples)\. 
  

```
    using System;
    using System.IO;
    using System.Threading.Tasks;
    using Amazon;
    using Amazon.IdentityManagement;
    using Amazon.IdentityManagement.Model;
    using Amazon.S3;
    using Amazon.SecurityToken;
    using Amazon.SecurityToken.Model;

    public class IAM_Basics
    {
        // Values needed for user, role, and policies.
        private const string UserName = "example-user";
        private const string S3PolicyName = "s3-list-buckets-policy";
        private const string RoleName = "temporary-role";
        private const string AssumePolicyName = "sts-trust-user";

        private static readonly RegionEndpoint Region = RegionEndpoint.USEast2;

        public static async Task Main()
        {
            DisplayInstructions();

            // Create the IAM client object.
            var client = new AmazonIdentityManagementServiceClient(Region);

            // First create a user. By default, the new user has
            // no permissions.
            Console.WriteLine($"Creating a new user with user name: {UserName}.");
            var user = await CreateUserAsync(client, UserName);
            var userArn = user.Arn;
            Console.WriteLine($"Successfully created user: {UserName} with ARN: {userArn}.");

            // Create an AccessKey for the user.
            var accessKey = await CreateAccessKeyAsync(client, UserName);

            var accessKeyId = accessKey.AccessKeyId;
            var secretAccessKey = accessKey.SecretAccessKey;

            // Try listing the Amazon Simple Storage Service (Amazon S3)
            // buckets. This should fail at this point because the user doesn't
            // have permissions to perform this task.
            var s3Client1 = new AmazonS3Client(accessKeyId, secretAccessKey);
            await ListMyBucketsAsync(s3Client1);

            // Define a role policy document that allows the new user
            // to assume the role.
            // string assumeRolePolicyDocument = File.ReadAllText("assumePolicy.json");
            string assumeRolePolicyDocument = "{" +
                "\"Version\": \"2012-10-17\"," +
                "\"Statement\": [{" +
                "\"Effect\": \"Allow\"," +
                "\"Principal\": {" +
                $"	\"AWS\": \"{userArn}\"" +
                "}," +
                    "\"Action\": \"sts:AssumeRole\"" +
                "}]" +
            "}";

            // Permissions to list all buckets.
            string policyDocument = "{" +
                "\"Version\": \"2012-10-17\"," +
                "	\"Statement\" : [{" +
                    "	\"Action\" : [\"s3:ListAllMyBuckets\"]," +
                    "	\"Effect\" : \"Allow\"," +
                    "	\"Resource\" : \"*\"" +
                "}]" +
            "}";

            // Create the role to allow listing the S3 buckets. Role names are
            // not case sensitive and must be unique to the account for which it
            // is created.
            var role = await CreateRoleAsync(client, RoleName, assumeRolePolicyDocument);
            var roleArn = role.Arn;

            // Create a policy with permissions to list S3 buckets
            var policy = await CreatePolicyAsync(client, S3PolicyName, policyDocument);

            // Wait 15 seconds for the policy to be created.
            WaitABit(15, "Waiting for the policy to be available.");

            // Attach the policy to the role you created earlier.
            await AttachRoleAsync(client, policy.Arn, RoleName);

            // Wait 15 seconds for the role to be updated.
            Console.WriteLine();
            WaitABit(15, "Waiting to time for the policy to be attached.");

            // Use the AWS Security Token Service (AWS STS) to have the user
            // assume the role we created.
            var stsClient = new AmazonSecurityTokenServiceClient(accessKeyId, secretAccessKey);

            // Wait for the new credentials to become valid.
            WaitABit(10, "Waiting for the credentials to be valid.");

            var assumedRoleCredentials = await AssumeS3RoleAsync(stsClient, "temporary-session", roleArn);

            // Try again to list the buckets using the client created with
            // the new user's credentials. This time, it should work.
            var s3Client2 = new AmazonS3Client(assumedRoleCredentials);

            await ListMyBucketsAsync(s3Client2);

            // Now clean up all the resources used in the example.
            await DeleteResourcesAsync(client, accessKeyId, UserName, policy.Arn, RoleName);

            Console.WriteLine("IAM Demo completed.");
        }


        /// <summary>
        /// Create a new IAM user.
        /// </summary>
        /// <param name="client">The initialized IAM client object.</param>
        /// <param name="userName">A string representing the user name of the
        /// new user.</param>
        /// <returns>The newly created user.</returns>
        public static async Task<User> CreateUserAsync(
            AmazonIdentityManagementServiceClient client,
            string userName)
        {
            var request = new CreateUserRequest
            {
                UserName = userName,
            };

            var response = await client.CreateUserAsync(request);

            return response.User;
        }



        /// <summary>
        /// Create a new AccessKey for the user.
        /// </summary>
        /// <param name="client">The initialized IAM client object.</param>
        /// <param name="userName">The name of the user for whom to create the key.</param>
        /// <returns>A new IAM access key for the user.</returns>
        public static async Task<AccessKey> CreateAccessKeyAsync(
            AmazonIdentityManagementServiceClient client,
            string userName)
        {
            var request = new CreateAccessKeyRequest
            {
                UserName = userName,
            };

            var response = await client.CreateAccessKeyAsync(request);

            if (response.AccessKey is not null)
            {
                Console.WriteLine($"Successfully created Access Key for {userName}.");
            }

            return response.AccessKey;
        }



        /// <summary>
        /// Create a policy to allow a user to list the buckets in an account.
        /// </summary>
        /// <param name="client">The initialized IAM client object.</param>
        /// <param name="policyName">The name of the poicy to create.</param>
        /// <param name="policyDocument">The permissions policy document.</param>
        /// <returns>The newly created ManagedPolicy object.</returns>
        public static async Task<ManagedPolicy> CreatePolicyAsync(
            AmazonIdentityManagementServiceClient client,
            string policyName,
            string policyDocument)
        {
            var request = new CreatePolicyRequest
            {
                PolicyName = policyName,
                PolicyDocument = policyDocument,
            };

            var response = await client.CreatePolicyAsync(request);

            return response.Policy;
        }



        /// <summary>
        /// Attach the policy to the role so that the user can assume it.
        /// </summary>
        /// <param name="client">The initialized IAM client object.</param>
        /// <param name="policyArn">The ARN of the policy to attach.</param>
        /// <param name="roleName">The name of the role to attach the policy to.</param>
        public static async Task AttachRoleAsync(
            AmazonIdentityManagementServiceClient client,
            string policyArn,
            string roleName)
        {
            var request = new AttachRolePolicyRequest
            {
                PolicyArn = policyArn,
                RoleName = roleName,
            };

            var response = await client.AttachRolePolicyAsync(request);

            if (response.HttpStatusCode == System.Net.HttpStatusCode.OK)
            {
                Console.WriteLine("Successfully attached the policy to the role.");
            }
            else
            {
                Console.WriteLine("Could not attach the policy.");
            }
        }



        /// <summary>
        /// Create a new IAM role which we can attach to a user.
        /// </summary>
        /// <param name="client">The initialized IAM client object.</param>
        /// <param name="roleName">The name of the IAM role to create.</param>
        /// <param name="rolePermissions">The permissions which the role will have.</param>
        /// <returns>A Role object representing the newly created role.</returns>
        public static async Task<Role> CreateRoleAsync(
            AmazonIdentityManagementServiceClient client,
            string roleName,
            string rolePermissions)
        {
            var request = new CreateRoleRequest
            {
                RoleName = roleName,
                AssumeRolePolicyDocument = rolePermissions,
            };

            var response = await client.CreateRoleAsync(request);

            return response.Role;
        }



        /// <summary>
        /// List the Amazon S3 buckets owned by the user.
        /// </summary>
        /// <param name="accessKeyId">The access key Id for the user.</param>
        /// <param name="secretAccessKey">The Secret access key for the user.</param>
        public static async Task ListMyBucketsAsync(AmazonS3Client client)
        {
            Console.WriteLine("\nPress <Enter> to list the S3 buckets using the new user.\n");
            Console.ReadLine();

            try
            {
                // Get the list of buckets accessible by the new user.
                var response = await client.ListBucketsAsync();

                // Loop through the list and print each bucket's name
                // and creation date.
                Console.WriteLine(new string('-', 80));
                Console.WriteLine("Listing S3 buckets:\n");
                response.Buckets
                    .ForEach(b => Console.WriteLine($"Bucket name: {b.BucketName}, created on: {b.CreationDate}"));
            }
            catch (AmazonS3Exception ex)
            {
                // Something else went wrong. Display the error message.
                Console.WriteLine($"Error: {ex.Message}");
            }

            Console.WriteLine("Press <Enter> to continue.");
            Console.ReadLine();
        }



        /// <summary>
        /// Have the user assume the role that allows the role to be used to
        /// list all S3 buckets.
        /// </summary>
        /// <param name="client">An initialized AWS STS client object.</param>
        /// <param name="roleSession">The name of the session where the role
        /// assumption will be active.</param>
        /// <param name="roleToAssume">The Amazon Resource Name (ARN) of the
        /// role to assume.</param>
        /// <returns>The AssumedRoleUser object needed to perform the list
        /// buckets procedure.</returns>
        public static async Task<Credentials> AssumeS3RoleAsync(
            AmazonSecurityTokenServiceClient client,
            string roleSession,
            string roleToAssume)
        {
            // Create the request to use with the AssumeRoleAsync call.
            var request = new AssumeRoleRequest()
            {
                RoleSessionName = roleSession,
                RoleArn = roleToAssume,
            };

            var response = await client.AssumeRoleAsync(request);

            return response.Credentials;
        }



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


        /// <summary>
        /// Display a countdown and wait for a number of seconds.
        /// </summary>
        /// <param name="numSeconds">The number of seconds to wait.</param>
        public static void WaitABit(int numSeconds, string msg)
        {
            Console.WriteLine(msg);

            // Wait for the requested number of seconds.
            for (int i = numSeconds; i > 0; i--)
            {
                System.Threading.Thread.Sleep(1000);
                Console.Write($"{i}...");
            }

            Console.WriteLine("\n\nPress <Enter> to continue.");
            Console.ReadLine();
        }

        /// <summary>
        /// Shows the a description of the features of the program.
        /// </summary>
        public static void DisplayInstructions()
        {
            var separator = new string('-', 80);

            Console.WriteLine(separator);
            Console.WriteLine("IAM Basics");
            Console.WriteLine("This application uses the basic features of the AWS Identity and Access");
            Console.WriteLine("Management (IAM) creating, managing, and controlling access to resources for");
            Console.WriteLine("users. The application was created using the AWS SDK for .NET version 3.7 and");
            Console.WriteLine(".NET Core 5. The application performs the following actions:");
            Console.WriteLine();
            Console.WriteLine("1. Creates a user with no permissions");
            Console.WriteLine("2. Creates a rolw and policy that grants s3:ListAllMyBuckets permission");
            Console.WriteLine("3. Grants the user permission to assume the role");
            Console.WriteLine("4. Creates an Amazon Simple Storage Service (Amazon S3) client and tries");
            Console.WriteLine("   to list buckets. (This should fail.)");
            Console.WriteLine("5. Gets temporary credentials by assuming the role.");
            Console.WriteLine("6. Creates an Amazon S3 client object with the temporary credentials and");
            Console.WriteLine("   lists the buckets. (This time it should work.)");
            Console.WriteLine("7. Deletes all of the resources created.");
            Console.WriteLine(separator);
            Console.WriteLine("Press <Enter> to continue.");
            Console.ReadLine();
        }
    }
```
+ For API details, see the following topics in *AWS SDK for \.NET API Reference*\.
  + [AttachRolePolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/AttachRolePolicy)
  + [CreateAccessKey](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/CreateAccessKey)
  + [CreatePolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/CreatePolicy)
  + [CreateRole](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/CreateRole)
  + [CreateUser](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/CreateUser)
  + [DeleteAccessKey](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DeleteAccessKey)
  + [DeletePolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DeletePolicy)
  + [DeleteRole](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DeleteRole)
  + [DeleteUser](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DeleteUser)
  + [DeleteUserPolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DeleteUserPolicy)
  + [DetachRolePolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/DetachRolePolicy)
  + [PutUserPolicy](https://docs.aws.amazon.com/goto/DotNetSDKV3/iam-2010-05-08/PutUserPolicy)

------
#### [ Go ]

**SDK for Go V2**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/gov2/iam#code-examples)\. 
  

```
package main

import (
	"context"
	"errors"
	"fmt"
	"time"

	"github.com/aws/aws-sdk-go-v2/aws"
	"github.com/aws/aws-sdk-go-v2/config"
	"github.com/aws/aws-sdk-go-v2/credentials"
	"github.com/aws/aws-sdk-go-v2/credentials/stscreds"
	"github.com/aws/aws-sdk-go-v2/service/iam"
	"github.com/aws/aws-sdk-go-v2/service/iam/types"
	"github.com/aws/aws-sdk-go-v2/service/s3"
	"github.com/aws/aws-sdk-go-v2/service/sts"
	"github.com/aws/smithy-go"
)

/*
This is a basic scenario for using AWS Identity and Access Management (IAM) and AWS Security Token Service (STS).

This example will do the following:

 *   Create a user that has no permissions.
 *   Create a role and policy that grant s3:ListAllMyBuckets permission.
 *   Grant the user permission to assume the role.
 *   Create an S3 client object as the user and try to list buckets (this should fail).
 *   Get temporary credentials by assuming the role.
 *   Create an S3 client object with the temporary credentials and list the buckets (this should succeed).
 *   Delete all the resources.

 */

const (
	scenario_UserName               = "ExampleUser123"
	scenario_BucketListerRoleName   = "BucketListerRole"
	scenario_BucketListerPolicyName = "BucketListerListMyBucketsPolicy"
)

func scenario() {

	cfg, err := config.LoadDefaultConfig(context.Background())

	if err != nil {
		panic("Couldn't load a configuration")
	}

	iamSvc := iam.NewFromConfig(cfg)

	fmt.Println("⏺️ Create user")

	var userInfo types.User

	user, err := iamSvc.CreateUser(context.Background(), &iam.CreateUserInput{
		UserName: aws.String(scenario_UserName),
	})

	if err != nil {

		var existsAlready *types.EntityAlreadyExistsException
		if errors.As(err, &existsAlready) {
			// The user possibly exists.
			// Check if the user actually exists within IAM.
			uuser, err := iamSvc.GetUser(context.Background(), &iam.GetUserInput{UserName: aws.String(scenario_UserName)})
			if err != nil {
				panic("Can't get user: " + err.Error())
			} else {
				// Make sure the user info is set for later.
				userInfo = *uuser.User
				fmt.Println("User already existed...")
			}
		} else {
			fmt.Println("Couldn't create user! " + err.Error())
		}
	} else {
		userInfo = *user.User
	}

	fmt.Printf("User %s has id %s\n", scenario_UserName, *userInfo.Arn)

	fmt.Println("⏺️ Create access key")

	creds, err := iamSvc.CreateAccessKey(context.Background(), &iam.CreateAccessKeyInput{
		UserName: aws.String(scenario_UserName),
	})

	if err != nil {
		panic("Couldn't create credentials for a user! " + err.Error())
	}

	akId := *creds.AccessKey.AccessKeyId
	sakId := *creds.AccessKey.SecretAccessKey

	fmt.Printf("🗝️ CREDS: accessKeyId(%s) Secretkey(%s)\n", akId, sakId)

	// Grant the user the ability to assume the role.

	fmt.Println("💤 waiting for a few moments for keys to become available")

	time.Sleep(10 * time.Second)

	fmt.Println("⏺️ Create the bucket lister role")
	bucketListerRole, err := iamSvc.CreateRole(context.Background(), &iam.CreateRoleInput{
		RoleName: aws.String(scenario_BucketListerRoleName),
		AssumeRolePolicyDocument: aws.String(`{
			"Version": "2012-10-17",
			"Statement": [
			  {
				"Effect": "Allow",
				"Principal": {
				  "AWS":"` + (*userInfo.Arn) + `"
				},
				"Action": "sts:AssumeRole"
			  }
			]
		  }`),
		Description: aws.String("Role to let users list their buckets."),
	})
	var bucketListerRoleArn string
	if err != nil {
		// Check to see if the role exists.
		var existsException *types.EntityAlreadyExistsException
		if errors.As(err, &existsException) {
			// Check if we can look up the role as it stands already
			tRole, err := iamSvc.GetRole(context.Background(), &iam.GetRoleInput{
				RoleName: aws.String(scenario_BucketListerRoleName),
			})
			if err != nil {
				// Told it already exists, but now it's gone.
				panic("Couldn't find seemingly extant role: " + err.Error())
			} else {
				bucketListerRoleArn = *tRole.Role.Arn
			}
		} else {
			panic("Couldn't create role! " + err.Error())
		}
	} else {
		bucketListerRoleArn = *bucketListerRole.Role.Arn
	}

	fmt.Printf("✔️ The ARN for the bucket lister role is %s", bucketListerRoleArn)

	fmt.Println("⏺️ Create policy to allow bucket listing")
	bucketAllowPolicy := aws.String(`{
		"Version": "2012-10-17",
		"Statement": [
		  {
			"Sid": "Stmt1646154730759",
			"Action": [
			  "s3:ListAllMyBuckets"
			],
			"Effect": "Allow",
			"Resource": "*"}]}`)

	var bucketListerPolicyArn string
	bucketListerPolicy, err := iamSvc.CreatePolicy(context.Background(), &iam.CreatePolicyInput{
		PolicyName:     aws.String(scenario_BucketListerPolicyName),
		PolicyDocument: bucketAllowPolicy,
		Description:    aws.String("Allow user to list their own buckets"),
	})

	if err != nil {
		var existsException *types.EntityAlreadyExistsException
		if errors.As(err, &existsException) {

			stsClient := sts.NewFromConfig(cfg)
			mCallerId, _ := stsClient.GetCallerIdentity(context.Background(), &sts.GetCallerIdentityInput{})

			mpolicyArn := fmt.Sprintf("arn:aws:iam::%s:policy/%s", *mCallerId.Account, scenario_BucketListerPolicyName)

			_, err := iamSvc.GetPolicy(context.Background(), &iam.GetPolicyInput{
				PolicyArn: &mpolicyArn,
			})
			if err != nil {
				panic("Failed to find policy by arn(" + mpolicyArn + ") -> " + err.Error())
			}
			bucketListerPolicyArn = mpolicyArn

		} else {
			panic("Couldn't create policy! " + err.Error())
		}
	} else {
		bucketListerPolicyArn = *bucketListerPolicy.Policy.Arn
	}

	fmt.Println("⏺️ Attach role policy")

	_, err = iamSvc.AttachRolePolicy(context.Background(), &iam.AttachRolePolicyInput{
		PolicyArn: &bucketListerPolicyArn,
		RoleName:  aws.String(scenario_BucketListerRoleName),
	})

	if err != nil {
		fmt.Println("Couldn't attach policy to role! " + err.Error())
	}

	fmt.Printf("⭕  attached role policy ")

	fmt.Println("💤 waiting for a few moments for keys to become available")

	time.Sleep(10 * time.Second)

	// Create an S3 client that acts as the user.
	userConfig, err := config.LoadDefaultConfig(context.TODO(),
		// Use credentials created earlier.
		config.WithCredentialsProvider(credentials.StaticCredentialsProvider{
			Value: aws.Credentials{
				AccessKeyID: akId, SecretAccessKey: sakId,
				Source: "Example user creds",
			},
		}))
	if err != nil {
		panic("Couldn't create config for new credentials! " + err.Error())
	} else {
		creds, err := userConfig.Credentials.Retrieve(context.Background())
		if err != nil {
			panic("Couldn't get credentials for our new config, something is wrong: " + err.Error())
		}
		fmt.Printf("-> config creds are %s %s\n", creds.AccessKeyID, creds.SecretAccessKey)
	}

	s3Client := s3.NewFromConfig(userConfig)
	// Attempt to list buckets.
	_, err = s3Client.ListBuckets(context.Background(), &s3.ListBucketsInput{})

	if err == nil {
		fmt.Println("Call to s3:ListBuckets was not denied (unexpected!)")
	} else {
		var oe smithy.APIError
		if errors.As(err, &oe) && (oe.ErrorCode() == "AccessDenied") {
			fmt.Println("Couldn't list buckets (expected!)")
		} else {
			panic("unexpected error: " + err.Error())
		}
	}

	stsClient := sts.NewFromConfig(userConfig)
	roleCreds := stscreds.NewAssumeRoleProvider(stsClient, bucketListerRoleArn)

	tmpCreds, err := roleCreds.Retrieve(context.Background())
	if err != nil {
		fmt.Println("couldn't get role creds: " + err.Error())
	} else {
		fmt.Printf("role creds: %s %v\n\n", tmpCreds.AccessKeyID, tmpCreds.Expires)
	}

	roleConfig, err := config.LoadDefaultConfig(context.Background(),
		config.WithCredentialsProvider(roleCreds),
	)
	if err != nil {
		panic("Couldn't create config with assumed role! " + err.Error())
	}

	roleS3client := s3.NewFromConfig(roleConfig)

	mybuckets, err := roleS3client.ListBuckets(context.Background(), &s3.ListBucketsInput{})

	if err != nil {
		panic("Couldn't list buckets while assuming role that allows this: " + err.Error())
	} else {
		fmt.Println("Buckets owned by the user....")
		for _, bucket := range mybuckets.Buckets {
			fmt.Printf("%s -> %s\n", *bucket.Name, bucket.CreationDate)
		}
	}

	// ---- Clean up ----

	// Delete the user's access keys.

	fmt.Println("cleanup: Delete created access key")
	_, _ = iamSvc.DeleteAccessKey(context.Background(), &iam.DeleteAccessKeyInput{
		AccessKeyId: &akId,
		UserName:    aws.String(scenario_UserName),
	})

	// Delete the user.
	fmt.Println("cleanup: delete the user we created")
	_, err = iamSvc.DeleteUser(context.Background(), &iam.DeleteUserInput{UserName: aws.String(scenario_UserName)})
	if err != nil {
		fmt.Println("Couldn't delete user! " + err.Error())
	}

	// Detach the role policy.

	fmt.Println("cleanup: Detach the policy from the role")
	_, err = iamSvc.DetachRolePolicy(context.Background(), &iam.DetachRolePolicyInput{
		RoleName:  aws.String(scenario_BucketListerRoleName),
		PolicyArn: &bucketListerPolicyArn,
	})

	if err != nil {
		fmt.Println("Couldn't detach role policy from role " + err.Error())
	}

	// Delete the role.
	fmt.Println("cleanup: Remove the role")
	_, err = iamSvc.DeleteRole(context.Background(), &iam.DeleteRoleInput{
		RoleName: aws.String(scenario_BucketListerRoleName),
	})
	if err != nil {
		fmt.Println("Couldn't delete role! " + err.Error())
	}

	// Delete the policy.
	fmt.Println("cleanup: delete the policy")
	_, err = iamSvc.DeletePolicy(context.Background(), &iam.DeletePolicyInput{
		PolicyArn: &bucketListerPolicyArn,
	})
	if err != nil {
		fmt.Println("couldn't delete policy!")
	}

	fmt.Println("done!")
}
```
+ For API details, see the following topics in *AWS SDK for Go API Reference*\.
  + [AttachRolePolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.AttachRolePolicy)
  + [CreateAccessKey](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.CreateAccessKey)
  + [CreatePolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.CreatePolicy)
  + [CreateRole](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.CreateRole)
  + [CreateUser](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.CreateUser)
  + [DeleteAccessKey](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DeleteAccessKey)
  + [DeletePolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DeletePolicy)
  + [DeleteRole](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DeleteRole)
  + [DeleteUser](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DeleteUser)
  + [DeleteUserPolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DeleteUserPolicy)
  + [DetachRolePolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.DetachRolePolicy)
  + [PutUserPolicy](https://pkg.go.dev/github.com/aws/aws-sdk-go-v2/service/iam#Client.PutUserPolicy)

------
#### [ Java ]

**SDK for Java 2\.x**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javav2/example_code/iam#readme)\. 
Create functions that wrap IAM user actions\.  

```
public class IAMScenario {

    public static final String PolicyDocument =
            "{" +
                    "  \"Version\": \"2012-10-17\"," +
                    "  \"Statement\": [" +
                    "    {" +
                    "        \"Effect\": \"Allow\"," +
                    "        \"Action\": [" +
                    "            \"s3:*\"" +
                    "       ]," +
                    "       \"Resource\": \"*\"" +
                    "    }" +
                    "   ]" +
                    "}";

    public static void main(String[] args) throws Exception {

        final String usage = "\n" +
            "Usage:\n" +
            "    <username> <policyName> <roleName> <roleSessionName> <fileLocation> <bucketName> \n\n" +
            "Where:\n" +
            "    username - The name of the IAM user to create. \n\n" +
            "    policyName - The name of the policy to create. \n\n" +
            "    roleName - The name of the role to create. \n\n" +
            "    roleSessionName - The name of the session required for the assumeRole operation. \n\n" +
            "    fileLocation - The file location to the JSON required to create the role (see Readme). \n\n" +
            "    bucketName - The name of the Amazon S3 bucket from which objects are read. \n\n" ;

        if (args.length != 6) {
            System.out.println(usage);
            System.exit(1);
        }

        String userName = args[0];
        String policyName = args[1];
        String roleName = args[2];
        String roleSessionName = args[3];
        String fileLocation = args[4];
        String bucketName = args[5];

        Region region = Region.AWS_GLOBAL;
        IamClient iam = IamClient.builder()
            .region(region)
            .credentialsProvider(ProfileCredentialsProvider.create())
            .build();

        // Create the IAM user.
        Boolean createUser = createIAMUser(iam, userName);

       if (createUser) {
           System.out.println(userName + " was successfully created.");
           String polArn = createIAMPolicy(iam, policyName);
           System.out.println("The policy " + polArn + " was successfully created.");
           String roleArn = createIAMRole(iam, roleName, fileLocation);
           System.out.println(roleArn + " was successfully created.");
           attachIAMRolePolicy(iam, roleName, polArn);

           System.out.println("*** Wait for 1 MIN so the resource is available");
           TimeUnit.MINUTES.sleep(1);
           assumeGivenRole(roleArn, roleSessionName, bucketName);

           System.out.println("*** Getting ready to delete the AWS resources");
           deleteRole(iam, roleName, polArn);
           deleteIAMUser(iam, userName);
           System.out.println("This IAM Scenario has successfully completed");
       } else {
           System.out.println(userName +" was not successfully created.");
       }
    }

    public static Boolean createIAMUser(IamClient iam, String username ) {

        try {
            // Create an IamWaiter object
            IamWaiter iamWaiter = iam.waiter();
            CreateUserRequest request = CreateUserRequest.builder()
                .userName(username)
                .build();

            // Wait until the user is created.
            CreateUserResponse response = iam.createUser(request);
            GetUserRequest userRequest = GetUserRequest.builder()
                .userName(response.user().userName())
                .build();

            WaiterResponse<GetUserResponse> waitUntilUserExists = iamWaiter.waitUntilUserExists(userRequest);
            waitUntilUserExists.matched().response().ifPresent(System.out::println);
            return true;

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
        return false;
    }

    public static String createIAMRole(IamClient iam, String rolename, String fileLocation ) throws Exception {

        try {
            JSONObject jsonObject = (JSONObject) readJsonSimpleDemo(fileLocation);
            CreateRoleRequest request = CreateRoleRequest.builder()
                .roleName(rolename)
                .assumeRolePolicyDocument(jsonObject.toJSONString())
                .description("Created using the AWS SDK for Java")
                .build();

            CreateRoleResponse response = iam.createRole(request);
            System.out.println("The ARN of the role is "+response.role().arn());
            return response.role().arn();

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
        return "";
    }

    public static String createIAMPolicy(IamClient iam, String policyName ) {

        try {
            // Create an IamWaiter object.
            IamWaiter iamWaiter = iam.waiter();
            CreatePolicyRequest request = CreatePolicyRequest.builder()
                .policyName(policyName)
                .policyDocument(PolicyDocument).build();

            CreatePolicyResponse response = iam.createPolicy(request);

            // Wait until the policy is created.
            GetPolicyRequest polRequest = GetPolicyRequest.builder()
                .policyArn(response.policy().arn())
                .build();

            WaiterResponse<GetPolicyResponse> waitUntilPolicyExists = iamWaiter.waitUntilPolicyExists(polRequest);
            waitUntilPolicyExists.matched().response().ifPresent(System.out::println);
            return response.policy().arn();

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
        return "" ;
    }

    public static void attachIAMRolePolicy(IamClient iam, String roleName, String policyArn ) {

        try {
            ListAttachedRolePoliciesRequest request = ListAttachedRolePoliciesRequest.builder()
                .roleName(roleName)
                .build();

            ListAttachedRolePoliciesResponse response = iam.listAttachedRolePolicies(request);
            List<AttachedPolicy> attachedPolicies = response.attachedPolicies();

            String polArn;
            for (AttachedPolicy policy: attachedPolicies) {
                polArn = policy.policyArn();
                if (polArn.compareTo(policyArn)==0) {
                    System.out.println(roleName + " policy is already attached to this role.");
                    return;
                }
            }

            AttachRolePolicyRequest attachRequest = AttachRolePolicyRequest.builder()
                .roleName(roleName)
                .policyArn(policyArn)
                .build();

            iam.attachRolePolicy(attachRequest);
            System.out.println("Successfully attached policy " + policyArn + " to role " + roleName);

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }

    // Invoke an Amazon S3 operation using the Assumed Role.
    public static void assumeGivenRole(String roleArn, String roleSessionName, String bucketName) {

        StsClient stsClient = StsClient.builder()
            .region(Region.US_EAST_1)
            .build();

        try {
            AssumeRoleRequest roleRequest = AssumeRoleRequest.builder()
                .roleArn(roleArn)
                .roleSessionName(roleSessionName)
                .build();

            AssumeRoleResponse roleResponse = stsClient.assumeRole(roleRequest);
            Credentials myCreds = roleResponse.credentials();
            String key = myCreds.accessKeyId();
            String secKey = myCreds.secretAccessKey();
            String secToken = myCreds.sessionToken();

            // List all objects in an Amazon S3 bucket using the temp creds.
            Region region = Region.US_EAST_1;
            S3Client s3 = S3Client.builder()
                .credentialsProvider(StaticCredentialsProvider.create(AwsSessionCredentials.create(key, secKey, secToken)))
                .region(region)
                .build();

            System.out.println("Created a S3Client using temp credentials.");
            System.out.println("Listing objects in "+bucketName);
            ListObjectsRequest listObjects = ListObjectsRequest.builder()
                .bucket(bucketName)
                .build();

            ListObjectsResponse res = s3.listObjects(listObjects);
            List<S3Object> objects = res.contents();
            for (S3Object myValue : objects) {
                System.out.println("The name of the key is " + myValue.key());
                System.out.println("The owner is " + myValue.owner());
            }

        } catch (StsException e) {
            System.err.println(e.getMessage());
            System.exit(1);
        }
    }

    public static void deleteRole(IamClient iam, String roleName, String polArn) {

        try {
            // First the policy needs to be detached.
            DetachRolePolicyRequest rolePolicyRequest = DetachRolePolicyRequest.builder()
                .policyArn(polArn)
                .roleName(roleName)
                .build();

            iam.detachRolePolicy(rolePolicyRequest);

            // Delete the policy.
            DeletePolicyRequest request = DeletePolicyRequest.builder()
                .policyArn(polArn)
                .build();

            iam.deletePolicy(request);
            System.out.println("*** Successfully deleted "+polArn);

            // Delete the role.
            DeleteRoleRequest roleRequest = DeleteRoleRequest.builder()
                .roleName(roleName)
                .build();

            iam.deleteRole(roleRequest);
            System.out.println("*** Successfully deleted " +roleName);

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }

    public static void deleteIAMUser(IamClient iam, String userName) {

        try {
            DeleteUserRequest request = DeleteUserRequest.builder()
                .userName(userName)
                .build();

            iam.deleteUser(request);
            System.out.println("*** Successfully deleted " + userName);

        } catch (IamException e) {
            System.err.println(e.awsErrorDetails().errorMessage());
            System.exit(1);
        }
    }

    public static Object readJsonSimpleDemo(String filename) throws Exception {
        FileReader reader = new FileReader(filename);
        JSONParser jsonParser = new JSONParser();
        return jsonParser.parse(reader);
    }
}
```
+ For API details, see the following topics in *AWS SDK for Java 2\.x API Reference*\.
  + [AttachRolePolicy](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/AttachRolePolicy)
  + [CreateAccessKey](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/CreateAccessKey)
  + [CreatePolicy](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/CreatePolicy)
  + [CreateRole](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/CreateRole)
  + [CreateUser](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/CreateUser)
  + [DeleteAccessKey](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DeleteAccessKey)
  + [DeletePolicy](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DeletePolicy)
  + [DeleteRole](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DeleteRole)
  + [DeleteUser](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DeleteUser)
  + [DeleteUserPolicy](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DeleteUserPolicy)
  + [DetachRolePolicy](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/DetachRolePolicy)
  + [PutUserPolicy](https://docs.aws.amazon.com/goto/SdkForJavaV2/iam-2010-05-08/PutUserPolicy)

------
#### [ JavaScript ]

**SDK for JavaScript V3**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
Create the client\.  

```
// Create service client module using ES6 syntax.
import { IAMClient } from "@aws-sdk/client-iam";
// Set the AWS Region.
export const REGION = "REGION"; // For example, "us-east-1".
// Create an Amazon S3 service client object.
export const iamClient = new IAMClient({ region: REGION });
```
Create an IAM user and a role that grants permission to list Amazon S3 buckets\. The user has rights only to assume the role\. After assuming the role, use temporary credentials to list buckets for the account\.  

```
// Import required AWS SDK clients and commands for Node.js.
import { iamClient, REGION } from "../libs/iamClient.js"; // Helper function that creates an IAM service client module.
import {
  CreateUserCommand,
  CreateAccessKeyCommand,
  CreatePolicyCommand,
  CreateRoleCommand,
  AttachRolePolicyCommand,
  AttachUserPolicyCommand,
  DeleteAccessKeyCommand,
  DeleteUserCommand,
  DeleteRoleCommand,
  DeletePolicyCommand,
  DetachUserPolicyCommand,
  DetachRolePolicyCommand,
} from "@aws-sdk/client-iam";
import { ListBucketsCommand, S3Client } from "@aws-sdk/client-s3";
import { AssumeRoleCommand, STSClient } from "@aws-sdk/client-sts";

if (process.argv.length < 6) {
  console.log(
      "Usage: node iam_basics.js <user name> <s3 policy name> <role name> <assume policy name>\n" +
      "Example: node iam_basics.js test-user my-s3-policy my-iam-role my-assume-role"
  );
}
// Set the parameters.
const region = REGION;
const userName = process.argv[2];
const s3_policy_name = process.argv[3];
const role_name = process.argv[4];
const assume_policy_name = process.argv[5];

// Helper function to delay running the code while the AWS service calls wait for responses.
function wait(ms) {
  var start = Date.now();
  var end = start
  while (end < start + ms){
    end = Date.now()
  }
}

export const run = async (
    userName,
    s3_policy_name,
    role_name,
    assume_policy_name
) => {
  try {
    // Create a new user.
    const user_params = { UserName: userName };
    console.log("\nCreating a user name " + user_params.UserName + "...\n");
    const data = await iamClient.send(
        new CreateUserCommand({ UserName: userName })
    );
    const user_arn = data.User.Arn;
    const user_name = data.User.UserName;
    console.log(
        "User with name" + user_name + " and ARN " + user_arn + " created."
    );
    try {
      // Create access keys for the new user.
      console.log(
          "\nCreating access keys for " + user_params.UserName + "...\n"
      );
      const access_key_params = { UserName: user_name };
      const data = await iamClient.send(
          new CreateAccessKeyCommand(access_key_params)
      );
      console.log("Success. Access key created: ", data.AccessKey.AccessKeyId);
      var myAccessKey = data.AccessKey.AccessKeyId;
      var mySecretAccessKey = data.AccessKey.SecretAccessKey;

      try {
        // Attempt to list S3 buckets.
        console.log(
            "\nWaiting 10 seconds for user and access keys to be created...\n"
        );
        wait(10000);
        console.log(
            "Attempt to list S3 buckets with the new user (without permissions)...\n"
        );
        // Use the credentials for the new user that you created.
        var user_creds = {
          accessKeyId: myAccessKey,
          secretAccessKey: mySecretAccessKey,
        };
        const s3Client = new S3Client({
          credentials: user_creds,
          region: region,
        });
        await s3Client.send(new ListBucketsCommand({}));
      } catch (err) {
        console.log(
            "Error. As expected the new user has no permissions to list buckets. ",
            err.stack
        );
        console.log(
            "\nCreating policy to allow the new user to list all buckets, and to assume an STS role...\n"
        );
        const myManagedPolicy = {
          Version: "2012-10-17",
          Statement: [
            {
              Effect: "Allow",
              Action: ["s3:ListAllMyBuckets", "sts:AssumeRole"],
              Resource: "*",
            },
          ],
        };
        const policy_params = {
          PolicyDocument: JSON.stringify(myManagedPolicy),
          PolicyName: s3_policy_name, // Name of the new policy.
        };
        const data = await iamClient.send(
            new CreatePolicyCommand(policy_params)
        );
        console.log(
            "Success. Policy created that allows listing of all S3 buckets.\n" +
            "Policy ARN: " +
            data.Policy.Arn +
            "\n" +
            "Policy name: " +
            data.Policy.PolicyName +
            "\n"
        );

        var s3_policy_arn = data.Policy.Arn;

        try {
          console.log(
              "\nCreating a role with a trust policy that lets the user assume the role....\n"
          );

          const role_json = {
            Version: "2012-10-17",
            Statement: [
              {
                Effect: "Allow",
                Principal: {
                  AWS: user_arn, // The ARN of the user.
                },
                Action: "sts:AssumeRole",
              },
            ],
          };
          const myJson = JSON.stringify(role_json);

          const role_params = {
            AssumeRolePolicyDocument: myJson, // Trust relationship policy document.
            Path: "/",
            RoleName: role_name // The name of the new role.
          };
          const data = await iamClient.send(new CreateRoleCommand(role_params));
          console.log("Success. Role created. Role Arn: ", data.Role.Arn);
          const role_arn = data.Role.Arn;
          try {
            console.log(
                "\nAttaching to the role the policy with permissions to list all buckets....\n"
            );
            const params = {
              PolicyArn: s3_policy_arn,
              RoleName: role_name,
            };
            await iamClient.send(new AttachRolePolicyCommand(params));
            console.log("Success. Policy attached successfully to role.");
            try {
              console.log(
                  "\nCreate a policy that enables the user to assume the role ....\n"
              );
              const myNewPolicy = {
                Version: "2012-10-17",
                Statement: [
                  {
                    Effect: "Allow",
                    Action: ["sts:AssumeRole"],
                    Resource: role_arn,
                  },
                ],
              };
              const policy_params = {
                PolicyDocument: JSON.stringify(myNewPolicy),
                PolicyName: assume_policy_name,
              };
              const data = await iamClient.send(
                  new CreatePolicyCommand(policy_params)
              );
              console.log(
                  "Success. Policy created. Policy ARN: " + data.Policy.Arn
              );

              const assume_policy_arn = data.Policy.Arn;
              try {
                console.log("\nAttaching the policy to the user.....\n");
                const attach_policy_to_user_params = {
                  PolicyArn: assume_policy_arn,
                  UserName: user_name,
                };
                const data = await iamClient.send(
                    new AttachUserPolicyCommand(attach_policy_to_user_params)
                );
                console.log(
                    "\nWaiting 10 seconds for policy to be attached...\n"
                );
                wait(10000);
                console.log(
                    "Success. Policy attached to user " + user_name + "."
                );
                try {
                  console.log(
                      "\nAssume for the user the role with permission to list all buckets....\n"
                  );
                  const assume_role_params = {
                    RoleArn: role_arn, //ARN_OF_ROLE_TO_ASSUME
                    RoleSessionName: "session1",
                    DurationSeconds: 900,
                  };
                  // Create an AWS STS client with the credentials for the user. Remember, the user has permissions to assume roles using AWS STS.
                  const stsClientWithUsersCreds = new STSClient({
                    credentials: user_creds,
                    region: REGION,
                  });

                  const data = await stsClientWithUsersCreds.send(
                      new AssumeRoleCommand(assume_role_params)
                  );
                  console.log(
                      "Success assuming role. Access key id is " +
                      data.Credentials.AccessKeyId +
                      "\n" +
                      "Secret access key is " +
                      data.Credentials.SecretAccessKey
                  );

                  const newAccessKey = data.Credentials.AccessKeyId;
                  const newSecretAccessKey = data.Credentials.SecretAccessKey;

                  console.log(
                      "\nWaiting 10 seconds for the user to assume the role with permission to list all buckets...\n"
                  );
                  wait(10000);
                  // Set the parameters for the temporary credentials. This grants permission to list S3 buckets.
                  var new_role_creds = {
                    accessKeyId: newAccessKey,
                    secretAccessKey: newSecretAccessKey,
                    sessionToken: data.Credentials.SessionToken,
                  };
                  try {
                    console.log(
                        "Listing the S3 buckets using the credentials of the assumed role... \n"
                    );
                    // Create an S3 client with the temporary credentials.
                    const s3ClientWithNewCreds = new S3Client({
                      credentials: new_role_creds,
                      region: REGION,
                    });
                    const data = await s3ClientWithNewCreds.send(
                        new ListBucketsCommand({})
                    );
                    console.log("Success. Your S3 buckets are:", data.Buckets);
                    try {
                      console.log(
                          "Detaching s3 policy from user " + userName + " ... \n"
                      );
                      const data = await iamClient.send(
                          new DetachUserPolicyCommand({
                            PolicyArn: assume_policy_arn,
                            UserName: userName,
                          })
                      );
                      console.log("Success, S3 policy detached from user.");
                      try {
                        console.log(
                            "Detaching role policy from " + role_name + " ... \n"
                        );
                        const data = await iamClient.send(
                            new DetachRolePolicyCommand({
                              PolicyArn: s3_policy_arn,
                              RoleName: role_name,
                            })
                        );
                        console.log(
                            "Success, assume policy detached from role."
                        );
                        try {
                          console.log("Deleting s3 policy ... \n");
                          const data = await iamClient.send(
                              new DeletePolicyCommand({
                                PolicyArn: s3_policy_arn,
                              })
                          );
                          console.log("Success, S3 policy deleted.");
                          try {
                            console.log("Deleting assume role policy ... \n");
                            const data = await iamClient.send(
                                new DeletePolicyCommand({
                                  PolicyArn: assume_policy_arn,
                                })
                            );
                            try {
                              console.log("Deleting access keys ... \n");
                              const data = await iamClient.send(
                                  new DeleteAccessKeyCommand({
                                    UserName: userName,
                                    AccessKeyId: myAccessKey,
                                  })
                              );
                              try {
                                console.log(
                                    "Deleting user " + user_name + " ... \n"
                                );
                                const data = await iamClient.send(
                                    new DeleteUserCommand({ UserName: userName })
                                );
                                console.log("Success, user deleted.");
                                try {
                                  console.log(
                                      "Deleting role " + role_name + " ... \n"
                                  );
                                  const data = await iamClient.send(
                                      new DeleteRoleCommand({
                                        RoleName: role_name,
                                      })
                                  );
                                  console.log("Success, role deleted.");
                                  return "Run successfully"; // For unit tests.
                                } catch (err) {
                                  console.log("Error deleting  role .", err);
                                }
                              } catch (err) {
                                console.log("Error deleting user.", err);
                              }
                            } catch (err) {
                              console.log("Error deleting access keys.", err);
                            }
                          } catch (err) {
                            console.log(
                                "Error detaching assume role policy from user.",
                                err
                            );
                          }
                        } catch (err) {
                          console.log("Error deleting role.", err);
                        }
                      } catch (err) {
                        console.log("Error deleting user.", err);
                      }
                    } catch (err) {
                      console.log("Error detaching S3 policy from role.", err);
                      process.exit(1);
                    }
                  } catch (err) {
                    console.log("Error listing S3 buckets.", err);
                    process.exit(1);
                  }
                } catch (err) {
                  console.log("Error assuming role.", err);
                  process.exit(1);
                }
              } catch (err) {
                console.log(
                    "Error adding permissions to user to assume role.",
                    err
                );
                process.exit(1);
              }
            } catch (err) {
              console.log("Error assuming role.", err);
              process.exit(1);
            }
          } catch (err) {
            console.log("Error creating policy. ", err);
            process.exit(1);
          }
        } catch (err) {
          console.log("Error attaching policy to role.", err);
          process.exit(1);
        }
      }
    } catch (err) {
      console.log("Error creating access keys. ", err);
      process.exit(1);
    }
  } catch (err) {
    console.log("Error creating user. ", err);
  }
};
run(userName, s3_policy_name, role_name, assume_policy_name);
```
+ For API details, see the following topics in *AWS SDK for JavaScript API Reference*\.
  + [AttachRolePolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/attachrolepolicycommand.html)
  + [CreateAccessKey](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/createaccesskeycommand.html)
  + [CreatePolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/createpolicycommand.html)
  + [CreateRole](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/createrolecommand.html)
  + [CreateUser](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/createusercommand.html)
  + [DeleteAccessKey](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/deleteaccesskeycommand.html)
  + [DeletePolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/deletepolicycommand.html)
  + [DeleteRole](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/deleterolecommand.html)
  + [DeleteUser](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/deleteusercommand.html)
  + [DeleteUserPolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/deleteuserpolicycommand.html)
  + [DetachRolePolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/detachrolepolicycommand.html)
  + [PutUserPolicy](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/putuserpolicycommand.html)

------
#### [ Kotlin ]

**SDK for Kotlin**  
This is prerelease documentation for a feature in preview release\. It is subject to change\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/kotlin/services/iam#code-examples)\. 
Create functions that wrap IAM user actions\.  

```
suspend fun main(args: Array<String>) {

    val usage = """
    Usage:
        <username> <policyName> <roleName> <roleSessionName> <fileLocation> <bucketName> 

    Where:
        username - The name of the IAM user to create. 
        policyName - The name of the policy to create. 
        roleName - The name of the role to create. 
        roleSessionName - The name of the session required for the assumeRole operation. 
        fileLocation - The file location to the JSON required to create the role (see Readme). 
        bucketName - The name of the Amazon S3 bucket from which objects are read. 
    """

    if (args.size != 6) {
        println(usage)
        exitProcess(1)
    }

    val userName = args[0]
    val policyName = args[1]
    val roleName = args[2]
    val roleSessionName = args[3]
    val fileLocation = args[4]
    val bucketName = args[5]

    createUser(userName)
    println("$userName was successfully created.")

    val polArn = createPolicy(policyName)
    println("The policy $polArn was successfully created.")

    val roleArn = createRole(roleName, fileLocation)
    println("$roleArn was successfully created.")
    attachRolePolicy(roleName, polArn)

    println("*** Wait for 1 MIN so the resource is available.")
    delay(60000)
    assumeGivenRole(roleArn, roleSessionName, bucketName)

    println("*** Getting ready to delete the AWS resources.")
    deleteRole(roleName, polArn)
    deleteUser(userName)
    println("This IAM Scenario has successfully completed.")
}

suspend fun createUser(usernameVal: String?): String? {

    val request = CreateUserRequest {
        userName = usernameVal
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        val response = iamClient.createUser(request)
        return response.user?.userName
    }
}

suspend fun createPolicy(policyNameVal: String?): String {

    val policyDocumentValue: String = "{" +
        "  \"Version\": \"2012-10-17\"," +
        "  \"Statement\": [" +
        "    {" +
        "        \"Effect\": \"Allow\"," +
        "        \"Action\": [" +
        "            \"s3:*\"" +
        "       ]," +
        "       \"Resource\": \"*\"" +
        "    }" +
        "   ]" +
        "}"

    val request = CreatePolicyRequest {
        policyName = policyNameVal
        policyDocument = policyDocumentValue
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        val response = iamClient.createPolicy(request)
        return response.policy?.arn.toString()
    }
}

suspend fun createRole(rolenameVal: String?, fileLocation: String?): String? {

    val jsonObject = fileLocation?.let { readJsonSimpleDemo(it) } as JSONObject

    val request = CreateRoleRequest {
        roleName = rolenameVal
        assumeRolePolicyDocument = jsonObject.toJSONString()
        description = "Created using the AWS SDK for Kotlin"
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        val response = iamClient.createRole(request)
        return response.role?.arn
    }
}

suspend fun attachRolePolicy(roleNameVal: String, policyArnVal: String) {

    val request = ListAttachedRolePoliciesRequest {
        roleName = roleNameVal
    }

    IamClient { region = "AWS_GLOBAL" }.use { iamClient ->
        val response = iamClient.listAttachedRolePolicies(request)
        val attachedPolicies = response.attachedPolicies

        // Ensure that the policy is not attached to this role.
        val checkStatus: Int
        if (attachedPolicies != null) {
            checkStatus = checkMyList(attachedPolicies, policyArnVal)
            if (checkStatus == -1)
                return
        }

        val policyRequest = AttachRolePolicyRequest {
            roleName = roleNameVal
            policyArn = policyArnVal
        }
        iamClient.attachRolePolicy(policyRequest)
        println("Successfully attached policy $policyArnVal to role $roleNameVal")
    }
}

fun checkMyList(attachedPolicies: List<AttachedPolicy>, policyArnVal: String): Int {

    for (policy in attachedPolicies) {
        val polArn = policy.policyArn.toString()

        if (polArn.compareTo(policyArnVal) == 0) {
            println("The policy is already attached to this role.")
            return -1
        }
    }
    return 0
}

suspend fun assumeGivenRole(roleArnVal: String?, roleSessionNameVal: String?, bucketName: String) {

    val stsClient = StsClient {
        region = "us-east-1"
    }

    val roleRequest = AssumeRoleRequest {
        roleArn = roleArnVal
        roleSessionName = roleSessionNameVal
    }

    val roleResponse = stsClient.assumeRole(roleRequest)
    val myCreds = roleResponse.credentials
    val key = myCreds?.accessKeyId
    val secKey = myCreds?.secretAccessKey
    val secToken = myCreds?.sessionToken

    val staticCredentials = StaticCredentialsProvider {
        accessKeyId = key
        secretAccessKey = secKey
        sessionToken = secToken
    }

    // List all objects in an Amazon S3 bucket using the temp creds.
    val s3 = S3Client {
        credentialsProvider = staticCredentials
        region = "us-east-1"
    }

    println("Created a S3Client using temp credentials.")
    println("Listing objects in $bucketName")

    val listObjects = ListObjectsRequest {
        bucket = bucketName
    }

    val response = s3.listObjects(listObjects)
    response.contents?.forEach { myObject ->
        println("The name of the key is ${myObject.key}")
        println("The owner is ${myObject.owner}")
    }
}

suspend fun deleteRole(roleNameVal: String, polArn: String) {

    val iam = IamClient { region = "AWS_GLOBAL" }

    // First the policy needs to be detached.
    val rolePolicyRequest = DetachRolePolicyRequest {
        policyArn = polArn
        roleName = roleNameVal
    }

    iam.detachRolePolicy(rolePolicyRequest)

    // Delete the policy.
    val request = DeletePolicyRequest {
        policyArn = polArn
    }

    iam.deletePolicy(request)
    println("*** Successfully deleted $polArn")

    // Delete the role.
    val roleRequest = DeleteRoleRequest {
        roleName = roleNameVal
    }

    iam.deleteRole(roleRequest)
    println("*** Successfully deleted $roleNameVal")
}

suspend fun deleteUser(userNameVal: String) {
    val iam = IamClient { region = "AWS_GLOBAL" }
    val request = DeleteUserRequest {
        userName = userNameVal
    }

    iam.deleteUser(request)
    println("*** Successfully deleted $userNameVal")
}

@Throws(java.lang.Exception::class)
fun readJsonSimpleDemo(filename: String): Any? {
    val reader = FileReader(filename)
    val jsonParser = JSONParser()
    return jsonParser.parse(reader)
}
```
+ For API details, see the following topics in *AWS SDK for Kotlin API reference*\.
  + [AttachRolePolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [CreateAccessKey](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [CreatePolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [CreateRole](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [CreateUser](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [DeleteAccessKey](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [DeletePolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [DeleteRole](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [DeleteUser](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [DeleteUserPolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [DetachRolePolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)
  + [PutUserPolicy](https://github.com/awslabs/aws-sdk-kotlin#generating-api-documentation)

------
#### [ PHP ]

**SDK for PHP**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/php/example_code/iam/iam_basics#code-examples)\. 
  

```
namespace Iam\Basics;

require 'vendor/autoload.php';

use Aws\Credentials\Credentials;
use Aws\S3\Exception\S3Exception;
use Aws\S3\S3Client;
use Aws\Sts\StsClient;
use Iam\IamService;

echo("--------------------------------------\n");
print("Welcome to the Amazon IAM getting started demo using PHP!\n");
echo("--------------------------------------\n");
$uuid = uniqid();
$service = new IamService();

$user = $service->createUser("iam_demo_user_$uuid");
echo "Created user with the arn: {$user['Arn']}\n";

$key = $service->createAccessKey($user['UserName']);
$assumeRolePolicyDocument = "{
                \"Version\": \"2012-10-17\",
                \"Statement\": [{
                    \"Effect\": \"Allow\",
                    \"Principal\": {\"AWS\": \"{$user['Arn']}\"},
                    \"Action\": \"sts:AssumeRole\"
                }]
            }";
$assumeRoleRole = $service->createRole("iam_demo_role_$uuid", $assumeRolePolicyDocument);
echo "Created role: {$assumeRoleRole['RoleName']}\n";

$listAllBucketsPolicyDocument = "{
                \"Version\": \"2012-10-17\",
                \"Statement\": [{
                    \"Effect\": \"Allow\",
                    \"Action\": \"s3:ListAllMyBuckets\",
                    \"Resource\": \"arn:aws:s3:::*\"}]
}";
$listAllBucketsPolicy = $service->createPolicy("iam_demo_policy_$uuid", $listAllBucketsPolicyDocument);
echo "Created policy: {$listAllBucketsPolicy['PolicyName']}\n";

$service->attachRolePolicy($assumeRoleRole['RoleName'], $listAllBucketsPolicy['Arn']);

$inlinePolicyDocument = "{
                \"Version\": \"2012-10-17\",
                \"Statement\": [{
                    \"Effect\": \"Allow\",
                    \"Action\": \"sts:AssumeRole\",
                    \"Resource\": \"{$assumeRoleRole['Arn']}\"}]
}";
$inlinePolicy = $service->createUserPolicy("iam_demo_inline_policy_$uuid", $inlinePolicyDocument, $user['UserName']);
//First, fail to list the buckets with the user
$credentials = new Credentials($key['AccessKeyId'], $key['SecretAccessKey']);
$s3Client = new S3Client(['region' => 'us-west-2', 'version' => 'latest', 'credentials' => $credentials]);
try {
    $s3Client->listBuckets([
    ]);
    echo "this should not run";
} catch (S3Exception $exception) {
    echo "successfully failed!\n";
}

$stsClient = new StsClient(['region' => 'us-west-2', 'version' => 'latest', 'credentials' => $credentials]);
sleep(10);
$assumedRole = $stsClient->assumeRole([
    'RoleArn' => $assumeRoleRole['Arn'],
    'RoleSessionName' => "DemoAssumeRoleSession_$uuid",
]);
$assumedCredentials = [
    'key' => $assumedRole['Credentials']['AccessKeyId'],
    'secret' => $assumedRole['Credentials']['SecretAccessKey'],
    'token' => $assumedRole['Credentials']['SessionToken'],
];
$s3Client = new S3Client(['region' => 'us-west-2', 'version' => 'latest', 'credentials' => $assumedCredentials]);
try {
    $s3Client->listBuckets([
    ]);
    echo "this should now run!\n";
} catch (S3Exception $exception) {
    echo "this should now not fail\n";
}

$service->detachRolePolicy($assumeRoleRole['RoleName'], $listAllBucketsPolicy['Arn']);
$deletePolicy = $service->deletePolicy($listAllBucketsPolicy['Arn']);
echo "Delete policy: {$listAllBucketsPolicy['PolicyName']}\n";
$deletedRole = $service->deleteRole($assumeRoleRole['Arn']);
echo "Deleted role: {$assumeRoleRole['RoleName']}\n";
$deletedKey = $service->deleteAccessKey($key['AccessKeyId']);
$deletedUser = $service->deleteUser($user['UserName']);
echo "Delete user: {$user['UserName']}\n";
```
+ For API details, see the following topics in *AWS SDK for PHP API Reference*\.
  + [AttachRolePolicy](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/AttachRolePolicy)
  + [CreateAccessKey](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/CreateAccessKey)
  + [CreatePolicy](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/CreatePolicy)
  + [CreateRole](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/CreateRole)
  + [CreateUser](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/CreateUser)
  + [DeleteAccessKey](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/DeleteAccessKey)
  + [DeletePolicy](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/DeletePolicy)
  + [DeleteRole](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/DeleteRole)
  + [DeleteUser](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/DeleteUser)
  + [DeleteUserPolicy](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/DeleteUserPolicy)
  + [DetachRolePolicy](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/DetachRolePolicy)
  + [PutUserPolicy](https://docs.aws.amazon.com/goto/SdkForPHPV3/iam-2010-05-08/PutUserPolicy)

------
#### [ Python ]

**SDK for Python \(Boto3\)**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/python/example_code/iam/iam_basics#code-examples)\. 
Create an IAM user and a role that grants permission to list Amazon S3 buckets\. The user has rights only to assume the role\. After assuming the role, use temporary credentials to list buckets for the account\.  

```
import json
import sys
import time
from uuid import uuid4

import boto3
from botocore.exceptions import ClientError


def progress_bar(seconds):
    """Shows a simple progress bar in the command window."""
    for _ in range(seconds):
        time.sleep(1)
        print('.', end='')
        sys.stdout.flush()
    print()


def setup(iam_resource):
    """
    Creates a new user with no permissions.
    Creates an access key pair for the user.
    Creates a role with a policy that lets the user assume the role.
    Creates a policy that allows listing Amazon S3 buckets.
    Attaches the policy to the role.
    Creates an inline policy for the user that lets the user assume the role.

    :param iam_resource: A Boto3 AWS Identity and Access Management (IAM) resource
                         that has permissions to create users, roles, and policies
                         in the account.
    :return: The newly created user, user key, and role.
    """
    try:
        user = iam_resource.create_user(UserName=f'demo-user-{uuid4()}')
        print(f"Created user {user.name}.")
    except ClientError as error:
        print(f"Couldn't create a user for the demo. Here's why: "
              f"{error.response['Error']['Message']}")
        raise

    try:
        user_key = user.create_access_key_pair()
        print(f"Created access key pair for user.")
    except ClientError as error:
        print(f"Couldn't create access keys for user {user.name}. Here's why: "
              f"{error.response['Error']['Message']}")
        raise

    print(f"Wait for user to be ready.", end='')
    progress_bar(10)

    try:
        role = iam_resource.create_role(
            RoleName=f'demo-role-{uuid4()}',
            AssumeRolePolicyDocument=json.dumps({
                'Version': '2012-10-17',
                'Statement': [{
                    'Effect': 'Allow',
                    'Principal': {'AWS': user.arn},
                    'Action': 'sts:AssumeRole'}]}))
        print(f"Created role {role.name}.")
    except ClientError as error:
        print(f"Couldn't create a role for the demo. Here's why: "
              f"{error.response['Error']['Message']}")
        raise

    try:
        policy = iam_resource.create_policy(
            PolicyName=f'demo-policy-{uuid4()}',
            PolicyDocument=json.dumps({
                'Version': '2012-10-17',
                'Statement': [{
                    'Effect': 'Allow',
                    'Action': 's3:ListAllMyBuckets',
                    'Resource': 'arn:aws:s3:::*'}]}))
        role.attach_policy(PolicyArn=policy.arn)
        print(f"Created policy {policy.policy_name} and attached it to the role.")
    except ClientError as error:
        print(f"Couldn't create a policy and attach it to role {role.name}. Here's why: "
              f"{error.response['Error']['Message']}")
        raise

    try:
        user.create_policy(
            PolicyName=f'demo-user-policy-{uuid4()}',
            PolicyDocument=json.dumps({
                'Version': '2012-10-17',
                'Statement': [{
                    'Effect': 'Allow',
                    'Action': 'sts:AssumeRole',
                    'Resource': role.arn}]}))
        print(f"Created an inline policy for {user.name} that lets the user assume "
              f"the role.")
    except ClientError as error:
        print(f"Couldn't create an inline policy for user {user.name}. Here's why: "
              f"{error.response['Error']['Message']}")
        raise

    print("Give AWS time to propagate these new resources and connections.", end='')
    progress_bar(10)

    return user, user_key, role


def show_access_denied_without_role(user_key):
    """
    Shows that listing buckets without first assuming the role is not allowed.

    :param user_key: The key of the user created during setup. This user does not
                     have permission to list buckets in the account.
    """
    print(f"Try to list buckets without first assuming the role.")
    s3_denied_resource = boto3.resource(
        's3', aws_access_key_id=user_key.id, aws_secret_access_key=user_key.secret)
    try:
        for bucket in s3_denied_resource.buckets.all():
            print(bucket.name)
        raise RuntimeError("Expected to get AccessDenied error when listing buckets!")
    except ClientError as error:
        if error.response['Error']['Code'] == 'AccessDenied':
            print("Attempt to list buckets with no permissions: AccessDenied.")
        else:
            raise


def list_buckets_from_assumed_role(user_key, assume_role_arn, session_name):
    """
    Assumes a role that grants permission to list the Amazon S3 buckets in the account.
    Uses the temporary credentials from the role to list the buckets that are owned
    by the assumed role's account.

    :param user_key: The access key of a user that has permission to assume the role.
    :param assume_role_arn: The Amazon Resource Name (ARN) of the role that
                            grants access to list the other account's buckets.
    :param session_name: The name of the STS session.
    """
    sts_client = boto3.client(
        'sts', aws_access_key_id=user_key.id, aws_secret_access_key=user_key.secret)
    try:
        response = sts_client.assume_role(
            RoleArn=assume_role_arn, RoleSessionName=session_name)
        temp_credentials = response['Credentials']
        print(f"Assumed role {assume_role_arn} and got temporary credentials.")
    except ClientError as error:
        print(f"Couldn't assume role {assume_role_arn}. Here's why: "
              f"{error.response['Error']['Message']}")
        raise

    # Create an S3 resource that can access the account with the temporary credentials.
    s3_resource = boto3.resource(
        's3',
        aws_access_key_id=temp_credentials['AccessKeyId'],
        aws_secret_access_key=temp_credentials['SecretAccessKey'],
        aws_session_token=temp_credentials['SessionToken'])
    print(f"Listing buckets for the assumed role's account:")
    try:
        for bucket in s3_resource.buckets.all():
            print(bucket.name)
    except ClientError as error:
        print(f"Couldn't list buckets for the account. Here's why: "
              f"{error.response['Error']['Message']}")
        raise


def teardown(user, role):
    """
    Removes all resources created during setup.

    :param user: The demo user.
    :param role: The demo role.
    """
    try:
        for attached in role.attached_policies.all():
            policy_name = attached.policy_name
            role.detach_policy(PolicyArn=attached.arn)
            attached.delete()
            print(f"Detached and deleted {policy_name}.")
        role.delete()
        print(f"Deleted {role.name}.")
    except ClientError as error:
        print("Couldn't detach policy, delete policy, or delete role. Here's why: "
              f"{error.response['Error']['Message']}")
        raise

    try:
        for user_pol in user.policies.all():
            user_pol.delete()
            print("Deleted inline user policy.")
        for key in user.access_keys.all():
            key.delete()
            print("Deleted user's access key.")
        user.delete()
        print(f"Deleted {user.name}.")
    except ClientError as error:
        print("Couldn't delete user policy or delete user. Here's why: "
              f"{error.response['Error']['Message']}")


def usage_demo():
    """Drives the demonstration."""
    print('-'*88)
    print(f"Welcome to the IAM create user and assume role demo.")
    print('-'*88)
    iam_resource = boto3.resource('iam')
    user = None
    role = None
    try:
        user, user_key, role = setup(iam_resource)
        print(f"Created {user.name} and {role.name}.")
        show_access_denied_without_role(user_key)
        list_buckets_from_assumed_role(user_key, role.arn, 'AssumeRoleDemoSession')
    except Exception:
        print("Something went wrong!")
    finally:
        if user is not None and role is not None:
            teardown(user, role)
        print("Thanks for watching!")


if __name__ == '__main__':
    usage_demo()
```
+ For API details, see the following topics in *AWS SDK for Python \(Boto3\) API Reference*\.
  + [AttachRolePolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/AttachRolePolicy)
  + [CreateAccessKey](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/CreateAccessKey)
  + [CreatePolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/CreatePolicy)
  + [CreateRole](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/CreateRole)
  + [CreateUser](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/CreateUser)
  + [DeleteAccessKey](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DeleteAccessKey)
  + [DeletePolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DeletePolicy)
  + [DeleteRole](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DeleteRole)
  + [DeleteUser](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DeleteUser)
  + [DeleteUserPolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DeleteUserPolicy)
  + [DetachRolePolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/DetachRolePolicy)
  + [PutUserPolicy](https://docs.aws.amazon.com/goto/boto3/iam-2010-05-08/PutUserPolicy)

------
#### [ Ruby ]

**SDK for Ruby**  
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/ruby/example_code/iam#code-examples)\. 
  

```
require "aws-sdk-iam"
require "aws-sdk-s3"

# Wraps the scenario actions.
class ScenarioCreateUserAssumeRole
  attr_reader :iam_resource

  # @param iam_resource [Aws::IAM::Resource] An AWS IAM resource.
  def initialize(iam_resource)
    @iam_resource = iam_resource
  end

  # Waits for the specified number of seconds.
  #
  # @param duration [Integer] The number of seconds to wait.
  def wait(duration)
    puts("Give AWS time to propagate resources...")
    sleep(duration)
  end

  # Creates a user.
  #
  # @param user_name [String] The name to give the user.
  # @return [Aws::IAM::User] The newly created user.
  def create_user(user_name)
    user = @iam_resource.create_user(user_name: user_name)
    puts("Created demo user named #{user.name}.")
  rescue Aws::Errors::ServiceError => e
    puts("Tried and failed to create demo user.")
    puts("\t#{e.code}: #{e.message}")
    puts("\nCan't continue the demo without a user!")
    raise
  else
    user
  end

  # Creates an access key for a user.
  #
  # @param user [Aws::IAM::User] The user that owns the key.
  # @return [Aws::IAM::AccessKeyPair] The newly created access key.
  def create_access_key_pair(user)
    user_key = user.create_access_key_pair
    puts("Created access key pair for user.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't create access keys for user #{user.name}.")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    user_key
  end

  # Creates a role that can be assumed by a user.
  #
  # @param role_name [String] The name to give the role.
  # @param user [Aws::IAM::User] The user who is granted permission to assume the role.
  # @return [Aws::IAM::Role] The newly created role.
  def create_role(role_name, user)
    role = @iam_resource.create_role(
      role_name: role_name,
      assume_role_policy_document: {
        Version: "2012-10-17",
        Statement: [{
          Effect: "Allow",
          Principal: {'AWS': user.arn},
          Action: "sts:AssumeRole"
        }]
      }.to_json)
    puts("Created role #{role.name}.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't create a role for the demo. Here's why: ")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    role
  end

  # Creates a policy that grants permission to list S3 buckets in the account, and
  # then attaches the policy to a role.
  #
  # @param policy_name [String] The name to give the policy.
  # @param role [Aws::IAM::Role] The role that the policy is attached to.
  # @return [Aws::IAM::Policy] The newly created policy.
  def create_and_attach_role_policy(policy_name, role)
    policy = @iam_resource.create_policy(
      policy_name: policy_name,
      policy_document: {
        Version: "2012-10-17",
        Statement: [{
          Effect: "Allow",
          Action: "s3:ListAllMyBuckets",
          Resource: "arn:aws:s3:::*"
        }]
      }.to_json)
    role.attach_policy(policy_arn: policy.arn)
    puts("Created policy #{policy.policy_name} and attached it to role #{role.name}.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't create a policy and attach it to role #{role.name}. Here's why: ")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    policy
  end

  # Creates an inline policy for a user that lets the user assume a role.
  #
  # @param policy_name [String] The name to give the policy.
  # @param user [Aws::IAM::User] The user that owns the policy.
  # @param role [Aws::IAM::Role] The role that can be assumed.
  # @return [Aws::IAM::UserPolicy] The newly created policy.
  def create_user_policy(policy_name, user, role)
    policy = user.create_policy(
      policy_name: policy_name,
      policy_document: {
        Version: "2012-10-17",
        Statement: [{
          Effect: "Allow",
          Action: "sts:AssumeRole",
          Resource: role.arn
        }]
      }.to_json)
    puts("Created an inline policy for #{user.name} that lets the user assume role #{role.name}.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't create an inline policy for user #{user.name}. Here's why: ")
    puts("\t#{e.code}: #{e.message}")
    raise
  else
    policy
  end

  # Creates an Amazon S3 resource with specified credentials. This is separated into a
  # factory function so that it can be mocked for unit testing.
  #
  # @param credentials [Aws::Credentials] The credentials used by the Amazon S3 resource.
  def create_s3_resource(credentials)
    Aws::S3::Resource.new(client: Aws::S3::Client.new(credentials: credentials))
  end

  # Lists the S3 buckets for the account, using the specified Amazon S3 resource.
  # Because the resource uses credentials with limited access, it may not be able to
  # list the S3 buckets.
  #
  # @param s3_resource [Aws::S3::Resource] An Amazon S3 resource.
  def list_buckets(s3_resource)
    count = 10
    s3_resource.buckets.each do |bucket|
      puts "\t#{bucket.name}"
      count -= 1
      break if count.zero?
    end
  rescue Aws::Errors::ServiceError => e
    if e.code == "AccessDenied"
      puts("Attempt to list buckets with no permissions: AccessDenied.")
    else
      puts("Couldn't list buckets for the account. Here's why: ")
      puts("\t#{e.code}: #{e.message}")
      raise
    end
  end

  # Creates an AWS Security Token Service (AWS STS) client with specified credentials.
  # This is separated into a factory function so that it can be mocked for unit testing.
  #
  # @param key_id [String] The ID of the access key used by the STS client.
  # @param key_secret [String] The secret part of the access key used by the STS client.
  def create_sts_client(key_id, key_secret)
    Aws::STS::Client.new(access_key_id: key_id, secret_access_key: key_secret)
  end

  # Gets temporary credentials that can be used to assume a role.
  #
  # @param role_arn [String] The ARN of the role that is assumed when these credentials
  #                          are used.
  # @param sts_client [AWS::STS::Client] An AWS STS client.
  # @return [Aws::AssumeRoleCredentials] The credentials that can be used to assume the role.
  def assume_role(role_arn, sts_client)
    credentials = Aws::AssumeRoleCredentials.new(
      client: sts_client,
      role_arn: role_arn,
      role_session_name: "create-use-assume-role-scenario"
    )
    puts("Assumed role '#{role_arn}', got temporary credentials.")
    credentials
  end

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

  # Deletes a user. If the user has inline policies or access keys, they are deleted
  # before the user is deleted.
  #
  # @param user [Aws::IAM::User] The user to delete.
  def delete_user(user)
    user.policies.each do |policy|
      name = policy.name
      policy.delete
      puts("Deleted user policy #{name}.")
    end
    user.access_keys.each do |key|
      key.delete
      puts("Deleted access key for user #{user.name}.")
    end
    name = user.name
    user.delete
    puts("Deleted user #{name}.")
  rescue Aws::Errors::ServiceError => e
    puts("Couldn't detach policies and delete user #{user.name}. Here's why:")
    puts("\t#{e.code}: #{e.message}")
  end
end

# Runs the IAM create a user and assume a role scenario.
def run_scenario(scenario)
  puts("-" * 88)
  puts("Welcome to the IAM create a user and assume a role demo!")
  puts("-" * 88)

  user = scenario.create_user("doc-example-user-#{Random.uuid}")
  user_key = scenario.create_access_key_pair(user)
  scenario.wait(10)
  role = scenario.create_role("doc-example-role-#{Random.uuid}", user)
  scenario.create_and_attach_role_policy("doc-example-role-policy-#{Random.uuid}", role)
  scenario.create_user_policy("doc-example-user-policy-#{Random.uuid}", user, role)
  scenario.wait(10)
  puts("Try to list buckets with credentials for a user who has no permissions.")
  puts("Expect AccessDenied from this call.")
  scenario.list_buckets(
    scenario.create_s3_resource(Aws::Credentials.new(user_key.id, user_key.secret)))
  puts("Now, assume the role that grants permission.")
  temp_credentials = scenario.assume_role(
    role.arn, scenario.create_sts_client(user_key.id, user_key.secret))
  puts("Here are your buckets:")
  scenario.list_buckets(scenario.create_s3_resource(temp_credentials))
  puts("Deleting role '#{role.name}' and attached policies.")
  scenario.delete_role(role)
  puts("Deleting user '#{user.name}', policies, and keys.")
  scenario.delete_user(user)

  puts("Thanks for watching!")
  puts("-" * 88)
rescue Aws::Errors::ServiceError => e
  puts("Something went wrong with the demo.")
  puts("\t#{e.code}: #{e.message}")
end

run_scenario(ScenarioCreateUserAssumeRole.new(Aws::IAM::Resource.new)) if $PROGRAM_NAME == __FILE__
```
+ For API details, see the following topics in *AWS SDK for Ruby API Reference*\.
  + [AttachRolePolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/AttachRolePolicy)
  + [CreateAccessKey](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/CreateAccessKey)
  + [CreatePolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/CreatePolicy)
  + [CreateRole](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/CreateRole)
  + [CreateUser](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/CreateUser)
  + [DeleteAccessKey](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeleteAccessKey)
  + [DeletePolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeletePolicy)
  + [DeleteRole](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeleteRole)
  + [DeleteUser](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeleteUser)
  + [DeleteUserPolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DeleteUserPolicy)
  + [DetachRolePolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/DetachRolePolicy)
  + [PutUserPolicy](https://docs.aws.amazon.com/goto/SdkForRubyV3/iam-2010-05-08/PutUserPolicy)

------
#### [ Rust ]

**SDK for Rust**  
This documentation is for an SDK in preview release\. The SDK is subject to change and should not be used in production\.
 To learn how to set up and run this example, see [GitHub](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/rust_dev_preview/iam#code-examples)\. 
  

```
use aws_config::meta::region::RegionProviderChain;
use aws_sdk_iam::Error as iamError;
use aws_sdk_iam::{Client as iamClient, Credentials as iamCredentials};
use aws_sdk_s3::Client as s3Client;
use aws_sdk_sts::Client as stsClient;
use aws_types::region::Region;
use std::borrow::Borrow;
use tokio::time::{sleep, Duration};
use uuid::Uuid;

#[tokio::main]
async fn main() -> Result<(), iamError> {
    let (client, uuid, list_all_buckets_policy_document, inline_policy_document) =
        initialize_variables().await;

    if let Err(e) = run_iam_operations(
        client,
        uuid,
        list_all_buckets_policy_document,
        inline_policy_document,
    )
    .await
    {
        println!("{:?}", e);
    };

    Ok(())
}

async fn initialize_variables() -> (iamClient, String, String, String) {
    let region_provider = RegionProviderChain::first_try(Region::new("us-west-2"));

    let shared_config = aws_config::from_env().region(region_provider).load().await;
    let client = iamClient::new(&shared_config);
    let uuid = Uuid::new_v4().to_string();

    let list_all_buckets_policy_document = "{
                \"Version\": \"2012-10-17\",
                \"Statement\": [{
                    \"Effect\": \"Allow\",
                    \"Action\": \"s3:ListAllMyBuckets\",
                    \"Resource\": \"arn:aws:s3:::*\"}]
    }"
    .to_string();
    let inline_policy_document = "{
                \"Version\": \"2012-10-17\",
                \"Statement\": [{
                    \"Effect\": \"Allow\",
                    \"Action\": \"sts:AssumeRole\",
                    \"Resource\": \"{}\"}]
    }"
    .to_string();

    (
        client,
        uuid,
        list_all_buckets_policy_document,
        inline_policy_document,
    )
}

async fn run_iam_operations(
    client: iamClient,
    uuid: String,
    list_all_buckets_policy_document: String,
    inline_policy_document: String,
) -> Result<(), iamError> {
    let user = iam_service::create_user(&client, &format!("{}{}", "iam_demo_user_", uuid)).await?;
    println!(
        "Created the user with the name: {}",
        user.user_name.as_ref().unwrap()
    );
    let key = iam_service::create_access_key(&client, user.user_name.as_ref().unwrap()).await?;

    let assume_role_policy_document = "{
        \"Version\": \"2012-10-17\",
                \"Statement\": [{
                    \"Effect\": \"Allow\",
                    \"Principal\": {\"AWS\": \"{}\"},
                    \"Action\": \"sts:AssumeRole\"
                }]
            }"
    .to_string()
    .replace("{}", user.arn.as_ref().unwrap());

    let assume_role_role = iam_service::create_role(
        &client,
        &format!("{}{}", "iam_demo_role_", uuid),
        &assume_role_policy_document,
    )
    .await?;
    println!(
        "Created the role with the ARN: {}",
        assume_role_role.arn.as_ref().unwrap()
    );

    let list_all_buckets_policy = iam_service::create_policy(
        &client,
        &format!("{}{}", "iam_demo_policy_", uuid),
        &list_all_buckets_policy_document,
    )
    .await?;
    println!(
        "Created policy: {}",
        list_all_buckets_policy.policy_name.as_ref().unwrap()
    );

    let attach_role_policy_result =
        iam_service::attach_role_policy(&client, &assume_role_role, &list_all_buckets_policy)
            .await?;
    println!(
        "Attached the policy to the role: {:?}",
        attach_role_policy_result
    );

    let inline_policy_name = &format!("{}{}", "iam_demo_inline_policy_", uuid);
    let inline_policy_document =
        inline_policy_document.replace("{}", assume_role_role.arn.as_ref().unwrap());
    iam_service::create_user_policy(&client, &user, &inline_policy_name, &inline_policy_document)
        .await?;
    println!("Created inline policy.");

    //First, fail to list the buckets with the user.
    let creds = iamCredentials::from_keys(
        key.access_key_id.as_ref().unwrap(),
        key.secret_access_key.as_ref().unwrap(),
        None,
    );
    let fail_config = aws_config::from_env()
        .credentials_provider(creds.clone())
        .load()
        .await;
    println!("Fail config: {:?}", fail_config);
    let fail_client: s3Client = s3Client::new(&fail_config);
    match fail_client.list_buckets().send().await {
        Ok(e) => {
            println!("This should not run. {:?}", e);
        }
        Err(e) => {
            println!("Successfully failed with error: {:?}", e)
        }
    }

    let sts_config = aws_config::from_env()
        .credentials_provider(creds.clone())
        .load()
        .await;
    let sts_client: stsClient = stsClient::new(&sts_config);
    sleep(Duration::from_secs(10)).await;
    let assumed_role = sts_client
        .assume_role()
        .role_arn(assume_role_role.arn.as_ref().unwrap())
        .role_session_name(&format!("{}{}", "iam_demo_assumerole_session_", uuid))
        .send()
        .await;
    println!("Assumed role: {:?}", assumed_role);
    sleep(Duration::from_secs(10)).await;

    let assumed_credentials = iamCredentials::from_keys(
        assumed_role
            .as_ref()
            .unwrap()
            .credentials
            .as_ref()
            .unwrap()
            .access_key_id
            .as_ref()
            .unwrap(),
        assumed_role
            .as_ref()
            .unwrap()
            .credentials
            .as_ref()
            .unwrap()
            .secret_access_key
            .as_ref()
            .unwrap(),
        assumed_role
            .as_ref()
            .unwrap()
            .credentials
            .as_ref()
            .unwrap()
            .session_token
            .borrow()
            .clone(),
    );

    let succeed_config = aws_config::from_env()
        .credentials_provider(assumed_credentials)
        .load()
        .await;
    println!("succeed config: {:?}", succeed_config);
    let succeed_client: s3Client = s3Client::new(&succeed_config);
    sleep(Duration::from_secs(10)).await;
    match succeed_client.list_buckets().send().await {
        Ok(_) => {
            println!("This should now run successfully.")
        }
        Err(e) => {
            println!("This should not run. {:?}", e);
            panic!()
        }
    }

    //Clean up.
    iam_service::detach_role_policy(
        &client,
        assume_role_role.role_name.as_ref().unwrap(),
        list_all_buckets_policy.arn.as_ref().unwrap(),
    )
    .await?;
    iam_service::delete_policy(&client, list_all_buckets_policy).await?;
    iam_service::delete_role(&client, &assume_role_role).await?;
    println!(
        "Deleted role {}",
        assume_role_role.role_name.as_ref().unwrap()
    );
    iam_service::delete_access_key(&client, &user, &key).await?;
    println!("Deleted key for {}", key.user_name.as_ref().unwrap());
    iam_service::delete_user_policy(&client, &user, &inline_policy_name).await?;
    println!("Deleted inline user policy: {}", inline_policy_name);
    iam_service::delete_user(&client, &user).await?;
    println!("Deleted user {}", user.user_name.as_ref().unwrap());

    Ok(())
}
```
+ For API details, see the following topics in *AWS SDK for Rust API reference*\.
  + [AttachRolePolicy](https://docs.rs/releases/search?query=aws-sdk)
  + [CreateAccessKey](https://docs.rs/releases/search?query=aws-sdk)
  + [CreatePolicy](https://docs.rs/releases/search?query=aws-sdk)
  + [CreateRole](https://docs.rs/releases/search?query=aws-sdk)
  + [CreateUser](https://docs.rs/releases/search?query=aws-sdk)
  + [DeleteAccessKey](https://docs.rs/releases/search?query=aws-sdk)
  + [DeletePolicy](https://docs.rs/releases/search?query=aws-sdk)
  + [DeleteRole](https://docs.rs/releases/search?query=aws-sdk)
  + [DeleteUser](https://docs.rs/releases/search?query=aws-sdk)
  + [DeleteUserPolicy](https://docs.rs/releases/search?query=aws-sdk)
  + [DetachRolePolicy](https://docs.rs/releases/search?query=aws-sdk)
  + [PutUserPolicy](https://docs.rs/releases/search?query=aws-sdk)

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.