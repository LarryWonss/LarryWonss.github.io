# 写在前面

> Docker在Coder中的普及程度，基本已经99.99%了吧，但是对于普通非docker，该怎么玩转docker呢，这就是本章节docker部分将会跟大家分享的非coder从业者该如何玩转docker。**希望Coder们可以从专业性角度轻喷，从实用性角度多给些友善的建议**

如果您有更好的docker的镜像，也欢迎您与我们一起分享。

<center><b>测试环境</b></center>

<small>注：PVE底层本来就是Debian系统，所以本教程适用于使用PVE直接作为虚拟机环境，安装Docker。我这边为了不影响底层PVE虚拟机，故使用Debian-KVM进行教程，也推荐对Debian不是太熟悉的小伙伴这么操作，防止弄崩底层PVE虚拟机</small>

本部分教程基于以下环境：

- 宿主机：**iKoolCore R1 N5100 (<small>工程样机</small>)**

- 底层虚拟机：PVE 7.2

- 虚拟环境：Debian11-KVM

  ![image.png](https://s2.loli.net/2022/09/06/gLXJ5SmxZ9EdzPQ.png)
  