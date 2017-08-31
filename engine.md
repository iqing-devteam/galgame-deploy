# 部署游戏引擎服务器

## 配置游戏引擎

引擎的配置文件在交接包的```/engine/gamecontent/iqa.conf.json```

```javascript
// engine/gamecontent/iqa.conf.json
{
    "imageCDN":"https://image.example.com/",
    "soundCDN":"https://sound.example.com/",
    "customProcessName":"iqing-rip-biligame"
}
```

imageCDN对应七牛镜像image.iqing.in的储存空间

soundCDN对应七牛镜像sound.iqing.in的储存空间

customProcessName对应自定义数据处理名称

## 使用nginx为游戏引擎提供服务， 并设置反向代理

这一版的游戏引擎是部署在合作方的机器中，然后配置反向代理解决跨域问题。

以下是一个nginx配置的示例。

```bash
server {
    listen  80;
    server_name line5-h5-patch-iqing.bilibiligame.net;

    location / {
        root /www/engine; # 交付包的engin文件夹复制到这里
    }

    location /account/bilibili_login/ {
        proxy_pass http://bilibili.iqing.in/bilibili_login/;
    }

    location /ngame/ {
        proxy_pass http://bilibili.iqing.in/ngame/;
    }
}
```
