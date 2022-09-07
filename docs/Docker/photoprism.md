# PhotoPrism ——优秀的图片管理工具

> [![](https://img.shields.io/badge/PhotoPrism-Official-blue)](https://photoprism.app/)
> [![](https://img.shields.io/badge/PhotoPrism-Github-blue)](https://github.com/photoprism/photoprism)
> [![](https://img.shields.io/badge/PhotoPrism-DockerHub-blue)](https://hub.docker.com/r/photoprism/photoprism/tags)

**部署方式**

> <small><b>默认：所有操作均为ssh到Debian-KVM下操作。本教程代码适用于x86架构CPU。</b></small>

1. ssh连接到debian后台，并切换身份为root；

2. 运行以下代码，即可安装PhotoPrism图片管理工具：
   <small><b>注：2342是端口号，可自行修改。Picture的路径记得替换为自己存放照片文件的文件夹的绝对路径</b></small>

   ```dockerfile
   docker run -d \
     --name photoprism \
     --security-opt seccomp=unconfined \
     --security-opt apparmor=unconfined \
     -p 2342:2342 \
     -e PHOTOPRISM_UPLOAD_NSFW="true" \
     -e PHOTOPRISM_ADMIN_PASSWORD="insecure" \
     -v /photoprism/storage \
     -v ~/Pictures:/photoprism/originals \
     photoprism/photoprism
   ```

3. 通过访问 <small><b>192.168.x.x:2342</b></small>  即可进入到PhotoPrism的后台。登陆信息如下：

   - User: admin
   - Password: 
     通过在终端输入 `docker exec -ti photoprism photoprism passwd` 进行密码设置

   ![image.png](https://s2.loli.net/2022/09/07/fpkMlgS4XGcEbUK.png)

   ![image.png](https://s2.loli.net/2022/09/07/qPClZ9otTLwJAWB.png)

   ![image.png](https://s2.loli.net/2022/09/07/MF1UwQxBAqfrymk.png)

