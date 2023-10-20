#### HFish设计理念

HFish是一款社区型免费蜜罐，侧重企业安全场景，从内网失陷检测、外网威胁感知、威胁情报生产三个场景出发，为用户提供可独立操作且实用的功能，通过安全、敏捷、可靠的中低交互蜜罐增加用户在失陷感知和威胁情报领域的能力。

HFish具有超过40种蜜罐环境、提供免费的云蜜网、可高度自定义的蜜饵能力、一键部署、跨平台多架构、国产操作系统和CPU支持、极低的性能要求、邮件/syslog/webhook/企业微信/钉钉/飞书告警等多项特性，帮助用户降低运维成本，提升运营效率。



#### 为什么选择HFish

- **免费、简单、安全的蜜罐产品**
	
    蜜罐通常被定义为具有轻量级检测能力、低误报率的检测产品，同时它也是企业生产本地威胁情报的优质来源之一。HFish可以帮助中小型企业用户在日常安全运营中进行避免告警洪水、低成本的增加威胁感知和情报生产能力。目前，社区的力量正在不断帮助HFish完善自身，共同探索欺骗防御的最佳实践。

- **安全、敏捷的威胁感知节点**
	
    HFish被广泛应用于感知办公内网、生产环境、云内网及其他环境失陷主机横向移动、员工账号外泄、扫描和探测行为、私有情报生产甚至内部演练和安全意识培训，HFish的多种告警输出形式与态感、NDR、XDR或日志平台结合，极大拓展检测视野。



#### HFish架构

HFish采用B/S架构，系统由管理端和节点端组成，管理端用来生成和管理节点端，并接收、分析和展示节点端回传的数据，节点端接受管理端的控制并负责构建蜜罐服务。

在HFish中，**管理端**只用于**数据的分析和展示**，**节点端**进行**虚拟蜜罐**，最后由**蜜罐来承受攻击**。

<img src="https://hfish.net/images/image-20210902163914134.png" alt="image-20210902163914134" style="zoom:50%;" />

在最小化测试的情况，您可以直接通过安装管理端，通过管理端内的内置节点，直接进行蜜罐服务测试。

[linux下载](https://hfish.net/#/2-2-linux)

[windows下载](https://hfish.net/#/2-3-windows)

[docker下载](https://hfish.net/#/2-1-docker)

如果有企业下载需求，您也可以前往[HFish文档区域](https://hfish.net/#/docs)下载部署文档方案。



#### 我们的故事

2019年的8月7日，我们发布了自己的第一款开源蜜罐HFish，在之后的16个月里，HFish在Github上获得2.6k个star，在Gitee上成为安全类目TOP5的GVP项目。 

2021年2月9日，融合社区反馈和过去2年的思考，我们开启了全新概念的威胁捕捉和诱骗系统HFish V2版本，并宣布采用闭源共享方式向所有用户免费授权使用。



#### 联系我们


![image-20220729162931543](http://img.threatbook.cn/hfish/image-20220729162931543.png)



##### HFish是北京微步在线科技有限公司旗下产品

```
联系地址：北京市海淀区苏州街49号盈智大厦4层
联系电话：400-030-1051
```
