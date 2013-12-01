MicroTimer
==========

一个支持秒级定时的微型定时器


为什么需要？
===========
目前cron 只能定时到分钟。 但是我们很多场合需要，秒级，毫秒级的定时功能。例如, 加粉的调度轮询，每个5秒一次。另外普通的cron，hudson对开发集成不是很方便。例如定时的调用，dubbo API等。

在Java里面的Timer方法虽然能实现高精度定时，但是配置很麻烦。例如需要实现，18点到第2天9点，每隔5分钟执行一个抓取数据的任务，
怎么用Java的Timer定时呢？

配置文件：

```
#兼容传统cron，每5分钟调用一次
*/5 * * * *   ---http://xxxx

#扩展秒级别实现，每5秒调用一次
* * * * * */5  ---taodian_api://xxxx

#支持毫秒级定时，每0.1秒执行一次
* * * * * * */100  ---shell://xxxx

```

基本功能：
=========
+  从配置文件读取配置。
+  有web GUI 可以查看运行状态。
+  支持作为library 调用
+  支持扩展schema

```java

new MicroTimer("* * * * * * */100", new Runnable(){
  public void run(){
    //do some thing per 0.1s
  }
});

```

sssssss

