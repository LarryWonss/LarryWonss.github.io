# Squoosh - GoogleChromLabs开源的强大图片压缩工具

> 该工具由Google Chrome Labs团队开源在Github上。[![](https://img.shields.io/badge/GoogleChromeLabs-Github-yellow)](https://github.com/GoogleChromeLabs/squoosh)

本Docker由v站老哥[![](https://img.shields.io/badge/V2ex-AllenHua-yellowgreen)](https://www.v2ex.com/member/AllenHua) 开源在Github，并分享在V2ex上。感谢老哥分享。[![](https://img.shields.io/badge/Dockerhub-%E9%95%9C%E5%83%8F-blue)](https://hub.docker.com/r/dko0/squoosh)

**本Docker部分分享，使用环境均为：PVE下虚拟出的debian11虚拟机，OpenWRT下使用方式大同小异**

**用法：**

1. ssh登陆PVE上的debian虚拟机；![image-20220904103055107.png](https://s2.loli.net/2022/09/04/tDhpumxYvPMR3yn.png)

2. 输入以下docker run，并按回车（<small>如提示权限不够，请切换到root身份执行</small>）；
   ```dockerfile
   docker run -d --name squoosh \
       --restart unless-stopped \
       -p 7701:8080 \
       dko0/squoosh:1.12.0
   ```

   ![image-20220904103350664.png](https://s2.loli.net/2022/09/04/DLQXdOphBGskVJa.png)
   ![image-20220904103413455.png](https://s2.loli.net/2022/09/04/27o8utiPKvYJkDM.png)
   
3. 输入`docker ps`查看docker镜像是否成功启动；
   ![image-20220904103530491.png](https://s2.loli.net/2022/09/04/bmpYnG2zxkXiBuR.png)

4. 浏览器输入Debain`虚拟机地址:端口号`7701进入squoosh微服务工具后台；

   ![image-20220904103802388.png](https://s2.loli.net/2022/09/04/3YSNPjho17GL2Qs.png)

5. 至此，squoosh内网图片压缩工具部署完毕。
   ***压缩比非常大，将1.43MB的图片压缩到151kb，压缩率达到89%！***
   ![image.png](https://s2.loli.net/2022/09/04/1yAF7g2DejpC6EQ.png)