# app认证

## 版本信息
版本 | 时间 |   备注
-- | -- |   --
0.1 | 2018-04-16

### 描述:
openAPI基于oauth2提供安全的接口服务。app必须通过认证拿到token来做后续的接口的调用。token的有效期为3600秒


### 调用方法

``` 
Url(测试):  https://open.bitgamex.org/api/oauth/token
Method:     POST

```
### headers

``` 
Content-Type:   application/x-www-form-urlencoded
Authorization:  Basic base64Encode(client_id:client_secret)    

```

### 请求参数：


 参数           |     类型        |必填| 描述         
------------ |     -------------|--|         -----------
 grant_type    | String    |Y| Oauth2类型
 client_id    | String    |Y| bitgame提供
 client_secret     | String        |Y| bitgame提供   
 
 
 #### Request
  ```
 
https://open.bitgamex.org/api/oauth/token?grant_type=client_credentials

  ```
  
### 成功返回：
HTTP/1.1 200 OK
``` 
{
"access_token":"5ad5fc52cbfb81c63e0e073013a234f61fbd43c390a2c68de71b941d",
"expires_in":3600,
"token_type":"bearer"}
```
### 失败返回：
HTTP/1.1 403 Forbidden
``` 
{
    "error": "invalid_request",
    "error_description": "The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed."
}
```

### 异常code描述：[点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/BitGame%E6%B8%B8%E6%88%8F%E5%AF%B9%E6%8E%A5%E6%96%87%E6%A1%A3.md)
