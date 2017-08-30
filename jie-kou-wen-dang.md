# 后端接口

> 登录/注册接口

```
Method GET

http://bilibili.iqing.in/bilibili_login/?test=1&uname=1_15033405428099267212&token=1_150340542809976434
```

uname: 用户昵称

token:  合作方token，类似于id

sign: 前面query的签名验证

test：当test=1的时候跳过sign验证\(方便测试\)

> 读档接口

```js
Method  POST 
http://bilibili.iqing.in/ngame/654/archive/

Header:
Content-Type: application/json

 Body

{
  "channel_token":"1b6fe627a0b34370364c4909b0437f28d59d2d45",  // android_token
  "client_type":2 // 这个指定了客户端为安卓
}
```



