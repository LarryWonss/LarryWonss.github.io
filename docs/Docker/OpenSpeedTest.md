# OpenSpeedTest - 高颜值测速工具

> [![](https://img.shields.io/badge/OpenSpeedTest-Official-blue)](https://openspeedtest.com/) <br> [![](https://img.shields.io/badge/OpenSpeedTest-Github-blue)](https://github.com/openspeedtest/Speed-Test) <br> [![](https://img.shields.io/badge/OpenSpeedTest-DockerHub-blue)](https://hub.docker.com/r/openspeedtest/latest) 

**部署方式**

> <small><b>默认：所有操作均为ssh到Debian-KVM下操作。本教程代码适用于x86架构CPU。</b></small>

1. ssh连接到debian后台，并切换身份为root；

2. 运行以下代码，即可安装PhotoPrism图片管理工具：
   <small><b>注：3000是端口号，可自行修改。Picture的路径记得替换为自己存放照片文件的文件夹的绝对路径</b></small>

   ```dockerfile
   sudo docker run --restart=unless-stopped --name openspeedtest -d -p 3000:3000 -p 3001:3001 openspeedtest/latest
   ```

   ![image.png](https://s2.loli.net/2022/09/07/lprOhz78ZU5JSmG.png)

3. 通过访问 <small><b>192.168.x.x:3000</b></small>  即可进入到测速后台。
   ![image.png](https://s2.loli.net/2022/09/07/kUi7zeFXoWQV5ND.png)
