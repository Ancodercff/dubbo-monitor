# Dubbo Monitor

## 项目介绍

![Dubbo monitor screenshot](https://github.com/handuyishe/dubbo-monitor/wiki/images/screenshot.png)

Dubbo Monitor是针对Dubbo开发的监控系统，基于dubbo-monitor-simple改进而成，可以理解为其演化版本。该系统用数据库记录日志的方式替代了dubbo-monitor-simple写文件的方式。

> PS: 项目目前依赖的是dubbo的2.5.4开发版本。

## 升级日志

>### 2015-07-08
>
> 1. 修复依赖

## Dubbo Monitor使用帮助

### Dubbo-Monitor配置介绍

**第一步**：创建数据库
首先创建名称为monitor数据库，编码格式UTF-8。然后将项目sql文件夹下面的create.sql导入到数据库，生成dubbo_invoke表代表成功导入。

**第二步**：编辑项目中application.properties，配置如下：

```
####Dubbo Settings
dubbo.application.name=dubbo-monitor
dubbo.application.owner=handu.com
dubbo.registry.address=zookeeper://127.0.0.1:2181
dubbo.protocol.port=6060

####Database Settings
db.url=jdbc:mysql://<database_host>:<database_port>/monitor?prepStmtCacheSize=517&cachePrepStmts=true&autoReconnect=true&characterEncoding=utf-8
db.username=root
db.password=root
db.maxActive=500
```

**第三步**：打包运行项目
执行maven命令：mvn clean package
target文件夹下生成的dubbo-monitor.war即为项目部署文件，将其放置到对应服务器目录下，启动服务器即可。例如：tomcat的webapps文件夹下。

**第四步**：访问项目
启动web服务器后，访问地址：http://IP:[port]/dubbo-moniotor

## 服务提供端配置

[Dubbo服务提供端监控配置](http://dubbo.io/User+Guide-zh.htm#UserGuide-zh-%3Cdubbo%3Amonitor%2F%3E)

## TODO List

- [ ] 将MySQL修改为Mongodb
- [ ] 细化应用间的调用依赖，展示更为直观的应用依赖图