# OpenWrt下挂载硬盘和开启共享

> 现在的软路由，基本都可以加装一块2.5寸的普通笔记本硬盘，这对于有家庭局域网多台设备之间有轻度的文件共享需求来说，可以说软路由挂载SAMBA文件共享，是比较经济划算的解决方案。

#### 一、挂载硬盘

在安装好硬盘之后，首先需要```系统>>>挂载点```挂载好硬盘。

1. 首先，在```已挂载的文件系统```中，查看是否已经自动挂载了;<br><img src="https://i.loli.net/2020/08/27/bC8QOteZ39MgRUH.png" alt="image-20200827213634379" style="zoom: 50%;" />

2. 如果没有自动挂载，则进入到```系统>>>挂载点```，然后在```挂载点```处查看是否自动挂载了加装的硬盘，如果没有，点击```添加```;

3. 设置```挂载点-存储区```:

   - 启用此挂载点：勾选
   - UUID：勾选挂载硬盘（根据硬盘大小区分）
   - 挂载点：```/mnt/sdb1```(sdb1根据实际需要修改数字，也许是sdb2)

   <img src="https://i.loli.net/2020/08/27/8L9l6qmZK1BDsHP.png" alt="image-20200827213759259" style="zoom: 50%;" />

4. 保存并应用

#### 二、硬盘分区

在我们安装好硬盘之后，使用ssh登录到软路由后台，输入分区命令：```fdisk /dev/sdb1```，**命令中的sdb1根据实际的挂载硬盘的序号填写**

- 输入```p```，显示现有分区信息

- 输入```n```，新建分区，然后再输入```p```新建主分区，根据提示完成分区的创建，警告输入```y```，然后输入```p```查看分区是否成功，最后输入```w```保存退出<br>

  <img src="https://i.loli.net/2020/08/27/Tr9ODi4EY3BJHjp.png" alt="image-20200827214117675" style="zoom: 50%;" />

#### 三、格式化分区

- 格式化命令：```mkfs.ext4 /dev/sdb1```

- 如无法格式化，先取消共享、挂载，命令为：```umount /dev/sdb1 /mnt/sdb1```<br>

  <img src="https://i.loli.net/2020/08/27/nTl6evzaoVMHBN4.png" alt="image-20200827214215387" style="zoom: 50%;" />

#### 四、配置SMB网络共享

1. 进入网络```存储>>>网络共享```：

2. 设置共享目录：

   - 名称：随便根据自己的喜好设置
   - 目录：```/mnt/sdb1```（上面挂载设置的位置）
   - 允许用户：空
   - 只读：不勾选
   - 可浏览：勾选
   - 允许匿名用户：勾选
   - 文件权限：均为0777<br>

   <img src="https://i.loli.net/2020/08/27/8DJKIEcl5x6wneu.png" alt="image-20200827214639289" style="zoom: 37%;" />

3. 修改编辑模板：

   - 注释掉```invalid users = root```(前面加一个#号即可)<br>

     <img src="https://i.loli.net/2020/08/27/oi6tI1Z93xOTGfq.png" alt="image-20200827214945287" style="zoom: 43%;" />

4. 保存并应用

#### 五、本地映射SMB网盘

1. 打开```我的电脑```，在地址栏输入```\\192.168.1.1```(请根据你实际设置的后台地址输入)，按```回车```进入<br>

   <img src="https://i.loli.net/2020/08/27/7avwQFkNRlH9xWh.png" alt="image-20200827215426234" style="zoom: 50%;" />

2. 右键需要挂载的```sdb1```，点击```映射网络驱动器```，点击```完成```<br>

   <img src="https://i.loli.net/2020/08/27/b8Sa3HNsOBnqdX4.png" alt="image-20200827215623844" style="zoom: 50%;" />

3. **All Well done! Enjoy yourselves!**<br><img src="https://i.loli.net/2020/08/27/YFn15TKcdkvfayh.png" alt="image-20200827215717349" style="zoom: 50%;" />