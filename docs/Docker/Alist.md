# Alist - 高颜值易用的网盘神器

> 感谢 Xh0fe 大神的分享。<br>
> 关注大神： [![](https://img.shields.io/badge/Xh0fe-Twitter-blue)](https://twitter.com/Xh0fe)  | [![](https://img.shields.io/badge/Xh0fe-Blog-red)](https://nn.ci/)  | [![](https://img.shields.io/badge/Xh0fe-Github-blue)](https://github.com/Xhofe) | [![](https://img.shields.io/badge/Alist-Dockerhub-blue)](https://registry.hub.docker.com/r/xhofe/alist/)



**安装Alist服务**

> <small><b>默认：所有操作均为ssh到Debian-KVM下操作</b></small>.

1. ssh连接到debian后台，并切换身份为root；

2. 运行以下代码，即可安装alist网盘服务：
   <small><b>注：5244的端口号，可以根据喜好在与其他服务不冲突的前提下，随便修改</b></small>.

   ```dockerfile
   docker run -d --restart=always -v /etc/alist:/opt/alist/data -p 5244:5244 --name="alist" xhofe/alist:latest
   ```

   ![image.png](https://s2.loli.net/2022/09/06/uBI3HUqk4lz2TyV.png)

3. 在终端输入`docker ps`，可看到运行到xhofe/alist服务已启动，访问端口号为5244；
   ![image.png](https://s2.loli.net/2022/09/06/fuESWlXHFGqVU91.png)

4. 获取初始登陆密码：在终端里输入`docker exec -it alist ./alist -password`；

   ![image.png](https://s2.loli.net/2022/09/06/gcfa7oW8Dq5vIlj.png)

5. 关于如何使用Alist部署网盘服务，可以到作者的wiki站点进行学习。
   传送门： **[Alist Doc](https://alist-doc.nn.ci/docs/intro)**

<hr>

