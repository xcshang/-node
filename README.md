系统简介
===========

- [1. 项目简介](#1-项目简介)
- [2. 目录介绍](#2-目录介绍)
- [3. 依赖服务](#3-依赖服务)
- [4. 环境配置](#4-环境配置)
- [5. 系统运行](#5-系统运行)

## 1. 系统简介
 本系统采用 spring boot + mybatis + freemarker 
## 2. 代码目录介绍
gulp: 前端打包工具
nodejs: 前端运行环境
src-css: 前端CSS
src-js: 前端JS
src-template: 前端FTL
src-lib: 前端lib
src-main-resources: 后端配置目录
src-main-Java: 后端代码目录


## 3. 依赖服务
1.系统登录状态依赖网易云账号服务
2.表单提交时滑块验证、短信验证依赖易盾云信服务

## 4. 环境配置

数据库配置
```
mysql.main.datasource.jdbcUrl = jdbc:mysql://10.240.192.254:3307/website?allowMultiQueries=true&useSSL=true&characterEncoding=utf8&serverTimezone=Asia/Shanghai
mysql.main.datasource.username = root
mysql.main.datasource.password =
```

域名配置（baseUrl：为nic地址，passportUrl：网易云账号地址）
```
frontend.nic.NicController.sdkVars= baseUrl:http://test.163.com:8096,passportUrl:http://test.163.com:8091

```

易盾滑块配置
```
client.common.NeteaseCaptchaClient.serverDomain= http://c.dun.163yun.com
client.common.NeteaseCaptchaClient.secretId= 96f630d6223d6969fedc4014af28ce43
client.common.NeteaseCaptchaClient.secretKey= 2fd097473ce17dcd8905e812d1137473
client.common.NeteaseCaptchaClient.captchaId= fffc9360980142aeb31603e22c0ac7f9
```

云信短信配置

```
client.common.NeteaseSMSClient.serverDomain= https://api.netease.im
client.common.NeteaseSMSClient.appKey= 0fc21f17721cdb43468383efe0aa0310
client.common.NeteaseSMSClient.appSecret= d0c68f7b4063
client.common.NeteaseSMSClient.codeLen= 6
client.common.NeteaseSMSClient.templateId= 3054042

```
 NOS配置
```
client.storage.StorageClientNos.nosDomain= https://nos.netease.com
client.storage.StorageClientNos.accessKey= 30f59cc8c286414c996760502c920b18
client.storage.StorageClientNos.secretKey= 4507267d3d1e459cbc7c22cd45e9cd75
client.storage.StorageClientNos.bucket= cloud-website-bucket-test
```


网易云账号配置
```
client.login.CloudClient.domain= http://test.163.com:8091
client.login.CloudClient.domain.product= nic
client.login.CloudClient.domain.signKey=0eedc9aea2c505a97d43432819f000d7
```

## 6. 系统运行
Pull代码，如要配置maven的settings.xml，可以：
```
cp ~/ host-nic/settings.xml ~/.m2/ 并mvn编译
```
或每次编译时使用-s settings.xml参数

编译代码：
```
mvn clean install
```
本地起程序：
```
java -jar target/host-nic-2.0.0.war
```

覆盖默认的配置项
```
-Dspring.config.location=file:///home/cloud/netease-cloud-config/nic-config/dev/application.properties
```
