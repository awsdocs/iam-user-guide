# Retrieving Your Lost or Forgotten Passwords or Access Keys<a name="id_credentials_access-keys_retrieve"></a>

For security reasons, you ***cannot*** retrieve console passwords or the secret access key part of an access key pair after you create it\. If you lose one of these, it cannot be recovered and you must have your administrator reset your password or create a new access key for you, as appropriate\.

If you have the permissions needed to create your own access keys, you can find instructions for creating a new one at [Creating, Modifying, and Viewing Access Keys \(Console\)](id_credentials_access-keys.md#Using_CreateAccessKey)\.

You should follow best practice and periodically change your password and AWS access keys\. In AWS, you change access keys by *rotating* them\. This means that you create a new one, configure your application\(s\) to use the new key, and then delete the old one\. You are allowed to have two access key pairs active at the same time for just this reason\. For more information, see [Rotating Access Keys](id_credentials_access-keys.md#Using_RotateAccessKey)\.