# IAM JSON policy elements: Supported data types<a name="reference_policies_elements_datatypes"></a>

This section lists the data types that are supported when you specify values in JSON policies\. The policy language doesn't support all types for each policy element; for information about each element, see the preceding sections\.
+ Strings
+ Numbers \(Ints and Floats\)
+ Boolean
+ Null
+ Lists
+ Maps
+ Structs \(which are just nested Maps\)

The following table maps each data type to the serialization\. Note that all policies must be in UTF\-8\. For information about the JSON data types, go to [RFC 4627](http://tools.ietf.org/html/rfc4627)\. 


****  

| Type | JSON | 
| --- | --- | 
|  String  |  String  | 
|  Integer  |  Number  | 
|  Float  |  Number  | 
|  Boolean  |  true false  | 
|  Null  |  null  | 
|  Date  |  String adhering to the [W3C Profile of ISO 8601](http://www.w3.org/TR/NOTE-datetime)  | 
|  IpAddress  |  String adhering to [RFC 4632](http://tools.ietf.org/html/rfc4632)  | 
|  List  |  Array  | 
|  Object  |  Object  | 