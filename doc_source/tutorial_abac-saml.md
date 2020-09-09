# IAM Tutorial: Use SAML session tags for ABAC<a name="tutorial_abac-saml"></a>

Attribute\-based access control \(ABAC\) is an authorization strategy that defines permissions based on attributes\. In AWS, these attributes are called tags\. You can [attach tags to IAM entities](id_tags.md) \(users or roles\) and to AWS resources\. When the entities are used to make requests to AWS, they become principals and those principals include tags\.

You can also pass [session tags](id_session-tags.md) when you assume a role or federate a user\. You can then define policies that use tag condition keys to grant permissions to your principals based on their tags\. When you use tags to control access to your AWS resources, you allow your teams and resources to grow with fewer changes to AWS policies\. ABAC policies are more flexible than traditional AWS policies, which require you to list each individual resource\. For more information about ABAC and its advantage over traditional policies, see [What is ABAC for AWS?](introduction_attribute-based-access-control.md)\.

If your company uses a SAML\-based identity provider \(IdP\) to manage corporate user identities, you can use SAML attributes for fine\-grained access control in AWS\. Attributes can include cost center identifiers, user email addresses, department classifications, and project assignments\. When you pass these attributes as session tags, you can then control access to AWS based on these session tags\.

To complete the [ABAC tutorial](tutorial_attribute-based-access-control.md) by passing SAML attributes to your session principal, complete the tasks in [IAM Tutorial: Define permissions to access AWS resources based on tags](tutorial_attribute-based-access-control.md), with the changes that are included in this topic\.

## Prerequisites<a name="tutorial_abac-saml-prerequisites"></a>

