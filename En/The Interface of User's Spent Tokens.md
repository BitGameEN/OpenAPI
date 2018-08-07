# interface of user's spent tokens (excluding the application with tokens fully managed by BIT.GAME )

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-15

### description:
The app side requests to invoke this interface. The player will invoke this interface when spending the tokens. To calculate the income proof of the developer, the rules are that the spent tokens by the player will be shifted to the disposable account of the developer, and the developer has the run of the tokens in that account. The interface should be invoked by the server and IP whitelist is needed.


### invoking methods

``` 
Url:            https://api.bit.game/api/usetoken
Method:         POST

```
### headers

``` 
Content-Type:   Application/Json
Authorization:  Bearer <token>    

```
### request parameter:


 parameter           |     type        |required| description        
------------ |     -------------|------|         -----------
 amount  |   double（32，18） |Y|   the amount of the spent tokens
 appid    |   int |Y|   app number (provided by the Exchange)
 appuid   |   String  |Y|   the unique identification of user in the app
 paramdata  |   String  |Y|   the app passthrough parameter will be returned in its original way（Base64 coded format, 200 length)
 sign     | String  |Y| signature (all parameters, sorted by parameter names (in addition to 'sign')， plus salt will be conducted MD5 encoding), the following signature example for reference
 timestamp|long|Y| standard time stamp should be accurate to milliseconds, in long type 
 tokensymbol    |   String  |Y|   the tokens marking (such as bgx), lower-case letters
 uid|int|Y| the unique identification in Game Center
 
 
 ### signature methods
 ```
 sign=MD5((amount=0.1&appid=1&appuid=12&bitaccount=test@gmail.com&paramdata=MTIzNDU2&timestamp=1525249211123&tokensymbol=bgx&uid=1)+salt).toLowerCase()
 
all parameters, sorted by parameter names, plus salt will be conducted MD5 encoding with 32 lower-case letter numbers (with empty parameter, alphabetic string "" is needed, and no null value.)
salt is provided by Bit Game Center
 ```
#### Request
  ```
 {
    "amount":0.1,
    "appid": 1,
    "appuid":"12",
    "bitaccount":"test@gmail.com",
    "paramdata":"MTIzNDU2",
    "sign": "66f985763e344ddf788938492e0019ea",
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
    "date": ""
}
```

### failed return:
HTTP/1.1 200 OK
```
{
    "code": -987,
    "message": "error message",
    "date": ""
}
```


### abnormal code description: [click to check](https://github.com/BitGameEN/OpenAPI/blob/master/BitGame%E6%B8%B8%E6%88%8F%E5%AF%B9%E6%8E%A5%E6%96%87%E6%A1%A3.md)
