# ESXI虚拟机的安装以及在虚拟机中安装OpenWrt

>继物理直装OpenWrt教程，很多小伙伴在评论里面说“这么好的配置只装OpenWrt软路由系统，有点奢侈浪费”，那么本篇就来了。本篇将会就如何安装虚拟机Esxi系统，以及在虚拟机上安装OpenWrt系统，详细记录，希望对刚入软路由的小伙伴有所帮助。（*当然，对于各位高级技术党们，可能本篇有点过于基础，请忽略*）

##### 一、软件工具的准备：

1. 虚拟机ISO安装包：**[点击直达官网](https://my.vmware.com/cn/group/vmware/downloads/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0)**
   - 注册并登录Vmware官网网站
   - 进入**[VMware vSphere下载页面](https://my.vmware.com/cn/group/vmware/downloads/info/slug/datacenter_cloud_infrastructure/vmware_vsphere/7_0)**![Vmware vSphere](https://i.loli.net/2020/08/02/i5e1WdKbAR3tqGu.png)

   - 选择需要下载的版本，并跳转至**[下载页面](https://my.vmware.com/cn/group/vmware/downloads/details?downloadGroup=ESXI67U3B&productId=742&rPId=48558&download=true&fileId=153ea9de288d1cc2518e747f3806f929&uuId=9e3b8069-f8ff-4855-8045-c47ebba21e7b)**![Vmware vSphere下载](https://i.loli.net/2020/08/02/3IFDBieJ8gCc2y1.png)

2. OpenWrt固件包：*随性挑选，不做推荐。百度一下，可以获得超多推荐*
3. 固件格式转换软件：**[StarWindConverter](https://www.starwindsoftware.com/starwind-v2v-converter)**
4. U盘启动盘制作工具：推荐rufus，**[点击直达官网下载](https://rufus.ie/)**





##### 二、虚拟机系统安装介质（U盘）的制作和固件格式转换

1. 使用rufus写盘：![虚拟机系统盘已经制作好](https://i.loli.net/2020/08/02/qrmzAbj2M9QHd4a.png)

2. OpenWrt固件格式转换

>通常情况下，我们下载的固件都仅适合物理装机，这个时候就需要借助这个**[StarWindConverter](https://www.starwindsoftware.com/starwind-v2v-converter)**来完成固件的格式转化。
>
> - 下载并安装好格式转化工具：**[点击直达]()**  *密码：*
> - 执行转化操作：![StaWind固件转换工具](https://i.loli.net/2020/08/02/WdI3FK61MzR4VXc.png)
>   ![选择VMWare ESX..](https://i.loli.net/2020/08/02/ZTEnNXqUfcpQvjS.png)
>   **转化完成后，会得到两个文件，一个是-flat.vmdk大文件和另外一个.vmdk的较小的文件，咱们先保存好，后续待用**



#### 三、Esxi虚拟机系统的安装

1. 第一步，还是插，插好键鼠，链接好显示器，设置好BIOS启动项

2. 上电进入自动&傻瓜化问答安装界面![虚拟机系统安装](https://i.loli.net/2020/08/02/VQACl2E9IpTwySm.jpg)
   **设置好密码**
   ![设置好密码](https://i.loli.net/2020/08/02/BPX7jhLbgsGUeDA.jpg)

   **安装成功**![虚拟机安装成功](https://i.loli.net/2020/08/02/TJnAlzB7WIugb1f.jpg)

3. 断电重启，进入安装成功的虚拟机界面，如下图：

4. 接下来就可以使用网线连接软路由的LAN1口，激活并设置ESXI虚拟机系统了。（**屏幕上会显示IPV4后台管理地址，密码是前面设置的密码，登录名为root，强烈建议设置固定的IPV4地址，防止重启后地址更换。连不上ESXI后台**）![成功安装](https://i.loli.net/2020/08/02/fFHykozGrVN7WCB.jpg)
   ![重设后台ipv4地址](https://i.loli.net/2020/08/02/UEIP4CN3goDKT5O.jpg)

**使用网线连接软路由的LAN1口和电脑，电脑浏览器输入ipv4地址即可出现如下登录界面：**
![使用前面设置的密码登录后台](https://i.loli.net/2020/08/02/FSZNHP5Ibo4qLgG.png)
**后台登录成功，请自行百度激活**
![后台登录成功](https://i.loli.net/2020/08/02/RdT7XfJ6lvAyh1q.png)





#### 四、虚拟机上安装OpenWrt + 网卡直通——*重头戏*

>上面我们已经进入到ESXI虚拟机后台了，那么接下来我将教大家如何设置网卡直通已经安装OpenWrt系统

1. 先设置好网卡直通：
   - 首先在左侧的导航栏中心点击```管理```按钮，然后进入到```硬件—PCI设备中```
   - 点击快速筛选器，把```支持直通```的设备筛选出来；
   - 选择2-6，然后```切换直通```，如上图所示。（**不选择1是因为需要把1口作为管理口，如果不留1作为管理口，后续就连不上ESXI后台了，又是一个坑**）
   - 切换直通后，点击重新引导主机，系统将重启；
   - 重新登录虚拟机后台后，进入**网络-虚拟交换机**，右键```vSwitch0```,打开安全下拉选项，把``混杂模式``勾选为``接受``![网络-虚拟交换机](https://i.loli.net/2020/08/02/6aeXk3Z8FgvKOI4.png)
     ![混杂模式-接受](https://i.loli.net/2020/08/02/vZbdMXlruUCjcF8.png)
     **至此，网卡就直通好了**

2. 新建虚拟机
   - 输入名称LEDE选择兼容性```ESXi 6.7虚拟机```，客户机操作系统系列```Linux```，客户机操作系统版本其他```2.6x Linux(64位)```![新建虚拟机](https://i.loli.net/2020/08/02/Yhb3ytvSzxgJqN7.png)
   - 选择默认存储，然后到达自定义设置：删掉原来的```硬盘1```，设置```USB控制器```为```USB3.0```，添加```硬盘```，并上传固件:
     - 添加硬盘，现有硬盘：![自定义配置1](https://i.loli.net/2020/08/02/b7TO4H61c9DmhMX.png)
       ![新建硬盘](https://i.loli.net/2020/08/02/frEglYWSXNKsPQu.png)
     - 创建目录OpenWrt,然后上载前面转换好格式的固件（**先上传小的，后上传大的，最后上传完了，只会显示一个**）![上传固件](https://i.loli.net/2020/08/02/lsjpTNGvMm6IZJE.png)

   - 接着，```添加其他设备-PCI设备```，并保存（一共添加5个，因为我们直通了5个网卡,要注意顺序）：![勾选直通的网卡](https://i.loli.net/2020/08/02/gNDnIkZUpJvS9Ft.png)

   - 最后别忘记了，设置虚拟机自启![设置虚拟机自启](https://i.loli.net/2020/08/02/vCuURwMbAlf4zda.jpg)



**至此，所有设置已经完成，可以点击虚拟机，启动了**

#### 五、登录软路由后台，设置网络
>和物理直装的OpenWrt一样设置，该部分内容略。

![WechatIMG115](https://i.loli.net/2020/08/02/dczHGpVTwUmaDxN.png)
**最后，祝各位，折腾愉快**