To perform the steps to use SAML session tags for ABAC, you must already have the following:
+ Access to a SAML\-based IdP where you can create test users with specific attributes\. 
+ An AWS account that you can sign in to as an IAM user with administrative permissions\. If you have a new account and sign in as the AWS account root user, then [create an IAM admin user](getting-started_create-admin-group.md)\.
+ Experience creating and editing IAM users, roles, and policies in the AWS Management Console\. However, if you need help remembering an IAM management process, the ABAC tutorial provides links where you can view step\-by\-step instructions\.
+ Experience setting up a SAML\-based IdP in IAM\. To view more details and links to detailed IAM documentation, see [Passing session tags using AssumeRoleWithSAML](id_session-tags.md#id_session-tags_adding-assume-role-saml)\.

## Step 1: Create a test IAM user<a name="tutorial_abac-saml-step1"></a>

Skip the instructions in [Step 1: Create test users](tutorial_attribute-based-access-control.md#tutorial_abac_step1)\. Because your identities are defined in your provider, it's not necessary for you to add IAM users for your employees\. 

## Step 2: Create the ABAC policy<a name="tutorial_abac-saml-step2"></a>

Follow the instructions in [Step 2: Create the ABAC policy](tutorial_attribute-based-access-control.md#tutorial_abac_step2) to create the specified managed policy in IAM\. 

## Step 3: Create and configure the SAML role<a name="tutorial_abac-saml-step3"></a>

When you use the ABAC tutorial for SAML, you must perform additional steps to create the role, configure the SAML IdP, and enable AWS Management Console access\. For more information, see [Step 3: Create roles](tutorial_attribute-based-access-control.md#tutorial_abac_step3)\.

### Step 3A: Create the SAML role<a name="tutorial_abac-saml-step3a"></a>

Create a single role that trusts your SAML identity provider and the `test-session-tags` user that you created in step 1\. The ABAC tutorial uses separate roles with different role tags\. Because you are passing session tags from your SAML IdP, you need only one role\. To learn how to create a SAML\-based role, see [Creating a role for SAML 2\.0 federation \(console\)](id_roles_create_for-idp_saml.md)\. 

Name the role `access-session-tags`\. Attach the `access-same-project-team` permissions policy to the role\. Edit the role trust policy to use the following policy\. For detailed instructions on how to edit the trust relationship of a role, see [Modifying a role \(console\)](roles-managingrole-editing-console.md)\.

The following role trust policy allows your SAML identity provider and the `test-session-tags` user to assume the role\. When they assume the role, they must pass the three specified session tags\. The `sts:TagSession` action is required to allow passing session tags\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowSamlIdentityAssumeRole",
            "Effect": "Allow",
            "Action": [
                "sts:AssumeRoleWithSAML",
                "sts:TagSession"
            ],
            "Principal": {"Federated":"arn:aws:iam::123456789012:saml-provider/ExampleCorpProvider"},
            "Condition": {
                "StringLike": {
                    "aws:RequestTag/cost-center": "*",
                    "aws:RequestTag/access-project": "*",
                    "aws:RequestTag/access-team": [
                        "eng",
                        "qas"
                    ]
                },
                "StringEquals": {"SAML:aud": "https://signin.aws.amazon.com/saml"}
            }
        }
    ]
}
```

The `AllowSamlIdentityAssumeRole` statement allows members of the Engineering and Quality Assurance teams to assume this role when they federate into AWS from the Example Corporation IdP\. The `ExampleCorpProvider` SAML provider is defined in IAM\. The administrator has already set up the SAML assertion to pass the three required session tags\. The assertion can pass additional tags, but these three must be present\. The identity's attributes can have any value for the `cost-center` and `access-project` tags\. However, the `access-team` attribute value must match `eng` or `qas` to indicate that the identity is on the Engineering or Quality Assurance team\. 

### Step 3B: Configure the SAML IdP<a name="tutorial_abac-saml-step3b"></a>

Configure your SAML IdP to pass the `cost-center`, `access-project`, and `access-team` attributes as session tags\. For more information, see [Passing session tags using AssumeRoleWithSAML](id_session-tags.md#id_session-tags_adding-assume-role-saml)\.

To pass these attributes as session tags, include the following elements in your SAML assertion\.

```
<Attribute Name="https://aws.amazon.com/SAML/Attributes/PrincipalTag:cost-center">
  <AttributeValue>987654</AttributeValue>
</Attribute>
<Attribute Name="https://aws.amazon.com/SAML/Attributes/PrincipalTag:access-project">
  <AttributeValue>peg</AttributeValue>
</Attribute>
<Attribute Name="https://aws.amazon.com/SAML/Attributes/PrincipalTag:access-team">
  <AttributeValue>eng</AttributeValue>
</Attribute>
```

### Step 3B: Enable console access<a name="tutorial_abac-saml-step3b"></a>

Enable console access for your federated SAML users\. For more information, see [Enabling SAML 2\.0 federated users to access the AWS Management Console](id_roles_providers_enable-console-saml.md)\.

## Step 4: Test creating secrets<a name="tutorial_abac-saml-step4"></a>

Federate into the AWS Management Console using the `access-session-tags` role\. For more information, see [Enabling SAML 2\.0 federated users to access the AWS Management Console](id_roles_providers_enable-console-saml.md)\. Then follow the instructions in [Step 4: Test creating secrets](tutorial_attribute-based-access-control.md#tutorial_abac_step4) to create secrets\. Use different SAML identities with attributes to match the tags that are indicated in the ABAC tutorial\. For more information, see [Step 4: Test creating secrets](tutorial_attribute-based-access-control.md#tutorial_abac_step4)\.

## Step 5: Test viewing secrets<a name="tutorial_abac-saml-step5"></a>

Follow the instructions in [Step 5: Test viewing secrets](tutorial_attribute-based-access-control.md#tutorial_abac_step5) to view the secrets that you created in the previous step\. Use different SAML identities with attributes to match the tags that are indicated in the ABAC tutorial\.

## Step 6: Test scalability<a name="tutorial_abac-saml-step6"></a>

Follow the instructions in [Step 6: Test scalability](tutorial_attribute-based-access-control.md#tutorial_abac_step6) to test scalability\. Do this by adding a new identity in your SAML\-based IdP with the following attributes:
+ `cost-center = 101010`
+ `access-project = cen`
+ `access-team = eng`

## Step 7: Test updating and deleting secrets<a name="tutorial_abac-saml-step7"></a>

Follow the instructions in [Step 7: Test updating and deleting secrets](tutorial_attribute-based-access-control.md#tutorial_abac_step7) to update and delete secrets\. Use different SAML identities with attributes to match the tags that are indicated in the ABAC tutorial\.

**Important**  
Delete all of the secrets that you created to avoid billing charges\. For details about pricing in Secrets Manager, see [AWS Secrets Manager Pricing](https://aws.amazon.com/secrets-manager/pricing/)\.

## Summary<a name="tutorial-abac-saml-summary"></a>

You've now successfully completed all of the steps necessary to use SAML session tags and resource tags for permissions management\.

**Note**  
You added policies that allow actions only under specific conditions\. If you apply a different policy to your users or roles that has broader permissions, then the actions might not be limited to require tagging\. For example, if you give a user full administrative permissions using the `AdministratorAccess` AWS managed policy, then these policies don't restrict that access\. For more information about how permissions are determined when multiple policies are involved, see [Determining whether a request is allowed or denied within an account](reference_policies_evaluation-logic.md#policy-eval-denyallow)\.