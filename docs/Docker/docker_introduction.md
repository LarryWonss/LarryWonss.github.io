# 玩转Docker应用


> Docker在Coder中的普及程度，基本已经99.99%了吧，但是对于普通非docker，该怎么玩转docker呢，这就是本章节docker部分将会跟大家分享的非coder从业者该如何玩转docker。**希望Coder们可以从专业性角度轻喷，从实用性角度多给些友善的建议**

如果您有更好的docker的镜像，也欢迎您与我们一起分享。

**教程环境**

<small>注：PVE底层本来就是Debian系统，所以本教程适用于使用PVE直接作为虚拟机环境，安装Docker。我这边为了不影响底层PVE虚拟机，故使用Debian-KVM进行教程，也推荐对Debian不是太熟悉的小伙伴这么操作，防止弄崩底层PVE虚拟机</small>

本部分教程基于以下环境：

- 宿主机：**iKoolCore R1 N5100 (<small>工程样机</small>)**

- 底层虚拟机：PVE 7.2

- 虚拟环境：Debian11-KVM

  ![image.png](https://s2.loli.net/2022/09/06/gLXJ5SmxZ9EdzPQ.png)



**开始前的疑问解答**

1. 虚拟机底层用PVE好还是ESXi好？
   <br>**<small>答：</small>**PVE是开源，基于Debain系统的底层虚拟机系统；而ESXi是商业闭源的虚拟机解决方案，需要使用激活码**<small>（百度找）</small>**激活。推荐尊重知识产权，使用PVE的底层虚拟机。
   
   <hr>
   
2. PVE底层虚拟机如何安装？<br>
   **<small>答：</small>**关于如何安装，在本wiki页面的**高级玩法**板块有相关教程指导如何安装。

3. PVE系统如何设置硬件（网卡、USB、显卡等）直通？<br>
   **<small>答：</small>**硬件直通，请参考这位大佬的**[文章教程](https://never666.uk/1631/)**

   <hr>

4. 如何获取PVE下的Debian虚拟机的内网IP地址？<br>
   **<small>答：</small>**有以下两种方式获取目标debian的内网IP地址：<br>

   - 在上级路由器下查看新接入设备IP：启动Debian-KVM后，虚拟机会作为一台设备显示在上级路由器中；

   - Debian下安装`net-tools`工具，运行`ifconfig`查看本机IP地址；
     ```shell
     sudo apt-get update
     sudo apt-get upgrade
     sudo apt install net-tools
     ifconfig
     ```

     <hr>

5. Debian如何安装Docker？<br>

   **<small>答：</small>**<br>

   - 看得懂英文：请查看[官网教程](https://docs.docker.com/engine/insta ll/debian/)

   - 大白话中文**<small>（所有操作在命令行下）</small>**：

     1. ssh连接上debian虚拟机：`ssh username@192.168.x.x`;

     2. 先更新当前系统下的各个组建：`sudo apt-get update`;

     3. 安装必要的依赖库和文件：
        ```shell
        sudo apt-get install \
            ca-certificates \
            curl \
            gnupg \
            lsb-release
        ```

     4. 添加Docker官方的GPG密钥：
        ```shell
        sudo mkdir -p /etc/apt/keyrings
        curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
        ```

     5. 使用以下命令设置存储库：
        ```shell
        echo \
          "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
          $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        ```

     6. 安装docker：

        ```shell
        sudo apt-get update
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
        ```

     7. 验证安装成功，运行下面代码并看终端是否输出对应说明。
        ```shell
        sudo docker run hello-world
        ```

        



