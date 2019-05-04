<div align=center><img src=images/logo.png width=30% ></div>

# Mars

Mars(战神),对之前的WDScanner的全新重写，结合Tide资产探测和指纹识别方面的技术积累，为客户提供更高效智能的安全检测和安全监测服务。

平台使用了flask+vali-admin做为前端，python作为后台扫描脚本，使用了分布式的节点扫描模式，可以对资产探测、POC检测、漏洞扫描等任务分多个节点来完成。


```
tips:只是有个了大体框架，很多功能才刚刚开始~~

```

# Change Log

- [2019-02-22] 完成部分核心功能
- [2019-01-15] 规划整体架构
 
# Abstract

功能规划：客户管理、资产管理、敏感信息检测、Github监控、主动扫描、被动扫描、POC检测、端口监测等等。


# Function

## 登录界面
直接使用的vali-admin内置的一个lockscreen页面，改了个比较灰主流的背景，原谅我的审美。

![pic](images/pic1.jpg)

## 用户管理
添加用户和管理用户：设置用户联系人、手机、邮箱等，可以进行漏洞预警，设置服务周期和服务类型，比如定期的漏洞扫描、POC检测、弱口令检测、敏感字检测等。

![pic](images/pic2.jpg)


## 资产管理
资产管理是整个平台最基础也算最核心的功能，对资产进行POC检测或者弱口令检测，首先依赖于资产能被发现、指纹能被识别。

比如通过资产探测发现某服务器使用了iis，那么系统会自动调用IIS短文件名检测POC、IIS PUT检测POC进行自动检测，如果发现使用了weblogic会把weblogic的所有反序列化漏洞POC都检测一遍，如果发现系统使用了Mysql，会自动调用mysql弱口令检测程序进行弱口令测试，等等。这些能自动检测的前提就是能发现资产指纹信息，目前我们也在搭建自己的指纹识别平台，后续可能会考虑放出来给大家使用。

添加资产时，平台会根据资产类型进行智能分类，比如你添加了test.gauzi.com和app.gauzi.com和www.maodou.com作为资产，平台会把该任务分为两个具体任务，一个是guazi.com，里面包括两个资产test.gauzi.com和app.gauzi.com，另一个是maodou.com，里面包括www.maodou.com作为资产。

之后后台会自动进行子域名枚举，子域名枚举共使用了四种方式以保证子域名枚举的全面，并把这些子域名都作为该资产任务下的具体资产。

之后会对这些子域名进行探测信息，可以根据策略配置扫描全端口还是部分端口，而且在分析过程中如果发现子域名对应的ip集中在某个C段，那么平台会自动把该C段IP也作为资产任务进行扫描探测，并写入数据库进行呈现。

![pic](images/pic3.jpg)

![pic](images/pic4.jpg)

![pic](images/pic5.jpg)


# ToDo

- 尽量完善各种功能，早日面世




# 和我联系

**和我联系：**

<div align=center><img src=images/zjwf.png width=30% ></div>