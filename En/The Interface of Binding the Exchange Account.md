# interface of binding the Exchange account

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-15|establish
0.3|2018-05-02|increase the interface parameter, and adjust the MD5 signature method

### description:
The app side requests to invoke this interface. The app account should bind the Exchange account for the transaction-related verification validity. The interface should be invoked by the server and IP whitelist is needed.


### invoking methods

``` 
Url(test):      https://open.bitgamex.org/api/bindaccount
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
 appid    |   int |Y|   app number(provided by the Exchange)
 appuid   |   String  |Y|   the unique identification of user in the app
 bitaccount    | String    |Y| username in the Exchange(mail/phone, phone format：country code-phone number. example: 86-13901234567)
 code   |   String  |Y|   user can obtain it from the interface of sending verification code
 sign     | String        |Y| signature(all parameters, sorted by parameter names (in addition to 'sign'), plus salt will be conducted MD5 encoding), the following signature example for reference
 timestamp|long|Y| standard time stamp should be accurate to milliseconds, in long type
 
 
 ### signature methods
 ```
 sign=MD5((appid=1&appuid=12&bitaccount=test@gmail.com&code=1234&timestamp=1525249211123)+salt).toLowerCase()
 
all parameters, sorted by parameter names, plus salt will be conducted MD5 encoding with 32 lower-case letter numbers (with empty parameters, alphabetic string "" is needed, and no null value.)
salt is provided by Bit Game Center
 ```
 
### Request
  ```
 {
    "appid": 1,
    "appuid":"12",
    "bitaccount": "test@gmail.com",
    "code":"1234",
    "sign": "03df9c89ac110cad0eaad2102841fcf9",
    "timestamp":1525249211123
 }
  ```
### successful return:
HTTP/1.1 200 OK
```
{
    "code": 0,
    "message": "success",
    "data": "
    {
        "uid":10000
    }
    "
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
