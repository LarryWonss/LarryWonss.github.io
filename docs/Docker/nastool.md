![logo-blue](https://user-images.githubusercontent.com/51039935/197520391-f35db354-6071-4c12-86ea-fc450f04bc85.png)
# NAS媒体库管理工具

[![GitHub stars](https://img.shields.io/github/stars/NAStool/nas-tools?style=plastic)](https://github.com/NAStool/nas-tools/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/NAStool/nas-tools?style=plastic)](https://github.com/NAStool/nas-tools/network/members)
[![GitHub issues](https://img.shields.io/github/issues/NAStool/nas-tools?style=plastic)](https://github.com/NAStool/nas-tools/issues)
[![GitHub license](https://img.shields.io/github/license/NAStool/nas-tools?style=plastic)](https://github.com/NAStool/nas-tools/blob/master/LICENSE.md)
[![Docker pulls](https://img.shields.io/docker/pulls/jxxghp/nas-tools?style=plastic)](https://hub.docker.com/r/jxxghp/nas-tools)
[![Platform](https://img.shields.io/badge/platform-amd64/arm64-pink?style=plastic)](https://hub.docker.com/r/jxxghp/nas-tools)


Docker：https://hub.docker.com/repository/docker/jxxghp/nas-tools
Wiki：https://t.me/NAStool_wiki


## 功能：

NAS媒体库管理工具。


## 部署方式
### 1.ssh连接到debian后台，并切换身份为root；
### 2.使用docker cli安装
```
docker run -d \
    --name nas-tools \
    --hostname nas-tools \
    -p 3000:3000   `# 默认的webui控制端口` \
    -v $(pwd)/config:/config  `# 冒号左边请修改为你想在主机上保存配置文件的路径` \
    -v /你的媒体目录:/你想设置的容器内能见到的目录    `# 媒体目录，多个目录需要分别映射进来` \
    -e PUID=0     `# 想切换为哪个用户来运行程序，该用户的uid，详见下方说明` \
    -e PGID=0     `# 想切换为哪个用户来运行程序，该用户的gid，详见下方说明` \
    -e UMASK=000  `# 掩码权限，默认000，可以考虑设置为022` \
    -e NASTOOL_AUTO_UPDATE=false `# 如需在启动容器时自动升级程程序请设置为true` \
    -e NASTOOL_CN_UPDATE=false `# 如果开启了容器启动自动升级程序，并且网络不太友好时，可以设置为true，会使用国内源进行软件更新` \
    jxxghp/nas-tools
```

如果你访问github的网络不太好，可以考虑在创建容器时增加设置一个环境变量`-e REPO_URL="https://ghproxy.com/https://github.com/NAStool/nas-tools.git" \`。

### 2.使用docker-compose安装（推荐）
#### 1.使用vim/nano/vi等工具，创建nastool的docker-compose.yaml
```
#请结合实际情况，创建文件夹及文件
mkdir /docker/nastool #创建nastool文件夹
cd /docker/nastool #进入目录
nano docker-compose.yaml 
```
#### 2.编辑文件
```
version: "3"
services:
  nas-tools:
    image: jxxghp/nas-tools:latest
    ports:
      - 3000:3000        # 默认的webui控制端口
    volumes:
      - ./config:/config   # 冒号左边请修改为你想保存配置的路径，如果不懂，默认设置即可
      - /你的媒体目录:/你想设置的容器内能见到的目录   # 媒体目录，多个目录需要分别映射进来，需要满足配置文件说明中的要求
    environment: 
      - PUID=0    # 想切换为哪个用户来运行程序，该用户的uid
      - PGID=0    # 想切换为哪个用户来运行程序，该用户的gid
      - UMASK=000 # 掩码权限，默认000，可以考虑设置为022
      - NASTOOL_AUTO_UPDATE=false  # 如需在启动容器时自动升级程程序请设置为true
      - NASTOOL_CN_UPDATE=false # 如果开启了容器启动自动升级程序，并且网络不太友好时，可以设置为true，会使用国内源进行软件更新
     #- REPO_URL=https://ghproxy.com/https://github.com/NAStool/nas-tools.git  # 当你访问github网络很差时，可以考虑解释本行注释
    restart: always
    network_mode: bridge
    hostname: nas-tools
    container_name: nas-tools
```
#### 3.docker-compose up -d

## 后续如何更新

~~- 正常情况下，如果设置了`NASTOOL_AUTO_UPDATE=true`，重启容器即可自动更新nas-tools程序。~~

~~- 设置了`NASTOOL_AUTO_UPDATE=true`时，如果启动时的日志提醒你 "更新失败，继续使用旧的程序来启动..."，请再重启一次，如果一直都报此错误，请改善你的网络。~~

~~- 设置了`NASTOOL_AUTO_UPDATE=true`时，如果启动时的日志提醒你 "无法安装依赖，请更新镜像..."，则需要删除旧容器，删除旧镜像，重新pull镜像，再重新创建容器。~~

- nastool可自行拉取github更新，前提是网络环境要好。

## 关于PUID/PGID的说明

- 如在使用诸如emby、jellyfin、plex、qbittorrent、transmission、deluge、jackett、sonarr、radarr等等的docker镜像，请保证创建本容器时的PUID/PGID和它们一样。

- 在docker宿主上，登陆媒体文件所有者的这个用户，然后分别输入`id -u`和`id -g`可获取到uid和gid，分别设置为PUID和PGID即可。
```
# 切换为系统用户，这里以ikoolcore为例，结合实际情况调整
su ikoolcore
```
```
id -u
```
```
id -g
```

- `PUID=0` `PGID=0`指root用户，它拥有最高权限，若你的媒体文件的所有者不是root，不建议设置为`PUID=0` `PGID=0`
