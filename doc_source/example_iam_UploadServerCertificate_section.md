# Upload an IAM server certificate using an AWS SDK<a name="example_iam_UploadServerCertificate_section"></a>

The following code example shows how to upload an AWS Identity and Access Management \(IAM\) server certificate\.

**Note**  
The source code for these examples is in the [AWS Code Examples GitHub repository](https://github.com/awsdocs/aws-doc-sdk-examples)\. Have feedback on a code example? [Create an Issue](https://github.com/awsdocs/aws-doc-sdk-examples/issues/new/choose) in the code examples repo\. 

------
#### [ JavaScript ]

**SDK for JavaScript \(v3\)**  
 There's more on GitHub\. Find the complete example and learn how to set up and run in the [AWS Code Examples Repository](https://github.com/awsdocs/aws-doc-sdk-examples/tree/main/javascriptv3/example_code/iam#code-examples)\. 
  

```
import { UploadServerCertificateCommand, IAMClient } from "@aws-sdk/client-iam";
import { readFileSync } from "fs";
import { dirnameFromMetaUrl } from "libs/utils/util-fs.js";
import * as path from "path";

const client = new IAMClient({});

/**
 * The certificate body and private key were generated with the
 * following command.
 *
 * ```
 * openssl req -x509 -newkey rsa:4096 -sha256 -days 3650 -nodes \
 * -keyout example.key -out example.crt -subj "/CN=example.com" \
 * -addext "subjectAltName=DNS:example.com,DNS:www.example.net,IP:10.0.0.1"
 * ```
 */

const certBody = readFileSync(
  path.join(
    dirnameFromMetaUrl(import.meta.url),
    "../../../../resources/sample_files/sample_cert.pem"
  )
);

const privateKey = readFileSync(
  path.join(
    dirnameFromMetaUrl(import.meta.url),
    "../../../../resources/sample_files/sample_private_key.pem"
  )
);

/**
 *
 * @param {string} certificateName
 */
export const uploadServerCertificate = (certificateName) => {
  const command = new UploadServerCertificateCommand({
    ServerCertificateName: certificateName,
    CertificateBody: certBody.toString(),
    PrivateKey: privateKey.toString(),
  });

  return client.send(command);
};
```
+  For API details, see [UploadServerCertificate](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-iam/classes/uploadservercertificatecommand.html) in *AWS SDK for JavaScript API Reference*\. 

------

For a complete list of AWS SDK developer guides and code examples, see [Using IAM with an AWS SDK](sdk-general-information-section.md)\. This topic also includes information about getting started and details about previous SDK versions\.