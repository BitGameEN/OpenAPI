# app authentication

## version information
version | time |   note
-- | -- |   --
0.1 | 2018-04-16

### description:
Open API is based on oauth2 to provide safe interface services. The app must be authenticated to acquire the tokens for invoking the subsequent interfaces. Term of validity of the tokens is 3,600 seconds.


### invoking methods

``` 
Url:            https://api.bit.game/api/oauth/token
Method:         POST

```
### headers

``` 
Content-Type:   application/x-www-form-urlencoded
Authorization:  Basic base64Encode(client_id:client_secret)    

```

### request parameter:


 parameter           |     type        |required| description         
------------ |     -------------|--|         -----------
 grant_type    | String    |Y| Oauth2 type
 client_id    | String    |Y| provided by BitGame
 client_secret     | String        |Y| provided by BitGame   
 
 
 #### Request
  ```
 
https://api.bit.game/api/oauth/token?grant_type=client_credentials

  ```
  
### successful return:
HTTP/1.1 200 OK
``` 
{
"access_token":"5ad5fc52cbfb81c63e0e073013a234f61fbd43c390a2c68de71b941d",
"expires_in":3600,
"token_type":"bearer"}
```
### failed return:
HTTP/1.1 403 Forbidden
``` 
{
    "error": "invalid_request",
    "error_description": "The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed."
}
```

### anormal code description:[click to check](https://github.com/BitGameEN/OpenAPI/blob/master/BitGame%E6%B8%B8%E6%88%8F%E5%AF%B9%E6%8E%A5%E6%96%87%E6%A1%A3.md)
