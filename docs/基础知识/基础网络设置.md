# 1.5 基础网络设置

> 前面我们已经给软路由装好了系统，并且在1.4中，我们初步Get到了简单的网络拓扑知识。那么这里，我们通过网络设置，让我们的软路由能正常连网。

**①进入到软路由后台：**

> 按照1.4中简单拓扑图组网后，我们的手机或PC连接上Wi-Fi后即可进入到软路由后台。当然，你用PC直连软路由的LAN1（ETH0）`管理口`口，设备本地IPv4地址和软路由在同个网段后也可直接进入到软路由后台。这里**以eSir大佬**的固件为例：

1. 正常连接上Wi-Fi，电脑浏览器输入`192.168.5.1`进入到软路由系统后台：

   - 账户名：root
   - 密码：password`(固件默认密码)`<br>

   <img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129090905334.png" alt="image-20220129090905334" style="zoom:25%;" /><hr>

2. 在左侧菜单栏，前往`网络`>>>`接口`修改并配置`LAN口`和`WAN口`网络：<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129091345842.png" alt="image-20220129091345842" style="zoom:25%;" />

   - `LAN口配置：`点击LAN口对应右侧的修改，进入设置界面，在**基本设置**中，修改IPv4地址即可修改OP系统的后台登陆地址`记的修改后的网段一致性问题`；在**物理设置**中的`接口`处，需要勾选你想设置为LAN口的其他网口`通常我是只留最后一个eth作为WAN口（软路由的进水口）`<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129091922803.png" alt="image-20220129091922803" style="zoom:25%;" />
   - `WAN口配置：`在**基础设置**中设置好接入网络类型，默认是DHCP客户端（`适用于光猫拨号下`）。如果你光猫是桥接的，那么在这里需要切换协议为`PPPoE`，并输入你的宽带账号和密码，保存并应用；在**物理设置**接口处勾选我们前面设置LAN口时未勾选的最后一个eth网口，保存并应用；`WAN6口配置一致，仅需修改绑定的接口和WAN口一致`<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129092805102.png" alt="image-20220129092805102" style="zoom:25%;" /><hr>

3. 配置好LAN口和WAN口后，最好断电重启一次软路由，待机器正常重启后，即可上网。

   `至此，你的软路由已经可以正常连网了！`





