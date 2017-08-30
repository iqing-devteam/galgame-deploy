# 部署游戏引擎服务器

这一版的游戏引擎是部署在合作方的机器中，然后配置反向代理解决跨域问题。

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
