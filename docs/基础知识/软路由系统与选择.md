# 1.2 软路由系统与选择

> 这里将会简单介绍软路由的系统有哪些，以及如何选择适合自己的软路由系统



##### 1、软路由系统有哪些？

> 软路由系统其实非常多，国内用户大部分可能只接触过**OpenWrt**和**iKuai**。软路由底层系统是Linux，基于Linux，结合各个细分市场需求，国外主流的路由系统还有Pfsense、OPNsense、RouterOS等。

<hr>

![Protectli Vault - tested software](https://protectli.com/wp-content/uploads/2020/07/logo_wall3-1.png)

###### 1.1 OpenWrt：

> 以下定义来源于维基百科。

**OpenWrt**是适合于[嵌入式](https://zh.wikipedia.org/wiki/嵌入式)设备的一个[Linux](https://zh.wikipedia.org/wiki/Linux)发行版。

相对原厂固件而言，OpenWrt不是一个单一、静态的[固件](https://zh.wikipedia.org/wiki/固件)，而是提供了一个可添加软件包的可写的[文件系统](https://zh.wikipedia.org/wiki/文件系统)。这使使用者可以自由的选择应用程序和配置，而不必受设备提供商的限制，并且可以使用一些适合某方面应用的软件包来定制你的设备。对于开发者来说，OpenWrt是一个框架，開發者不必麻烦地构建整个固件就能得到想要的[应用程序](https://zh.wikipedia.org/wiki/应用程序)；对于使用者来说，这意味着完全定制的能力，與以往不同的方式使用设备，OPKG包含超过3500个软件。 默认使用LuCI作为web交互界面。

OpenWrt另有一个复刻分支项目，名为[LEDE](https://zh.wikipedia.org/wiki/LEDE)，两者于2018年1月合并，合并后的项目使用OpenWrt的名字、LEDE的源代码。

<hr>

###### 1.2 iKuai

[爱快（iKuai）](https://www.ikuai8.com/)是一家商业场景网络解决方案提供商，具备X86架构大场景方案，也有ARM架构小场景WiFi方案，拥有DPI七层流控、AP主动探测技术。iKuaiOS是爱快公司开发并深度定制的流控功能强大的商用级路由系统。其具有以下特点：

1. 智能流控功能；
2. 流量数据可视化功能；
3. AC智能管理；
4. 强大的行为管控；

<hr>

###### 1.3 Pfsense：

> 以下解释来源于[维基百科](https://zh.wikipedia.org/wiki/PfSense)

**pfSense**是一个基於[FreeBSD](https://zh.wikipedia.org/wiki/FreeBSD)的[開源](https://zh.wikipedia.org/wiki/開放原始碼)[防火墙](https://zh.wikipedia.org/wiki/防火墙)及[路由](https://zh.wikipedia.org/wiki/住宅网关)平台（即作業系統）。

pfSense可安裝於實體電腦或[虚拟机](https://zh.wikipedia.org/wiki/虚拟机)，能夠在網絡中充當獨立的防火牆及[路由器](https://zh.wikipedia.org/wiki/路由器)。其配備用於進行設置及更新等管理工作的[Web](https://zh.wikipedia.org/wiki/Web)[用戶界面](https://zh.wikipedia.org/wiki/用戶界面)，因而易用性較高。

<hr>

###### 1.4 OPNsense

> 以下解释来源于[维基百科](https://zh.wikipedia.org/wiki/OPNsense)

**OPNsense** 是由 Deciso 开发的开源、基于 [FreeBSD](https://zh.wikipedia.org/wiki/FreeBSD) 的[防火墙](https://zh.wikipedia.org/wiki/防火墙)和路由软件，Deciso 是一家位于荷兰的公司，为 OPNsense 生产硬件并销售支持包。它是 [pfSense](https://zh.wikipedia.org/wiki/PfSense) 的一个分支，而 pfSense 又是从构建在 [FreeBSD](https://zh.wikipedia.org/wiki/FreeBSD) 上的 [m0n0wall](https://zh.wikipedia.org/wiki/M0n0wall) 派生出来的。[[3\]](https://zh.wikipedia.org/wiki/OPNsense#cite_note-InfoOPN-3)它于 2015 年 1 月推出。[[2\]](https://zh.wikipedia.org/wiki/OPNsense#cite_note-LaunchPR-2)当 m0n0wall 在 2015 年 2 月关闭时，它的创建者 Manuel Kaspar 将其开发者社区推荐给 OPNsense。[[4\]](https://zh.wikipedia.org/wiki/OPNsense#cite_note-4)

OPNsense 有一个基于 web 的界面，可以在 [i386](https://zh.wikipedia.org/wiki/I386) 和 [x86-64](https://zh.wikipedia.org/wiki/X86-64) 平台上使用。[[5\]](https://zh.wikipedia.org/wiki/OPNsense#cite_note-5)除了充当防火墙之外，它还具有流量整形、[负载均衡](https://zh.wikipedia.org/wiki/负载均衡)和[虚拟专用网](https://zh.wikipedia.org/wiki/虚拟专用网)功能，其他功能可以通过插件添加。[[6\]](https://zh.wikipedia.org/wiki/OPNsense#cite_note-TechROPN-6)

2017 年 11 月，[世界知识产权组织](https://zh.wikipedia.org/wiki/世界知识产权组织)的一个小组发现，pfSense 的版权所有人 Netgate 一直在恶意使用 opnsense.com 域名诋毁 OPNsense，Netgate 有义务将该域名转让给 Deciso。Netgate 一方试图援引[合理使用](https://zh.wikipedia.org/wiki/合理使用)条款，声称该域名“已被用于一个拙劣模仿网站”；它被拒绝的理由是[言论自由](https://zh.wikipedia.org/wiki/言论自由)不包括域名注册。

<hr>

###### 1.5 RouterOS

[RouterOS](https://mikrotik.com/software)是RouterBOARD的操作系统。它还可以安装在 PC 上，并将其变成具有所有必要功能的路由器 - 路由、防火墙、带宽管理、无线接入点、回程链路、热点网关、VPN 服务器等。

<hr>

###### 1.6 Panabit

[Panabit](https://www.panabit.com/)：北京派网软件有限公司是业内领先的从网络接入、流量分析、应用提速、带宽优化到七层要素审计的解决方案供应商。基于广受好评的网络应用识别优化引擎以及业界领先的操作系统，自主研发有Panabit 智能应用网关、Panalog 大数据日志分析平台、iXCache 互联网智能应用缓存、下一代负载均衡、SD-WAN 应用加速网关等解决方案，致力于提高网络经营中应用可视化、成本调优、行为管理和审计等能力，为用户提供高效、稳定、开放的应用层网络通信平台、产品和服务。  以自建产品生态圈的互联网模式，持续多年保持业内较快的特征库更新速度、极高的应用协议识别率，而这两点正是所有网络运营场景中流量管控、网络调优、大数据分析、日志审计的必备基础。

<hr>

<hr>

##### 2、我该选择哪个软路由系统？

1. **决策依据：**从你的实际使用需求出发，挑选适合自己的路由系统。
2. **国内主流：**
   - iKuai：适用于小型商业场景，比如商超、公共场合Wi-Fi、出租屋等对于流量和设备控制需求比较强的使用场景；
   - OpenWrt：适用于对插件依赖度比较高，爱折腾的家用消费者群体，**本Wiki也主要围绕OpenWrt的实际使用展开。**

