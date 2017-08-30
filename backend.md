# 部署后端服务

后端服务现在暂时由轻文轻小说托管运行。 下次发布会包括如何部署后端的方法。

## 核心架构

后端服务由Django Web Server + Mysql构成

## 实际部署方法

Django Web Server被封装在Docker容器之中，这些容器由阿里云容器服务托管和构建。

```yml
# 编排模板
bilibili:
  image: 'registry-internal.cn-shenzhen.aliyuncs.com/iqing/bilibili-test:latest'
  command:
    - run
  restart: always
  environment:
    - WWW_ROOT_DIR=/wwwroot
    - WWW_WEB_DIR=/wwwroot/www
    - WWW_LOG_DIR=/wwwroot/log
    - PROJECT_NAME=bilibili
    - DJANGO_SETTINGS_MODULE=bilibili.settings_prodn
    - WORK_CLASS=17
  expose:
    - 22/tcp
    - 8080/tcp
  labels:
    aliyun.latest_image: true
    aliyun.scale: '20'
    aliyun.routing.port_8080: bilibili.iqing.in;bilibili;line5-h5-patch-iqing.bilibiligame.net
    aliyun.rolling_updates: 'true'
    aliyun.rolling_updates.parallelism: "10"
    aliyun.log_store_name: /wwwroot/log/bilibili-access-gunicorn.log
```
