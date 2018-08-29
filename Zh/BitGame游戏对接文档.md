# BitGame游戏对接文档

## 版本信息
版本 | 时间 |   备注
-- | -- |   --
0.1 | 2018-04-15 | 初始
0.2 | 2018-04-16 | 增加oauth2认证

### BitGame游戏对接接口列表:


 接口名称   |   查看
 -- |  --
 1.app认证|[点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/app%E8%AE%A4%E8%AF%81.md)
 2.检测交易所账户|[点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/%E6%A3%80%E6%B5%8B%E4%BA%A4%E6%98%93%E6%89%80%E8%B4%A6%E6%88%B7.md)
 3.发送验证码（已作废）   | [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/%E5%8F%91%E9%80%81%E9%AA%8C%E8%AF%81%E7%A0%81.md)
 4.绑定交易所账户   |   [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/%E7%BB%91%E5%AE%9A%E4%BA%A4%E6%98%93%E6%89%80%E8%B4%A6%E6%88%B7.md)
 5.解除绑定关系   |   [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/%E8%A7%A3%E9%99%A4%E7%BB%91%E5%AE%9A%E5%85%B3%E7%B3%BB.md)
 6.提取代币 |   [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/%E6%8F%90%E5%8F%96%E4%BB%A3%E5%B8%81.md)
 7.充值代币到应用   |   [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/%E5%85%85%E5%80%BC%E4%BB%A3%E5%B8%81%E5%88%B0%E5%BA%94%E7%94%A8.md)
 8.查询用户订单历史(非必接)   | [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/%E6%9F%A5%E8%AF%A2%E7%94%A8%E6%88%B7%E8%AE%A2%E5%8D%95%E5%8E%86%E5%8F%B2.md)
 9.用户消耗代币(非必接)   | [点击查看](https://github.com/BitGameEN/OpenAPI/blob/master/Zh/%E7%94%A8%E6%88%B7%E6%B6%88%E8%80%97%E4%BB%A3%E5%B8%81.md)
 
 

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
-895|VerifyCode Fail|验证码错误
-894|UserNotExist|游戏中心用户不存在
-893|Token Symbol Error|代币类型
-892|Amount Error|金额不合法
-891|Order Processing|订单处理中
-890|Order Fail|订单已失败
-889|Bind BitAccount Error|绑定失败
-888|Please untie it first|请先解除绑定
-887|Google code fail|GoogleCode验证失败
-886|Google code not bind|Google验证器未绑定

### 异常code描述（http header 状态码）
code|message|描述
--|--|--
200|OK|成功
401|Unauthorized|未经授权
403|Forbidden|资源不可用
404|Not Found|无法找到指定位置的资源
