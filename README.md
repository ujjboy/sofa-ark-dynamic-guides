# 快速开始

本示例基于 SOFABoot 3.4.8 & Ark 1.1.6。

由于 SOFABoot 3.2.0 之后有 API 变更，原来的 runtime-sofa-boot-plugin 已经无法直接使用，通过自定义 Ark plugin 屏蔽

1、clone 当前代码

`git clone https://github.com/ujjboy/sofa-ark-dynamic-guides.git`

2、打包（含打包 facade、ark-plugin、ark-biz）

`mvn clean install -DskipTests` 

3、启动宿主应用

`java -jar target/ark-dynamic-master-1.0.0-ark-executable.jar`

4、验证宿主 rest 请求

`curl http://localhost:8088/api/master` 

期望返回： 
> THIS IS DEFAULT PROVIDER

5、安装模块

biz -i file://biz -i file:///${your-path}/sofa-ark-dynamic-guides/target/ark-dynamic-module-1.0.0-ark-biz.jar

```shell
$ telnet localhost 1234

sofa-ark>biz -a
ark-dynamic-master:1.0.0:activated
biz count = 1

sofa-ark>biz -i file:///Users/zhanggeng/workspace/github.com/sofastack-guides/sofa-ark-dynamic-guides/target/ark-dynamic-module-1.0.0-ark-biz.jar
Start to process install command now, pls wait and check.

sofa-ark>biz -a
ark-dynamic-master:1.0.0:activated
ark-dynamic-module:1.0.0:activated
biz count = 2
```

通过 biz -a 查看，如果两个模块都是 activited 状态，则继续

6、验证基座 rest 请求

`curl http://localhost:8088/api/master`  

期望返回：
> THIS IS MODULE PROVIDER

