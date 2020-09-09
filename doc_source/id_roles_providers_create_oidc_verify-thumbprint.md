# Obtaining the root CA thumbprint for an OpenID Connect Identity Provider<a name="id_roles_providers_create_oidc_verify-thumbprint"></a>

When you [create an OpenID Connect \(OIDC\) identity provider](id_roles_providers_create_oidc.md) in IAM, you must supply a thumbprint\. IAM requires the thumbprint for the root certificate authority \(CA\) that signed the certificate used by the external identity provider \(IdP\)\. The thumbprint is a signature for the CA's certificate that was used to issue the certificate for the OIDC\-compatible IdP\. When you create an IAM OIDC identity provider, you are trusting identities authenticated by that IdP to have access to your AWS account\. By supplying the CA's certificate thumbprint, you trust any certificate issued by that CA with the same DNS name as the one registered\. This eliminates the need to update trusts in each account when you renew the IdP's signing certificate\.

**Important**  
In most cases, the federation server uses two different certificates\. The first establishes an HTTPS connection between the clients and the federation endpoint\. This can be safely issued by a public root CA, such as AWS Certificate Manager\. The second is used to sign tokens\. We recommend that you issue this using a private CA\.

You can create an IAM OIDC identity provider with [the AWS Command Line Interface, the Tools for Windows PowerShell, or the IAM API](id_roles_providers_create_oidc.md#manage-oidc-provider-cli)\. When you use these methods, you must obtain the thumbprint manually and supply it to AWS\. When you create an OIDC identity provider with [the IAM console](id_roles_providers_create_oidc.md), the console attempts to fetch the thumbprint for you\. We recommend that you also obtain the thumbprint for your OIDC IdP manually and verify that the console fetched the correct thumbprint\. 

You use a web browser and the OpenSSL command line tool to obtain the thumbprint for an OIDC provider\. For more information, see the following sections\. 

**To obtain the thumbprint for an OIDC IdP**

1. Before you can obtain the thumbprint for an OIDC IdP, you need to obtain the OpenSSL command\-line tool\. You use this tool to download the OIDC IdP's certificate chain and produce a thumbprint of the final certificate in the certificate chain\. If you need to install and configure OpenSSL, follow the instructions at [Install OpenSSL](#oidc-install-openssl) and [Configure OpenSSL](#oidc-configure-openssl)\. 

1. Start with the OIDC IdP's URL \(for example, `https://server.example.com`\), and then add `/.well-known/openid-configuration` to form the URL for the IdP's configuration document, such as the following: 

   **https://*server\.example\.com*/\.well\-known/openid\-configuration**

   Open this URL in a web browser, replacing *server\.example\.com* with your IdP's server name\. 

1. <a name="thumbstep2"></a>In the document displayed in your web browser, find `"jwks_uri"`\. \(Use your web browser's **Find** feature to locate this text on the page\.\) Immediately following the text `"jwks_uri"` you will see a colon \(:\) followed by a URL\. Copy the fully qualified domain name of the URL\. Do not include the `https://` or any path that comes after the top\-level domain\. 

1. Use the OpenSSL command line tool to execute the following command\. Replace *keys\.example\.com* with the domain name you obtained in [Step 3](#thumbstep2)\.

   ```
   openssl s_client -servername keys.example.com -showcerts -connect keys.example.com:443
   ```

1. In your command window, scroll up until you see a certificate similar to the following example\. If you see more than one certificate, find the last certificate that is displayed \(at the bottom of the command output\)\. This will be the certificate of the root CA in the certificate authority chain\.

   ```
   -----BEGIN CERTIFICATE-----
    MIICiTCCAfICCQD6m7oRw0uXOjANBgkqhkiG9w0BAQUFADCBiDELMAkGA1UEBhMC
    VVMxCzAJBgNVBAgTAldBMRAwDgYDVQQHEwdTZWF0dGxlMQ8wDQYDVQQKEwZBbWF6
    b24xFDASBgNVBAsTC0lBTSBDb25zb2xlMRIwEAYDVQQDEwlUZXN0Q2lsYWMxHzAd
    BgkqhkiG9w0BCQEWEG5vb25lQGFtYXpvbi5jb20wHhcNMTEwNDI1MjA0NTIxWhcN
    MTIwNDI0MjA0NTIxWjCBiDELMAkGA1UEBhMCVVMxCzAJBgNVBAgTAldBMRAwDgYD
    VQQHEwdTZWF0dGxlMQ8wDQYDVQQKEwZBbWF6b24xFDASBgNVBAsTC0lBTSBDb25z
    b2xlMRIwEAYDVQQDEwlUZXN0Q2lsYWMxHzAdBgkqhkiG9w0BCQEWEG5vb25lQGFt
    YXpvbi5jb20wgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAMaK0dn+a4GmWIWJ
    21uUSfwfEvySWtC2XADZ4nB+BLYgVIk60CpiwsZ3G93vUEIO3IyNoH/f0wYK8m9T
    rDHudUZg3qX4waLG5M43q7Wgc/MbQITxOUSQv7c7ugFFDzQGBzZswY6786m86gpE
    Ibb3OhjZnzcvQAaRHhdlQWIMm2nrAgMBAAEwDQYJKoZIhvcNAQEFBQADgYEAtCu4
    nUhVVxYUntneD9+h8Mg9q6q+auNKyExzyLwaxlAoo7TJHidbtS4J5iNmZgXL0Fkb
    FFBjvSfpJIlJ00zbhNYS5f6GuoEDmFJl0ZxBHjJnyp378OD8uTs7fLvjx79LjSTb
    NYiytVbZPQUQ5Yaxu2jXnimvw3rrszlaEXAMPLE=
    -----END CERTIFICATE-----
   ```

   Copy the certificate \(including the `-----BEGIN CERTIFICATE-----` and `-----END CERTIFICATE-----` lines\) and paste it into a text file\. Then save the file with the file name **certificate\.crt**\. 

1. Use the OpenSSL command\-line tool to execute the following command\. 

   ```
   openssl x509 -in certificate.crt -fingerprint -noout
   ```

   Your command window displays the certificate thumbprint, which looks similar to the following example:

   ```
   SHA1 Fingerprint=99:0F:41:93:97:2F:2B:EC:F1:2D:DE:DA:52:37:F9:C9:52:F2:0D:9E
   ```

   Remove the colon characters \(:\) from this string to produce the final thumbprint, like this:

   ```
   990F4193972F2BECF12DDEDA5237F9C952F20D9E
   ```

1. If you are creating the IAM OIDC identity provider with the AWS CLI, Tools for Windows PowerShell, or the IAM API, supply this thumbprint when creating the provider\. 

   If you are creating the IAM OIDC identity provider in the IAM console, compare this thumbprint to the thumbprint shown on the console **Verify Provider Information** page when you create an OIDC provider\. 
**Important**  
If the thumbprint you obtained does not match the one you see in the console, you should not create the OIDC provider in the console\. Instead, you should wait a while and then try again to create the OIDC provider, ensuring that the thumbprints match before you create the provider\. If the thumbprints still do not match after a second attempt, use the [IAM Forum](https://forums.aws.amazon.com/forum.jspa?forumID=76) to contact AWS\.

## Install OpenSSL<a name="oidc-install-openssl"></a>

If you don't already have OpenSSL installed, follow the instructions in this section\.

**To install OpenSSL on Linux or Unix**

1. Go to [OpenSSL: Source, Tarballs](https://openssl.org/source/) \(https://openssl\.org/source/\)\.

1. Download the latest source and build the package\.

**To install OpenSSL on Windows**

1. Go to [OpenSSL: Binary Distributions](https://wiki.openssl.org/index.php/Binaries) \(https://wiki\.openssl\.org/index\.php/Binaries\) for a list of sites from which you can install the Windows version\.

1. Follow the instructions on your selected site to start the installation\.

1. If you are asked to install the **Microsoft Visual C\+\+ 2008 Redistributables ** and it is not already installed on your system, choose the download link appropriate for your environment\. Follow the instructions provided by the **Microsoft Visual C\+\+ 2008 Redistributable Setup Wizard**\.
**Note**  
If you are not sure whether the Microsoft Visual C\+\+ 2008 Redistributables is already installed on your system, you can try installing OpenSSL first\. The OpenSSL installer displays an alert if the Microsoft Visual C\+\+ 2008 Redistributables is not yet installed\. Make sure that you install the architecture \(32\-bit or 64\-bit\) that matches the version of OpenSSL that you install\.

1. After you have installed the Microsoft Visual C\+\+ 2008 Redistributables, select the appropriate version of the OpenSSL binaries for your environment and save the file locally\. Start the **OpenSSL Setup Wizard**\.

1. Follow the instructions described in the **OpenSSL Setup Wizard**\.

## Configure OpenSSL<a name="oidc-configure-openssl"></a>

Before you use OpenSSL commands, you must configure the operating system so that it has information about the location where OpenSSL is installed\.

**To configure OpenSSL on Linux or Unix**

1. At the command line, set the `OpenSSL_HOME` variable to the location of the OpenSSL installation:

   ```
   $ export OpenSSL_HOME=path_to_your_OpenSSL_installation
   ```

1. Set the path to include the OpenSSL installation:

   ```
   $ export PATH=$PATH:$OpenSSL_HOME/bin
   ```
**Note**  
Any changes you make to environment variables with the `export` command are valid only for the current session\. You can make persistent changes to the environment variables by setting them in your shell configuration file\. For more information, see the documentation for your operating system\.

**To configure OpenSSL on Windows**

1. Open a **Command Prompt** window\.

1. Set the `OpenSSL_HOME` variable to the location of the OpenSSL installation:

   ```
   C:\> set OpenSSL_HOME=path_to_your_OpenSSL_installation
   ```

1. Set the `OpenSSL_CONF` variable to the location of the configuration file in your OpenSSL installation:

   ```
   C:\> set OpenSSL_CONF=path_to_your_OpenSSL_installation\bin\openssl.cfg
   ```

1. Set the path to include the OpenSSL installation:

   ```
   C:\> set Path=%Path%;%OpenSSL_HOME%\bin
   ```
**Note**  
Any changes you make to Windows environment variables in a **Command Prompt** window are valid only for the current command line session\. You can make persistent changes to the environment variables by setting them as system properties\. The exact procedures depend on what version of Windows you're using\. \(For example, in Windows 7, open **Control Panel**, **System and Security**, **System**\. Then choose **Advanced system settings**, **Advanced** tab, **Environment Variables**\.\) For more information, see the Windows documentation\.