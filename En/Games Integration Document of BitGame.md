# games integration document of BitGame

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-15 | initialization
0.2 | 2018-04-16 | increase oauth2 authentication

### games integration interface lists of BitGame:


 interface names   |   check
 -- |  --
 1.app authentication|[click to check](https://github.com/BitGameEN/OpenAPI/blob/master/app%e8%ae%a4%e8%af%81.md)
 2.test the Exchange account|[click to check](https://github.com/BitGameEN/OpenAPI/blob/master/%E6%A3%80%E6%B5%8B%E4%BA%A4%E6%98%93%E6%89%80%E8%B4%A6%E6%88%B7.md)
 3.send verification code (invalid)   | [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/%E5%8F%91%E9%80%81%E9%AA%8C%E8%AF%81%E7%A0%81.md)
 4.bind the Exchange account   |   [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/%E7%BB%91%E5%AE%9A%E4%BA%A4%E6%98%93%E6%89%80%E8%B4%A6%E6%88%B7.md)
 5.unbind   |   [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/%E8%A7%A3%E9%99%A4%E7%BB%91%E5%AE%9A%E5%85%B3%E7%B3%BB.md)
 6.withdraw the tokens |   [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/%E6%8F%90%E5%8F%96%E4%BB%A3%E5%B8%81.md)
 7.top up the tokens to the app   |   [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/%E5%85%85%E5%80%BC%E4%BB%A3%E5%B8%81%E5%88%B0%E5%BA%94%E7%94%A8.md)
 8.search user's previous orders (not required)   | [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/%E6%9F%A5%E8%AF%A2%E7%94%A8%E6%88%B7%E8%AE%A2%E5%8D%95%E5%8E%86%E5%8F%B2.md)
 9.user's spent tokens (not required)   | [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/%E7%94%A8%E6%88%B7%E6%B6%88%E8%80%97%E4%BB%A3%E5%B8%81.md)
 
 

### message body code description（http header condition code 200）
code|message|description
--|--|--
0|Success|Success
-999|IPError|IP Restricted
-998|ParameterNull|Parameter Incomplete
-997|ParameterError|Parameter Anomaly
-996|SignError|Verification Failure
-995|ProtocolError|Unsupported Protocol
-994|ExceptionError|Exception Thrown
-993|GameNotOpen|Game Not Open
-990|BalanceError|Insufficient Golds
-989|RequestError|Request Failure
-988|RequestTimeOut|Request Timeout
-987|Error|Uncertain Error
-899|ExUserNotExist|Exchange User Not Exist 
-898|NotBindError|No Binding Between the User And the Exchange Account
-897|VerifyCodeTimeOut|Verification Code Timeout
-896|AccountFreezing|Account Suspension
-895|VerifyCode Fail|Verification Code Error
-894|UserNotExist|User Not Exist
-893|Token Symbol Error|Token Type Error
-892|Amount Error|Amount Error
-891|Order Processing|Order Processing
-890|Order Fail|Order Failed
-889|Bind BitAccount Error|Binding Failed
-888|Please untie it first|Please Unbind
-887|Google code fail|Google Code Error
-886|Google code not bind|Google Authenticator Not Bind
### abnormal code description（http header condition code）
code|message|description
--|--|--
200|OK|Success
401|Unauthorized|Unauthorized
403|Forbidden|Resources Forbidden
404|Not Found|Resources Not Found
