# interface of topping up the tokens to the app

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-15|establish
0.2|2018-04-27|update
0.3|2018-05-02|increase the interface parameter, and adjust the MD5 signature method
0.4|2018-08-02|adjust the interface code parameter	
### description:
The app side requests to invoke this interface. To shift the balance in the player's Exchange account to the app needs the binding between the app account and the Exchange account, and the latest verification code is also needed. The interface should be invoked by the server and IP whitelist is needed.


### invoking methods

``` 
Url(test):      https://open.bitgamex.org/recharge
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
 amount |   double（32，18）    |Y|   the amount of the token transactions
 appid    |   int |Y|   app number (provided by the Exchange)
 apporderno    |   String  |Y|   app order number
 appuid   |   String  |Y|   the unique identification of user in the app
 bitaccount    | String    |Y| username in the Exchange(mail/phone, phone format：country code-phone number. example: 86-13901234567)
 chainname|String|Y| the public chain that the tokens are in (such as eth), lower-case letters
 code   |   String  |Y|   user can obtain it from the interface of sending verification code
 paramdata  |   String  |Y|   the app passthrough parameter will be returned in its original way
 sign     | String  |Y| signature (all parameters, sorted by parameter names(in addition to 'sign'), plus salt will be conducted MD5 encoding), the following signature example for reference
 timestamp|long|Y| standard time stamp should be accurate to milliseconds, in long type. 
 tokensymbol    |   String  |Y|   the tokens marking (such as bgx), lower-case letters
 uid|int|Y| the unique identification of the user in Game Center
 
### signature methods
 ```
 sign=MD5((amount=0.5&appid=1&apporderno=2018041515401412&appuid=12&bitaccount=test@gmail.com&chainname=eth&code=1234&paramdata=MTIzNDU2&timestamp=1525249211123&tokensymbol=bgx&uid=1)+salt).toLowerCase()
 
all parameters, sorted by parameter names, plus salt will be conducted MD5 encoding with 32 lower-case letter numbers (with empty parameter, alphabetic string "" is needed, and no null value.)
salt is provided by Bit Game Center
 ```

#### Request
  ```
 {
    "amount":0.5,
    "appid": 1,
    "apporderno":"2018041515401412",
    "appuid":"12",
    "bitaccount": "test@gmail.com",
    "chainname":"eth",
    "code":"1234",
    "paramdata":"MTIzNDU2",
    "sign": "f27d13de2d7e02eca56ad8c62b0703de",
    "timestamp":1525249211123,
    "tokensymbol":"bgx",
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

### abnormal code description:[click to check](https://github.com/BitGameEN/OpenAPI/blob/master/BitGame%E6%B8%B8%E6%88%8F%E5%AF%B9%E6%8E%A5%E6%96%87%E6%A1%A3.md)
