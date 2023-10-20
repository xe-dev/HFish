
#### 模板管理

该页面用于展示现有模板及其被引用情况，并且允许用户自行定制经常被重复使用或有批量修改需求的一组蜜罐服务模板。

有两种方式建立模板：通过【模板管理】页面或在【节点管理】页面。

#### 制作服务模板

在【模板管理】页面，用户可以自定义模板名称、最多10个蜜罐服务，并添加一段描述完成模板制作。

 `注意：当前每个模板最多支持10个蜜罐服务。`

<img src="https://hfish.net/images/20210616170818.png" alt="image-20210616170816548" style="zoom:50%;" />

#### 调整传输协议

用户点击上一步制作好的模板，可以对某个服务的传输协议进行调整。针对Web应用仿真、网络设备服务、安全设备服务以及IOT服务，可以根据自身业务场景和网络情况，选择其具体的传输协议（HTTP或者HTTPS），从而让蜜罐更符合当前网络结构，更好吸引攻击者视线。

<img src="https://hfish.net/images/20210812135158.png" alt="image-20210506155628363" style="zoom:50%;" />


最后，在【节点管理】页面，展开某个节点，可以通过右侧下拉菜单选择需要的模板。一个模板可以被无限的节点使用，用户修改模板时，所有引用该模板的节点蜜罐服务都会被实时更新，用户可以利用该特性批量修改节点上的蜜罐服务。