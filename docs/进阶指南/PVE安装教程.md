# PVE安装教程

> 在群友的安利下，我开始折腾PVE，现在想想，主要原因有：
>
> I used to use ESXi as my server system on miniPC, and now, i am trying PVE due to: 
>
> - **PVE下可以看到CPU温度；**
>   PVE can show CPU tempemrature with a few settings
> - **网卡顺序不会乱**
>   The NICs order will not chaotic under PVE
> - **PVE基于Debian，个人会些简单的Linux命令行操作**
>   PVE is based on Debian, and i know a little Linux cammand 
>   
>   ![img](https://s2.loli.net/2022/06/02/Zzd75yoTWhkuqQg.jpg)

#### 一、制作PVE优盘启动盘

**安装PVE宿主机，其实非常简单，一句话：**

> 准备好个空白U盘，用写盘软件，将下载好的固件，刷入优盘，即可成功制作好系统启动盘。然后用制作好的启动盘插入小主机进行傻瓜化的安装操作。

**提前准备好：**

> 1. 空白优盘
> 2. 写盘软件：[**BalenaEtcher**](https://www.balena.io/etcher/) （rufus亲测失败）
> 3. 下载好PVE最新版本固件：[**PVE Proxmox Download**](https://pve.proxmox.com/wiki/Downloads)

正式开始制作启动盘。

1. 打开安装好的BalenaEtcher写盘软件；
   ![img](https://s2.loli.net/2022/06/02/mogT5OjpbRHyvAc.png)
2. 选择下载好的ISO固件；
   ![img](https://s2.loli.net/2022/06/02/HfkoZqzeTOpgXDb.png)
3. 点击Flash，等待刷写成功；
   ![img](https://s2.loli.net/2022/06/02/WJm24lSUhAdEZ6M.png)

**就是这么简单**

#### 二、安装PVE底层虚拟系统

> 制作好了启动盘，那么将键盘鼠标接好小主机，启动盘插好，开机*（工控机都是上电自启）*按F12或者Delete，开始真正的PVE安装；

1. 上电自启，**按F12或Delete**进入到安装界面；
   ![img](https://s2.loli.net/2022/06/02/GjMN4ICiOgYy53P.jpg)

2. 点击同意各种条款：
   ![img](https://s2.loli.net/2022/06/02/YuIZ5hpSxNe2R7k.jpg)

3. 选择安装到的目标磁盘，如果只有一个盘，会自动选择：
   ![img](https://s2.loli.net/2022/06/02/AFt4DIpy1VzdNkC.jpg)

4. 设置**国家、时区和键盘**布局信息：
   ![img](https://s2.loli.net/2022/06/02/JIyAEUDv7qK9gXd.jpg)

5. 设置PVE后台的**登录密码**（切记记住，否则进不去后台）*以及**邮箱***（邮箱是必填项）：
   ![img](https://s2.loli.net/2022/06/02/p5lhiK4oLjDYW1S.jpg)

6. 设置PVE后台地址等信息：
   ![img](https://s2.loli.net/2022/06/02/XENcSY6v3gJt4bm.jpg)
   ***这里的信息非常重要，建议完全按照我这里进行设置，除非你自己熟悉IP、网关、DNS等方面的网络知识。***

   - Management Interface: 管理网口，建议选择第一个网口
     ![img](https://s2.loli.net/2022/06/02/lUGD5A64QVM9NzK.jpg)

   - hostname: 根据你自己的想法填写，记住得是域名格式；
   - IP Address：是进入到PVE的后台地址；
   - Gateway：网关，这里我设置为上级路由器的网关；
   - DNS：同为上级的路由器

7. 设置完后，进行安装。安装完毕，系统会自动重启并进入Shell界面。

   ![img](https://s2.loli.net/2022/06/02/6ZpKkPeyu29WcS5.jpg)

**至此，PVE底层虚拟机系统就安装成功了！**







