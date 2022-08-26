# 2.2.1 DDNS实现外网访问

#### 前言

> 很多有Geek属性的家宽用户、工作室或小公司，可能会有远程管理家里、工作室或者公司的宽带网络，实时监控并处理一些事情，目前这个在国内还是比较难实现的，是有一些必要条件的。所以本篇教程必须有**公网IP**才能进行。本篇教程以eSir大佬编译的2021年2月份的固件为例进行。**固件版本为OpenWrt R21.1.18 GDQ v2.1[2021] Compiled by eSir / LuCI Master (git-20.343.54716-6fc079f)**，这个固件本身是没有带有阿里云ddns插件的。如果你使用的固件和我的不一样，且你的固件中也没有阿里云DDNS插件，可参考本教程操作。



#### 一、安装依赖包

> 阿里云DDNS插件需要有以下依赖包，请在`系统`-->>>`软件包`中**检查并确认**：
>
> - ddns-scripts
> - Luci-app-ddns
> - Openssl-util
> - wget
>
> 如果以上依赖包在你的OpenWrt系统中不存在，请操作安装。**「无法下载安装的话，请考虑并从网络问题入手解决」**

以上插件的安装更新方式如下

`系统`->>>`软件包`->>>`过滤器`->>>`搜索并安装`以上列表中的依赖包<img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920185857955.png" alt="image-20210920185857955" style="zoom:33%;" />





#### 二、安装阿里云DDNS插件

1. 插件下载；
   - **下载地址：[Github](https://github.com/LarryWonss/assets_for_openwrt/blob/main/luci-app-aliddns_0.1.1-1_all.ipk)    |  [Google Drive](https://drive.google.com/file/d/1GmVMyD--cB8IVp364Kb3DOK5k5KkOM_k/view?usp=sharing)**

2. 插件安装：插件为ipk格式，在`系统`->>>`文件传输`中，上传并安装上传的ipk文件<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920192423970.png" alt="image-20210920192423970" style="zoom:30%;" />

3. 检查并确认在`服务`下面存在`阿里云DDNS`服务；<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920192533521.png" alt="image-20210920192533521" style="zoom:30%;" />

#### 三、设置阿里云DDNS

1. 登录阿里云后台，购买一个域名**「阿里云购买域名步骤略」**；
2. 获取AccessKey ID和AccessKey Secrect;
   - 登陆阿里云后，点击右上角`控制台`；<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920193318913.png" alt="image-20210920193318913" style="zoom:30%;" />
   - 在`控制台`后台，点击右上角头像，找到AccessKey管理;<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920193300099.png" alt="image-20210920193300099" style="zoom:30%;" />
3. 按照以下截图中设置<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920193831996.png" alt="image-20210920193831996" style="zoom:40%;" />

4. 保存并应用；

 



#### 四、设置端口转发

1. 在`网络`->>>`防火墙`中设置端口转发：<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920194029055.png" alt="image-20210920194029055" style="zoom:32%;" />

2. 端口转发设置：

   - 名称：可定义
   - 传输协议：建议TCP+UDP
   - 外部区域：默认wan
   - 外部端口：端口号设置，就是我们域名后面加的端口号，在这里设置，可自定义，范围0~65535，请避开443、80、22等常用的且部分运营商会封禁的端口；
   - 内部IP地址：选择软路由后台的登陆地址；
   - 内部端口：80

   下图是我这边设置的，仅供参考。<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920201354979.png" alt="image-20210920201354979" style="zoom:38%;" />

##### 五、最重要步骤：

**请到`系统`**->>>`Web管理`中，勾选掉`只允许内网访问`(不勾选掉无法远程登录)<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920194654064.png" alt="image-20210920194654064" style="zoom:33%;" /><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210920201450569.png" alt="image-20210920201450569" style="zoom:37%;" /><br>



**本教程完，㊗️折腾愉快**

(如果设置完无法通过域名+端口号访问，请耐心等待，不同域名提供商需要的解析时间不一样，我们后台设置的10，是10分钟的意思。如果时间很长了还访问不了，**请确认你拥有公网IP**)