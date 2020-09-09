# How to view a SAML response in your browser for troubleshooting<a name="troubleshoot_saml_view-saml-response"></a>

The following procedures describe how to view the SAML response from your service provider from in your browser when troubleshooting a SAML 2\.0–related issue\. 

For all browsers, go to the page where you can reproduce the issue\. Then follow the steps for the appropriate browser:

**Topics**
+ [Google chrome](#chrome)
+ [Mozilla firefox](#firefox)
+ [Apple safari](#safari)
+ [Microsoft Internet Explorer](#ie)
+ [What to do with the Base64\-encoded SAML response](#whatnext)

## Google chrome<a name="chrome"></a>

**To view a SAML response in chrome**

These steps were tested using version 54\.0\.2840\.87m\. If you use another version, you might need to adapt the steps accordingly\.

1. Press **F12** to start the developer console\.

1. Select the **Network** tab, and then select **Preserve log**\.

1. Reproduce the issue\.

1. Look for a **SAML Post** in the developer console pane\. Select that row, and then view the **Headers** tab at the bottom\. Look for the **SAMLResponse** attribute that contains the encoded request\.

## Mozilla firefox<a name="firefox"></a>

**To view a SAML response in firefox**

This procedure was tested on version 37\.0\.2 of Mozilla Firefox\. If you use another version, you might need to adapt the steps accordingly\.

1. Press **F12** to start the developer console\.

1. In the upper right of the developer tools window, click options \(the small gear icon\)\. Under **Common Preferences** select **Enable persistent logs**\. 

1. Select the **Network** tab\. 

1. Reproduce the issue\.

1. Look for a **POST** **SAML** in the table\. Select that row\. In the **Form Data** window on the right, select the **Params** tab and find the **SAMLResponse** element\.

## Apple safari<a name="safari"></a>

**To view a SAML response in safari**

These steps were tested using version 8\.0\.6 \(10600\.6\.3\)\. If you use another version, you might need to adapt the steps accordingly\.

1. Enable Web Inspector in Safari\. Open the **Preferences** window, select the **Advanced** tab, and then select **Show Develop menu in the menu bar**\.

1. Now you can open Web Inspector\. Click **Develop**, then select **Show Web Inspector**\.

1. Select the **Resources** tab\.

1. Reproduce the issue\.

1. Look for a **saml\-signin\.aws\.amazon\.com** request\.

1. Scroll down to find `Request Data` with the name `SAMLResponse`\. The associated value is the Base64\-encoded response\.

## Microsoft Internet Explorer<a name="ie"></a>

**To view a SAML response in Internet Explorer**

The best way to analyze network traffic in Internet Explorer is through the use of a third\-party tool\.
+ Follow the steps at [http://social.technet.microsoft.com/wiki/contents/articles/3286.ad-fs-2-0-how-to-use-fiddler-web-debugger-to-analyze-a-ws-federation-passive-sign-in.aspx](http://social.technet.microsoft.com/wiki/contents/articles/3286.ad-fs-2-0-how-to-use-fiddler-web-debugger-to-analyze-a-ws-federation-passive-sign-in.aspx) to download and install Fiddler and capture the data\.

## What to do with the Base64\-encoded SAML response<a name="whatnext"></a>

Once you find the Base64\-encoded SAML response element in your browser, copy it and use your favorite Base\-64 decoding tool to extract the XML tagged response\.

**Security tip**  
Because the SAML response data that you are viewing might contain sensitive security data, we recommend that you do not use an *online* base64 decoder\. Instead use a tool installed on your local computer that does not send your SAML data over the network\.

**Built\-in option for Windows systems \(PowerShell\):**

```
PS C:\> [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String("base64encodedtext"))
```

**Built\-in option for MacOS and Linux systems:**

```
$ echo "base64encodedtext" | base64 --decode
```