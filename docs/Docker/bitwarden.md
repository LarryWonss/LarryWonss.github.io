 # bitwarden - 密码管理神器 

> 丰富多彩的互联网生活，各种网站都需要注册账号，为了信息安全，我们可能会设置各不相同的密码，纯靠人记住这些密码是基本不现实的，那么这个时候就需要借助诸如1Password, Bitwarden等类似的密码管理工具。这里我们来分享一种使用docker部署bitwarden进行密码管理的方法。

[![](https://img.shields.io/badge/Vaultwarden-Dockerhub-blue)](https://hub.docker.com/r/vaultwarden/server) <br>

[![](https://img.shields.io/badge/Vaultwarden-Github-blue)](https://github.com/dani-garcia/vaultwarden) <br>

[![](https://img.shields.io/badge/Vaultwarden-Wiki-red)](https://github.com/dani-garcia/vaultwarden/wiki)



**安装Bitwarden服务**

> <small><b>默认：所有操作均为ssh到Debian-KVM下操作，这里我们使用第三方的Vaultwarden镜像进行演示</b></small>.

1. ssh连接到debian后台，并切换身份为root；

2. 运行以下代码，即可安装vaultwarden密码管理工具：
   <small><b>注：443是端口号，可修改，请使用https访问后台。</b></small>

   ```dockerfile
   docker pull vaultwarden/server:latest
   docker run -d --name vaultwarden \
   	-e ROCKET_TLS='{certs="/ssl/certs.pem",key="/ssl/key.pem"}' \	
   	-v /ssl/keys/:/ssl/ \
   	-v /vw-data/:/data/ \
   	-p 443:80 
   	vaultwarden/server:latest
   ```

   > You need to mount SSL files (-v argument) and you need to forward appropriate port (-p argument), usually port 443 for HTTPS connections. If you choose a different port number than 443 like for example 3456, remember to explicitly provide that port number when you connect to the service, example: `https://bitwarden.local:3456`.<br>
   > <small><b> 大白话：</b></small> 443的端口号是带ssl证书加密的https访问，如果需要更改这个443端口号为其他，请记住需要是https才可访问。

   如果你不需要使用ssl证书，请使用下面dockerfile运行：
   ```dockerfile
   docker pull vaultwarden/server:latest
   docker run -d --name vaultwarden -v /vw-data/:/data/ -p 80:80 vaultwarden/server:latest
   ```

   <small><b>说明：不使用SSL访问，无法端口转发到公网上，也就是无法在异地进行登陆。优先推荐使用上面带SSL证书进行https安全访问。</b></small>