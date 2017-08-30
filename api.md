# 后端接口

> 登录/注册接口

```
Method GET
http://bilibili.iqing.in/bilibili_login/?test=1&uname=1_15033405428099267212&token=1_150340542809976434
```

说明：
 注册与登录API相同，如果用户已经注册则登录，如果未注册则为注册

参数说明： 
uname: 用户名

token: 第三方提供的token，用来标识用户

如果添加 test=1 则跳过sign验证

> 读档接口

```
Method  POST 
http://bilibili.iqing.in/ngame/654/archive/

Header:
Content-Type: application/json

 Body

{
  "channel_token":"1b6fe627a0b34370364c4909b0437f28d59d2d45",  # android_token
  "client_type":2 # 这个指定了客户端为安卓
}
```

说明：

当channel_token等于登录接口返回的android_token时， client_type必须为2。

client_type与channel_token是对应的。

> 存档接口

```
 Method PUT
Url: http://bilibili.iqing.in/ngame/654/archive/

Header:

Content-Type: application/json

Body
{
  "channel_token":"1b6fe627a0b34370364c4909b0437f28d59d2d45",    "client_type":2,  
   "content": "1234" # 存档内容
}
```

说明： 

当channel_token等于登录接口返回的android_token时， client_type必须为2。

client_type与channel_token是对应的。
