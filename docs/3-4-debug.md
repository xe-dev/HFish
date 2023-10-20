# 错误排查

### [管理端问题](https://hfish.net/#/3-4-debug?id=%E7%AE%A1%E7%90%86%E7%AB%AF%E9%97%AE%E9%A2%98)

> **管理端部署完成后，访问Web管理页面始终无法打开**

**解决办法：**

**1、确认浏览器访问地址是 https://[server]:4433/web/，注意不可缺少“/web/”这个路径**

**2、确认管理端进程的运行情况和TCP/4433端口开放情况，如果不正常需要重启管理端进程**

```
# 检查 hfish-server的进程是否运行正常
ps ax | grep ./hfish | grep -v grep
​
# 检查TCP/4433端口是否正常开放
ss -ntpl
```

**3、检查管理端主机是否开启了防火墙，导致目前无法访问，必要情况，考虑关闭防火墙**

```
 #centos7 检查防火墙状态
 systemctl status firewalld

 #centos7 检查防火墙开放端口
 firewall-cmd --list-ports
```

**4、Linux环境使用date命令确认系统时间的准确**

**5、如果以上都没有问题，请将server和client日志提供给我们**

```
节点端日志在安装目录的logs文件夹内，文件名为client.log
Linux管理端日志在/usr/share/hfish/log文件夹内，文件名为server.log
Windows管理端日志在C:\Users\Public\hfish\log文件夹内，文件名为server.log
```

### [节点问题](https://hfish.net/#/3-4-debug?id=%E8%8A%82%E7%82%B9%E9%97%AE%E9%A2%98)

> **节点状态为红色离线**

**解决办法：**

**1、检查节点到管理端的网络连通情况，以下是几种常见情况**

```
节点每60秒连接管理端的TCP/4434端口一次，180秒内连接不上即显示为离线。
刚完成部署或网络不稳定的时候会出现显示为离线。
通常情况，等待2~3分钟，如果节点恢复绿色在线，那蜜罐服务也会从绿色启用，变成绿色在线。
```

**2、如果确认网络访问正常，节点在管理端上始终离线，需要检查节点上的进程运行情况。如果进程运行异常，需要杀死全部关联进程后，重启进程，并记录错误日志。**

```
# 检查./client的进程是否运行正常
ps ax | grep -E 'services|./client' | grep -v grep        
```

**如果以上都没有问题，请将server和client日志提供给我们**

```
节点端日志在安装目录的logs目录内，文件名为client.log
Linux管理端日志在/usr/share/hfish/log文件夹内，文件名为server.log
Linux管理端日志在C:\Users\Public\hfish\log文件夹内，文件名为server.log
​
Linux节点端后台运行方案：
nohup .~/client >>nohup.out 2>&1 &
​
Linux开机自启动方案
echo 'nohup .~/client >>nohup.out 2>&1 &' >> /etc/rc.local
​
Linux定时任务方案
echo '* * * * * nohup .~/client >>nohup.out 2>&1 &' >> /var/spool/cron/crontabs/root
```

### [蜜罐服务问题](https://hfish.net/#/3-4-debug?id=%E8%9C%9C%E7%BD%90%E6%9C%8D%E5%8A%A1%E9%97%AE%E9%A2%98)

> **节点在线，部分蜜罐服务在线，部分蜜罐服务离线**

**可通过触碰状态旁边的问号，确认离线原因。**

![image-20220721111203773](http://img.threatbook.cn/hfish/image-20220721111203773.png)

**bind:address already in use解决办法：**

**该报错情况往往是因为端口冲突**

```
这个问题常见默认22端口的SSH服务，刚启动client的时候服务在线，过了一会儿后服务离线。
使用ss -ntpl命令检查该蜜罐服务的端口是否被占用？如果被占用，建议修改该业务的默认端口。
​
Windows操作系统上，如果用户启用了tcp端口监听，大概率会发现TCP 135、139、445、3389端口冲突，
这是用于Windows默认占用了这些端口，不建议在Windows上监听TCP 135、139、445、3389端口。
​
Linux操作系统端口冲突解决方案：
lsof -i:[port]
kill [pin]
重新启用该端口的蜜罐
```

> **变更服务模板后，蜜罐新服务访问不到    **

```
在HFish当前的产品结构中，管理端**永远不会**主动连接节点进行节点配置的变更。
管理端仅负责生成一个配置，等待节点每60秒尝试连接管理端拉取。
​
蜜罐服务被攻击的结果，会实时上报到管理端。
```
