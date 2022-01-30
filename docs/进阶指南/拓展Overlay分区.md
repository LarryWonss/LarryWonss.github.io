# 2.5 OpenWrt拓展Overlay分区

> 如果你的固件本身的剩余空间偏小，在OpenWrt运行一段时间后，剩余空间被日志文件耗尽时，你可能会面临后台无法进入的尴尬局面。为了杜绝该事情发生，故推荐在所有设置之前，先进行拓展Overlay分区。

**①什么是Overlay分区？**<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgoverlay.webp" alt="/images/Network/OpenWRT_overlay/overlay.webp" style="zoom:50%;" />

`OpenWRT` 一般使用的文件系统是 `SquashFS` ，这个文件系统的特点就是：**只读**。

一个只读的文件系统要怎么做到保存设置和安装软件的呢？这里就是使用 `/overlay` 的分区，`overlay` 顾名思义就是覆盖在上面一层的意思。虽然原来的文件不能修改，但把修改的部分放在 `overlay` 分区上，然后映射到原来的位置，读取的时候就可以读到修改过的文件了。

为什么要用这么复杂的方法呢？ `OpenWRT` 当然也可以使用 `EXT4` 文件系统，但使用 `SquashFS + overlay` 的方式有一定的优点。

- `SquashFS` 是经过压缩的，在路由器这种小型 `ROM` 的设备可以放下更多的东西。
- `OpenWRT` 的恢复出厂设置也要依赖于这个方式。在你重置的时候，它只需要把 `overlay` 分区清空就可以了，一切都回到了刚刷进去的样子。

如果是 `EXT4` 文件系统，就只能够备份每个修改的文件，在恢复出厂设置的时候复制回来，十分复杂。

当然，`SquashFS + overlay` 也有它的缺点：

- 修改文件的时候会占用更多的空间。首先你不能够删除文件，因为删除文件实际上是在 `overlay` 分区中写入一个删除的标识，反而占用更多的空间。

- 另外在修改文件的时候相当于增加了一份文件的副本，占用了双份的空间。

<hr>

**②  扩展Overlay分区操作步骤**

1. 创建新分区：

   - 首先进入到命令行终端工具；
   - 输入`cfdisk`打开磁盘管理界面；<br>![/images/Network/OpenWRT_overlay/cfdisk.webp](https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgcfdisk.webp)
   - 选择`Free Space`，再选择`New`，输入需要创建的分区大小，接着选择`Primary`；<br>![/images/Network/OpenWRT_overlay/primary.webp](https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgprimary-20220129224242122.webp)<br>![/images/Network/OpenWRT_overlay/primary.webp](https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgprimary.webp)
   - 选择`Write`，输入`yes`完成新分区的创建<br>![/images/Network/OpenWRT_overlay/write.webp](https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgwrite.webp)

2. 格式化分区：

   - 输入以下命令行：`mkfs.ext4 /dev/sda3 `

3. 挂载新分区：

   - 输入以下命令行：`mount /dev/sda3 /mnt/sda3 `

4. 转移到新分区：

   -  输入以下命令行：`cp -r /overlay/* /mnt/sda3 `

     `然后将原来 `upper` 层中的数据复制到新的分区中：`

5. Web界面修改配置：

   - 进入 `OpenWRT` Web 界面的`挂载点`挂载新创建的Overlay分区；`UUID根据新创建的分区大小选定，挂载点选择作为外部Overlay使用`<br>![/images/Network/OpenWRT_overlay/mountpoint.webp](https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgmountpoint.webp)

6. 完成，并重启生效。



