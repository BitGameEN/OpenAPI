# interface of sending verification code (invalid)

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-15|establish
0.2|2018-04-27|update
0.3|2018-05-02|increase the interface parameter, and adjust the MD5 signature method
0.3|2018-05-02|adjust the interface code parameter
### description:
The app side requests to invoke this interface and sends verification code to the mail or phone bound with the Exchange account. The term of validity of this code is 5 minutes. To avoid multiple sending, the app should set restriction, such as 60 seconds interval of the next sending. The interface should be invoked by the server and IP whitelist is needed.


### invoking methods

``` 
Url(test):      https://open.bitgamex.org/api/sendverifycode
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
 appuid   |   String  |Y|   the unique identification of user in the app
 bitaccount    | String    |Y| username in the Exchange(mail/phone, phone format：country code-phone number. example: 86-13901234567)
 language   |   String  |Y|   language version of the users
 sendtype   |   int |Y | 1: bind the account, 2: withdraw tokens to Exchange, 3: top up the tokens to the game, 4: unbind
 sign     | String        |Y| signature(all parameters, sorted by parameter names (in addition to 'sign')， plus salt will be conducted MD5 encoding), the following signature example for reference
 timestamp|long|Y| standard time stamp should be accurate to milliseconds, in long type
 uid    |int    |Y| After successfully bound, the unique identification in Game Center can be seen in the return data. 0 for first binding. After successfully bound, please send the operating parameter uid (!=0) of type 2, 3, 4
 
 
 ### signature methods
 ```
 sign=MD5((appid=1&appuid=12&bitaccount=test@gmail.com&language=en-US&sendtype=1&timestamp=1525249211123&uid=0)+salt).toLowerCase()
 
all parameters, sorted by parameter names, plus salt will be conducted MD5 encoding with 32 lower-case letter numbers (with empty parameter, alphabetic string "" is needed, and no null value.)
salt is provided by Bit Game Center
 ```
#### Request
  ```
 {
    "appid": 1,
    "appuid":"12",
    "bitaccount": "test@gmail.com",
    "language":"en-US",
    "sendtype":1,
    "sign": "b5725415c70654260e740c1712550f1f",
    "timestamp":1525249211123,
    "uid":0
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

### abnormal code description:[click to check](https://github.com/BitGameEN/OpenAPI/blob/master/BitGame%E6%B8%B8%E6%88%8F%E5%AF%B9%E6%8E%A5%E6%96%87%E6%A1%A3.md)
