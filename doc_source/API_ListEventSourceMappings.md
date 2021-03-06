# ListEventSourceMappings<a name="API_ListEventSourceMappings"></a>

Returns a list of event source mappings you created using the `CreateEventSourceMapping` \(see [CreateEventSourceMapping](API_CreateEventSourceMapping.md)\)\. 

For each mapping, the API returns configuration information\. You can optionally specify filters to retrieve specific event source mappings\.

If you are using the versioning feature, you can get list of event source mappings for a specific Lambda function version or an alias as described in the `FunctionName` parameter\. For information about the versioning feature, see [AWS Lambda Function Versioning and Aliases](http://docs.aws.amazon.com/lambda/latest/dg/versioning-aliases.html)\. 

This operation requires permission for the `lambda:ListEventSourceMappings` action\.

## Request Syntax<a name="API_ListEventSourceMappings_RequestSyntax"></a>

```
GET /2015-03-31/event-source-mappings/?EventSourceArn=EventSourceArn&FunctionName=FunctionName&Marker=Marker&MaxItems=MaxItems HTTP/1.1
```

## URI Request Parameters<a name="API_ListEventSourceMappings_RequestParameters"></a>

The request requires the following URI parameters\.

 ** EventSourceArn **   
The Amazon Resource Name \(ARN\) of the Amazon Kinesis stream\. \(This parameter is optional\.\)  
Pattern: `arn:aws:([a-zA-Z0-9\-])+:([a-z]{2}-[a-z]+-\d{1})?:(\d{12})?:(.*)` 

 ** FunctionName **   
The name of the Lambda function\.  
 You can specify the function name \(for example, `Thumbnail`\) or you can specify Amazon Resource Name \(ARN\) of the function \(for example, `arn:aws:lambda:us-west-2:account-id:function:ThumbNail`\)\. If you are using versioning, you can also provide a qualified function ARN \(ARN that is qualified with function version or alias name as suffix\)\. AWS Lambda also allows you to specify only the function name with the account ID qualifier \(for example, `account-id:Thumbnail`\)\. Note that the length constraint applies only to the ARN\. If you specify only the function name, it is limited to 64 characters in length\.   
Length Constraints: Minimum length of 1\. Maximum length of 140\.  
Pattern: `(arn:aws:lambda:)?([a-z]{2}-[a-z]+-\d{1}:)?(\d{12}:)?(function:)?([a-zA-Z0-9-_]+)(:(\$LATEST|[a-zA-Z0-9-_]+))?` 

 ** Marker **   
Optional string\. An opaque pagination token returned from a previous `ListEventSourceMappings` operation\. If present, specifies to continue the list from where the returning call left off\. 

 ** MaxItems **   
Optional integer\. Specifies the maximum number of event sources to return in response\. This value must be greater than 0\.  
Valid Range: Minimum value of 1\. Maximum value of 10000\.

## Request Body<a name="API_ListEventSourceMappings_RequestBody"></a>

The request does not have a request body\.

## Response Syntax<a name="API_ListEventSourceMappings_ResponseSyntax"></a>

```
HTTP/1.1 200
Content-type: application/json

{
   "EventSourceMappings": [ 
      { 
         "BatchSize": number,
         "EventSourceArn": "string",
         "FunctionArn": "string",
         "LastModified": number,
         "LastProcessingResult": "string",
         "State": "string",
         "StateTransitionReason": "string",
         "UUID": "string"
      }
   ],
   "NextMarker": "string"
}
```

## Response Elements<a name="API_ListEventSourceMappings_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** EventSourceMappings **   
An array of `EventSourceMappingConfiguration` objects\.  
Type: Array of [EventSourceMappingConfiguration](API_EventSourceMappingConfiguration.md) objects

 ** NextMarker **   
A string, present if there are more event source mappings\.  
Type: String

## Errors<a name="API_ListEventSourceMappings_Errors"></a>

 **InvalidParameterValueException**   
One of the parameters in the request is invalid\. For example, if you provided an IAM role for AWS Lambda to assume in the `CreateFunction` or the `UpdateFunctionConfiguration` API, that AWS Lambda is unable to assume you will get this exception\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
The resource \(for example, a Lambda function or access policy statement\) specified in the request does not exist\.  
HTTP Status Code: 404

 **ServiceException**   
The AWS Lambda service encountered an internal error\.  
HTTP Status Code: 500

 **TooManyRequestsException**   
   
HTTP Status Code: 429

## See Also<a name="API_ListEventSourceMappings_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/lambda-2015-03-31/ListEventSourceMappings) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/lambda-2015-03-31/ListEventSourceMappings) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/lambda-2015-03-31/ListEventSourceMappings) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/lambda-2015-03-31/ListEventSourceMappings) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/lambda-2015-03-31/ListEventSourceMappings) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/lambda-2015-03-31/ListEventSourceMappings) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/lambda-2015-03-31/ListEventSourceMappings) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/lambda-2015-03-31/ListEventSourceMappings) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/lambda-2015-03-31/ListEventSourceMappings) 