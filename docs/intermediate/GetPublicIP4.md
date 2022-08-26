# 2.1 获取公网IP

> 什么是公网IP？其实我们大部分用户使用的均是大局域网内网网段，大部分情况下，我们所在的小区内仅有几个动态公网IP。

`公网IP != 固定IP`



- **获取公网IP的方式：**

  - 已安装宽带用户：致电给宽带客服咨询。可用策略：`家庭内在装网络监控，安装师傅说要申请公网IP`、

  - 正安装宽带用户：让宽带安装师傅设置光猫桥接，并将宽带账号和密码告知你。`宽带桥接用户较大概率是公网IP`

    <hr>

- **关于公网IP，你需要了解或知悉：**

  1. 现在运营商已经基本不会主动给用户开放IPv4公网地址；
  2. 公网IP每24-72小时`通常48小时`变更一次；
  3. 移动宽带`⚠️大内网`基本拿不到公网iP；
  4. 电信宽带较大概率可申请到公网IP，实际看所在地区；
  5. 联通宽带光猫改桥接后（`亲测获得公网IP`）较大概率是公网IP；
  
- 宽带改桥接：

  > 光猫改桥接是为了让光猫就做光信号转电信号的功能，拨号和DHCP功能由后面的软路由实现，这样你可以实现对内网各种内网服务的转发到公网。
  
  - 条件：可以进入到光猫**超管后台**，以下是网友整理的各地的运营商光猫超管后台信息。
  
  - 超管后台账号密码获取：
  
    - 找装维师傅要；
    - 根据自己光猫的型号和地区，充分利用互联网引擎，自行搜索
  
  - 各位光猫的认证方式收集（by 网友)：
  
    > 有些大佬，在考虑使用猫棒加光纤收发器，实现完美替代光猫，并突破到2.5G下行。
  
    [![](https://secneti.oss-cn-shenzhen.aliyuncs.com/%E7%8C%AB%E6%A3%92%E5%A5%97%E8%A3%85.png)](https://item.taobao.com/item.htm?ft=t&id=680839912925)
  
    各地区的光猫光猫认证方式和超管后台信息收集如下：
  
    <hr>
  
    - 北京联通（小明）：
  
      - 认证方式 —— MAC
  
      - VLAN ID —— INTERNET 3961 / OTHER 3962 / IPTV 3964
  
        <hr>
  
    - 天津电信（一袋大酱）：
  
      - 认证方式 —— LOID
  
      - VLAN ID —— IPTV 3003 / INTERNET 105 / 其他 46
  
      - 后台地址 —— http://192.168.1.1:8080/cgi-bin/login.htm.cgi
  
      - 账号 —— telecomadmin
  
      - 密码 —— nE7jA%5m
  
        <hr>
  
    - 温州移动（蛤QAQ）：
  
      - 认证方式 —— Password 码认证下发业务
  
      - VLAN ID —— TR069 4034 / INTETNAT 4031
  
        <hr>
  
    - 辽宁联通（春麟_Techscl）：
  
      - 认证方式 —— LOID
  
      - VLAN ID —— Internet：2001
  
        <hr>
  
    - 辽宁移动（泫凝）：
  
      - 认证方式 —— LOID&密码+SN认证
  
      - VLAN ID —— INTERNET 1340/IPTV 4017/TR069 4011
  
        <hr>
  
    - 江苏移动（化性而起伪）：
  
      - 认证方式 —— Password下发和SN码双认证
  
      - VLAN ID —— TR069 4015/INTERNET 48/OTHER 2030(IPTV)/VOIP 3951(电话)
  
        <hr>
  
    - 海南电信（华GKjl）：
  
      - 认证方式 —— LOID 及密码（宽带账号&八位数字密码）
  
      - VLAN ID —— INTERNET 41 / OTHER 43 / TR06R 46
  
      - 后台地址 —— http://192.168.1.1
  
      - 账号 —— telecomadmin
  
      - 密码 —— telecomadminXXXXXXXX (X八位动态数字重启会变更)
  
        <hr>
  
    - 浙江丽水电信（Uing07）：
  
      - 认证方式 —— LOID
  
      - VLAN ID —— internet 41/IPTV 43
  
        <hr>
  
    - 贵州贵阳电信（Johnson_Y）：
  
      - 认证方式 —— LOID
  
      - VLAN ID —— 3701
  
      - 后台地址 —— http://192.168.1.1
  
      - 账号 —— telecomadmin
  
      - 密码 —— nE7jA%5m
  
        <hr>
  
    - 滁州电信（160512）：
  
      - 认证方式 —— LOID
  
      - VLAN ID —— IPTV 43 / INTERNET 41
  
      - 后台地址 —— http://192.168.1.1:8080/login.html
  
      - 账号 —— telecomadmin
  
      - 密码 —— nE7jA%5m
  
        <hr>
  
    - 深圳电信（编程乐园）：
  
      - 认证方式 —— LOID
  
      - VLAN ID —— IPTV 45 / INTERNET 41 / TR069 46
  
      - 后台地址 —— http://192.168.1.1
  
      - 账号 —— telecomadmin
  
      - 密码 —— nE7jA%5m
  
        <hr>
  
    - 深圳联通（isJackeroo）：
  
      - 认证方式 —— LOID
  
      - VLAN ID —— IPTV 46 / INTERNET 41 
  
      - 后台地址 —— http://192.168.1.1
  
      - 账号 —— 管理员账户（默认admin）
  
      - 密码 —— cuadmin00259e
  
        <hr>



