# interface of unbinding

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-27|establish
0.3|2018-05-02|increase the interface parameter, and adjust the MD5 signature method
0.4|2018-08-02|adjust the interface code parameter
### description:
The app side requests to invoke this interface. The user will invoke this interface when unbinding or changing the binding. After unbinding, the transaction cannot be conducted and rebindin of the Exchange account is needed. The interface should be invoked by the server and IP whitelist is needed.


### invoking methods

``` 
Url(test):      https://open.bitgamex.org/api/unbindaccount
Method:         POST

```
### headers

``` 
Content-Type:   Application/Json
Authorization:  Bearer <token>    

```
### request parameter:


 parameter           |     type        |required| description         
------------ |     -------------|--|         -----------
 appid    |   int |Y|   app number (provided by the Exchange)
 bitaccount    | String    |Y| username in the Exchange(mail/phone, phone format：country code-phone number. example: 86-13901234567)
 code   |   String  |Y|   user can obtain it from the interface of sending verification code
 sign     | String        |Y| signature(all parameters, sorted by parameter names (in addition to 'sign')， plus salt will be conducted MD5 encoding), the following signature example for reference
 timestamp|long|Y| standard time stamp should be accurate to milliseconds, in long type
 uid|int|Y| the unique identification in Game Center. After successfully bound, it will be returned from the interface.
 
 
 ### signature methods
 ```
 sign=MD5((appid=1&bitaccount=test@gmail.com&code=1234&key=e10adc3949ba59abbe56e057f20f883e&timestamp=1525249211123&uid=1)+salt).toLowerCase()
 
all parameters, sorted by parameter names, plus salt will be conducted MD5 encoding with 32 lower-case letter numbers (with empty parameter, alphabetic string "" is needed, and no null value.)
salt is provided by Bit Game Center
 ```
 
### Request
  ```
 {
    "appid": 1,
    "bitaccount": "test@gmail.com",
    "code":"1234",
    "sign": "03df9c89ac110cad0eaad2102841fcf9",
    "timestamp":1525249211123,
    "uid":1
 }
  ```
### successful return:
HTTP/1.1 200 OK
```
{
    "code": 0,
    "message": "success",
    "data": ""
}
```
### failed return:
HTTP/1.1 200 OK
```
{
    "code": -987,
    "message": "error message",
    "data": ""
}
```


### abnormal code description: [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/BitGame%E6%B8%B8%E6%88%8F%E5%AF%B9%E6%8E%A5%E6%96%87%E6%A1%A3.md)
