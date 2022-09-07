# Nginx Proxy Manager ——强大的反向代理工具

> 反向代理神器
>
> [![](https://img.shields.io/badge/NginxProxyManager-Official-blue)](https://nginxproxymanager.com/)
>
> [![](https://img.shields.io/badge/NginxProxyManager-Github-blue)](https://github.com/NginxProxyManager/nginx-proxy-manager/)

**部署方式**

> <small><b>默认：所有操作均为ssh到Debian-KVM下操作。本教程代码适用于x86架构CPU。</b></small>

1. ssh连接到debian后台，并切换身份为root；

2. 使用vim/nano/vi等工具，创建NginxProxyManager的`docker-compose.yml`工具
   <small><b>注：80、81、443是分别是http、管理后台、https等端口号，可自行修改，后台访问通过http://192.168.x.x:81。</b></small>

   ```dockerfile
   version: '3'
   services:
     app:
       image: 'jc21/nginx-proxy-manager:latest'
       restart: unless-stopped
       ports:
         - '80:80'
         - '81:81'
         - '443:443'
       volumes:
         - ./data:/data
         - ./letsencrypt:/etc/letsencrypt
   ```

3. 使用 `docker-compose up -d` 启动容器

4. 通过http://192.168.x.x:81 访问NPM后台，默认账号密码信息如下：

   - Email: admin@example.com
   - Password: changeme

