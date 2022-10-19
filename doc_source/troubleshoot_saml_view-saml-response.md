# How to view a SAML response in your browser for troubleshooting<a name="troubleshoot_saml_view-saml-response"></a>

The following procedures describe how to view the SAML response from your service provider from in your browser when troubleshooting a SAML 2\.0–related issue\. 

For all browsers, go to the page where you can reproduce the issue\. Then follow the steps for the appropriate browser:

**Topics**
+ [Google Chrome](#chrome)
+ [Mozilla Firefox](#firefox)
+ [Apple Safari](#safari)
+ [What to do with the Base64\-encoded SAML response](#whatnext)

## Google Chrome<a name="chrome"></a>

**To view a SAML response in Chrome**

These steps were tested using version 106\.0\.5249\.103 \(Official Build\) \(arm64\) of Google Chrome\. If you use another version, you might need to adapt the steps accordingly\.

1. Press **F12** to start the **Developer Tools** console\.

1. Select the **Network** tab, and then select **Preserve log** in the upper left of the **Developer Tools** window\.

1. Reproduce the issue\.

1. \(Optional\) If the **Method** column is not visible in the **Developer Tools** **Network** log pane, right\-click on any column label and choose **Method** to add the column\.

1. Look for a **SAML Post** in the **Developer Tools** **Network** log pane\. Select that row, and then view the **Payload** tab at the top\. Look for the **SAMLResponse** element that contains the encoded request\. The associated value is the Base64\-encoded response\.

## Mozilla Firefox<a name="firefox"></a>

**To view a SAML response in Firefox**

This procedure was tested on version 105\.0\.3 \(64\-bit\) of Mozilla Firefox\. If you use another version, you might need to adapt the steps accordingly\.

1. Press **F12** to start the **Web Developer Tools** console\.

1. Select the **Network** tab\. 

1. In the upper right of the **Web Developer Tools **window, choose options \(the small gear icon\)\. Select **Persist logs**\. 

1. Reproduce the issue\.

1. \(Optional\) If the **Method** column is not visible in the **Web Developer Tools** **Network** log pane, right\-click on any column label and choose **Method** to add the column\.

1. Look for a **POST** **SAML** in the table\. Select that row, and then view the **Request** tab and find the **SAMLResponse** element\. The associated value is the Base64\-encoded response\.

## Apple Safari<a name="safari"></a>

**To view a SAML response in Safari**

These steps were tested using version 16\.0 \(17614\.1\.25\.9\.10, 17614\) of Apple Safari\. If you use another version, you might need to adapt the steps accordingly\.

1. Enable Web Inspector in Safari\. Open the **Preferences** window, select the **Advanced** tab, and then select **Show Develop menu in the menu bar**\.

1. Now you can open Web Inspector\. Choose **Develop** in the menu bar, then select **Show Web Inspector**\.

1. Select the **Network** tab\.

1. In the upper left of the **Web Inspector** window, choose options \(the small circle icon containing three horizontal lines\)\. Select **Preserve Log**\.

1. \(Optional\) If the **Method** column is not visible in the **Web Inspector** **Network** log pane, right\-click on any column label and choose **Method** to add the column\.

1. Reproduce the issue\.

1. Look for a **POST** **SAML** in the table\. Select that row, and then view the Headers tab\.

1. Look for the **SAMLResponse** element that contains the encoded request\. Scroll down to find `Request Data` with the name `SAMLResponse`\. The associated value is the Base64\-encoded response\.

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