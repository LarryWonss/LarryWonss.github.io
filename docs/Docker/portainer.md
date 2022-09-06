<center><h3>Portainer</h3></center>

> About Portainer:
>
> > Portainer Community Edition (CE)  is a powerful, open source toolset that allows you to easily build and manage containers in Docker, Docker Swarm, Kubernetes and Azure ACI.
> >
> > Portainer hides the complexity of managing containers behind an easy-to-use UI. 
>
> 翻译过来的大白话理解就是：
>
> > Portainer社区版是一个功能强大的开源工具集，可让您轻松构建和管理 Docker、Docker Swarm、Kubernetes 和 Azure ACI 中的容器。在这里我们只会提到如何用portainer管理和查看我们的docker程序。



**在Docker下安装Portainer**

> 上一个板块，我们分享了如何安装docker容器，那么接下来的在docker容器中安装docker程序将会非常简单

1. 首先，创建用于存放portainer数据库的数据卷；
   ```shell
   docker volume create portainer_data
   ```

2. 接着，下载并安装Portainer服务器容器：
   ```shell
   docker run -d -p 8000:8000 -p 9443:9443 --name portainer \
       --restart=always \
       -v /var/run/docker.sock:/var/run/docker.sock \
       -v portainer_data:/data \
       portainer/portainer-ce:2.9.3
   ```

   <small><b>注意：默认portainer会生成并使用自签名SSL证书来保护9443端口，所以在部署完毕后，需要使用https://192.168.x.x:9443 才能进入到portainer后台</b></small>.

3. 上面第二步代码运行完毕，portainer即部署完毕，使用`docker ps`来验证：
   ```shell
   root@server:~# docker ps
   CONTAINER ID   IMAGE                          COMMAND                  CREATED       STATUS      PORTS                                                                                  NAMES             
   de5b28eb2fa9   portainer/portainer-ce:2.9.3   "/portainer"             2 weeks ago   Up 9 days   0.0.0.0:8000->8000/tcp, :::8000->8000/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   portainer
   ```




