# interface of testing the Exchange account

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-27|establish
0.3|2018-05-02|increase the interface parameter, and adjust the MD5 signature method

### description:
The app side requests to invoke this interface and determines whether to select this interface or not according to the actual needs. The interface should be invoked by the server and IP whitelist is needed.


### invoking methods

``` 
Url(test):      https://open.bitgamex.org/api/checkaccount
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
 sign     | String        |Y| signature(all parameters, sorted by parameter names (in addition to 'sign')， plus salt will be conducted MD5 encoding), the following signature example for reference
 timestamp|long|Y| standard time stamp should be accurate to milliseconds, in long type
 
 
 ### signature methods
 ```
 sign=MD5((appid=1&bitaccount=test@gmail.com&timestamp=1525249211123)+salt).toLowerCase()
 
 all parameters, sorted by parameter names, plus salt will be conducted MD5 encoding with 32 lower-case letter numbers (with empty parameter, alphabetic string "" is needed, and no null value.)
salt is provided by Bit Game Center
 ```
#### Request
  ```
 {
    "appid":1,
    "bitaccount":"test@gmail.com",
    "sign":"7012bc3ee2d0729ff10e15ea748fc380",
    "timestamp":1525249211123
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
