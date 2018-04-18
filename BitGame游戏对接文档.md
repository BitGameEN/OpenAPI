# BitGame游戏对接文档

## 版本信息
版本 | 时间 |   备注
-- | -- |   --
0.1 | 2018-04-15 | 初始
0.2 | 2018-04-16 | 增加oauth2认证

### BitGame游戏对接接口列表:


 接口名称   |   查看
 -- |  --
 1.app认证|[点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/app%e8%ae%a4%e8%af%81.md)
 2.验证交易所账户|[点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/%E9%AA%8C%E8%AF%81%E4%BA%A4%E6%98%93%E6%89%80%E8%B4%A6%E6%88%B7.md)
 3.发送验证码   | [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/%E5%8F%91%E9%80%81%E9%AA%8C%E8%AF%81%E7%A0%81.md)
 4.绑定交易所账户   |   [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/%E7%BB%91%E5%AE%9A%E4%BA%A4%E6%98%93%E6%89%80%E8%B4%A6%E6%88%B7.md)
 5.提取代币 |   [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/%E6%8F%90%E5%8F%96%E4%BB%A3%E5%B8%81.md)
 6.充值代币到应用   |   [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/%E5%85%85%E5%80%BC%E4%BB%A3%E5%B8%81%E5%88%B0%E5%BA%94%E7%94%A8.md)
 7.查询用户订单历史   | [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/%E6%9F%A5%E8%AF%A2%E7%94%A8%E6%88%B7%E8%AE%A2%E5%8D%95%E5%8E%86%E5%8F%B2.md)
 8.用户消耗代币   | [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/%E7%94%A8%E6%88%B7%E6%B6%88%E8%80%97%E4%BB%A3%E5%B8%81.md)
 
 

### 消息体内状态码code描述（http header 状态码 200）
code|message|描述
--|--|--
0|Success|成功
-999|IPError|IP受限
-998|ParameterNull|参数不全
-997|ParameterError|参数异常
-996|SignError|效验失败
-995|ProtocolError|协议不支持
-994|ExceptionError|异常抛出
-993|GameNotOpen|游戏未开放
-990|BalanceError|金币不足
-989|RequestError|请求失败
-988|RequestTimeOut|请求超时
-987|Error|未确定的错误
-899|ExUserNotExist|交易所用户不存在 
-898|NotBindError|游戏用户与交易所账户不是绑定关系
-897|VerifyCodeTimeOut|验证码超时
-896|AccountFreezing|账户冻结无法操作

### 异常code描述（http header 状态码）
code|message|描述
--|--|--
200|OK|成功
401|Unauthorized|未经授权
403|Forbidden|资源不可用
404|Not Found|无法找到指定位置的资源
