# EasyImage ——强大的个人图床工具

**项目地址：**

- [![](https://img.shields.io/badge/EasyImage-Github-blue)](https://github.com/DDS-Derek/EasyImage)
- [![](https://img.shields.io/badge/EasyImage-DockerHub-green)](https://hub.docker.com/r/ddsderek/easyimage)



**部署方式**

> <small><b>默认：所有操作均为ssh到Debian-KVM下操作。本教程代码适用于x86架构CPU。</b></small>

1. ssh连接到debian后台，并切换身份为root；

2. 运行以下代码，即可安装EasyImage图床工具：
   <small><b>注：8080是端口号，可自行修改。</b></small>

   ```dockerfile
   docker run -itd \
     --name easyimage \
     -p 8080:80 \
     -e TZ=Asia/Shanghai \
     -e PUID=1000 \
     -e PGID=1000 \
     -v /root/data/docker_data/easyimage/config:/app/web/config \
     -v /root/data/docker_data/easyimage/i:/app/web/i \
     ddsderek/easyimage:latest
   ```

   ![image.png](https://s2.loli.net/2022/09/06/e4aPbjpYWNv7LQA.png)

3. 访问debian虚拟机的IP:8080，即可打开初始化设置界面，设置完全后，如下图：
   ![image.png](https://s2.loli.net/2022/09/06/cid6Wg3PFfZQwJ9.png)
   <small><b>注：如果你习惯用markdown+图床的方式写博客，你将可以将所有图片上传到你家的内网服务器上，以杜绝外部服务不可用时，图片加载失败或丢失的问题。</b></small>



