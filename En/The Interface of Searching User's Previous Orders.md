# interface of searching user's previous orders

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-15|establish
0.2|2018-04-27|update
0.3|2018-05-02|increase the interface parameter, and adjust the MD5 signature method

### description:
The app side requests to invoke this interface. To search user's previous orders of withdrawing and topping up needs the binding between the app account and the Exchange account, and the latest verification code is also needed. The interface should be invoked by the server and IP whitelist is needed.


### invoking methods

``` 
Url(test):      https://open.bitgamex.org/api/getorderlist
Method:         POST

```
### headers

``` 
Content-Type:   Application/Json
Authorization:  Bearer <token>    

```
### request parameter:


 parameter           |     type        |required| description         
------------ |     -------------|---|         -----------
 appid    |   int |Y|   app number(provided by the Exchange)
 uid   |   String  |Y|   the unique identification of user in the app
 bitaccount    | String    |Y| username in the Exchange(mail/phone, phone format：country code-phone number. example: 86-13901234567)
 ordertype  |   int |Y|   the order list types to obtain(1:the order to withdraw 2:the order to top up)
 pagenumber  |   int  |Y| page number (10 per page)
 rowcount   |   int |Y|   the number of order list that returns in the interface
 sign     | String  |Y| signature(all parameters, sorted by parameter names (in addition to 'sign'), plus salt will be conducted MD5 encoding), the following signature example for reference 
 
 
 ### signature methods
 ```
 sign=MD5((appid=1&bitaccount=test@gmail.com&ordertype=1&pagenumber=1&rowcount=10&timestamp=1525249211123&uid=1)+salt).toLowerCase()
 
 all parameters,sorted by parameter names, after encrypting, plus salt will be conducted MD5 encoding with 32 lower-case letter numbers (with empty parameter, alphabetic string "" is needed, and no null value.)
 ```
#### Request
  ```
 {
    "appid":1,
    "bitaccount":"123456",
    "ordertype":1,
    "pagenumber":1,
    "rowcount":10,
    "sign":"0ba9127dbf09d06a549e1e932a64e2dd",
    "timestamp":1525249211123,
    "uid":1
 }
  ```

### successful return:
HTTP/1.1 200 OK
``` 
{
    "code":0,
    "message":"Success",
    "data":{
        "total_order_count":2,
        "order_list":"[
        {
            \"tokensymbol\":\"btc\",
            \"date\":1525262896000,
            \"amount\":20.0,
            \"ordertype\":1
        },
        {
            \"tokensymbol\":\"btc\",
            \"date\":1525262896123,
            \"amount\":10.0,
            \"ordertype\":1
        }]"
        
    }
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
