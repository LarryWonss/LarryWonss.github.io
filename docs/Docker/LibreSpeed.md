# LibreSpeed - 内外网测速工具

![](https://github.com/librespeed/speedtest/blob/master/.logo/logo3.png)

> LibreSpeed: Free and Open Source Speedtest. No Flash, No Java, No Websocket, No Bullshit.
>
> 非常简单，非常易用的内外网测速工具。
>
> - 官网：[LibreSpeed - Speedtest]([librespeed.org](https://librespeed.org/))
> - 官方Github仓库：[librespeed/speedtest](https://github.com/librespeed/speedtest)
> - Dockerhub地址：[adolfintel/speedtest](https://registry.hub.docker.com/r/adolfintel/speedtest)



**工具部署**

1. ssh登陆上Debian虚拟机，并切换身份为root；
   ![image.png](https://s2.loli.net/2022/09/04/OCvyPuAXNjJZfnH.png)

2. 运行以下`docker pull adolfintel/speedtest`拉取docker镜像到本地；
   ![image.png](https://s2.loli.net/2022/09/04/CIe4oW51kKbXvzS.png)

3. 运行以下代码启动docker服务
   ```dockerfile
   docker run -e MODE=standalone -e TELEMETRY=true -e ENABLE_ID_OBFUSCATION=true -e PASSWORD="yourPasswordHere" -e WEBPORT=86 -p 86:86 -it adolfintel/speedtest
   ```

   **端口号、密码可自行修改，我这里端口是86**
   ![image.png](https://s2.loli.net/2022/09/04/yw9NhIAeXMfiaxv.png)
   **外网测速需要有公网IP或者你已打隧道，外网测速需要在一级拨号路由设置端口转发**


