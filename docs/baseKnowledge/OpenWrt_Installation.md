# 1.3 OpenWrt系统安装

> 安装OpenWrt系统方法有比较多种，目的都是将OpenWrt固件写入到硬盘中，让系统每次均中硬盘中启动系统即可。



<hr>

###### ①最简单的方法：

`借助写盘软件`

- **所需工具：**

  - OpenWrt固件一份；

    **推荐：**	｜[eSir固件](https://openwrt.club/dl)｜[SulingGG](https://github.com/SuLingGG/OpenWrt-Buildbot)｜[HomeLede](https://github.com/xiaoqingfengATGH/HomeLede) ｜

    `有技术功底的大佬，请自行编译。参考Lean大佬源码`：[⏩前往](https://github.com/coolsnowwolf/lede)

  - mSATA转USB转接卡`长这样：`<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220128203650844.png" alt="image-20220128203650844" style="zoom:50%;" />

  - PC或者Mac电脑一台；

  - 写盘软件：

    - Mac：[BalenaEtcher](https://www.balena.io/etcher/)
    - Windows：[BalenaEtcher](https://www.balena.io/etcher/) ｜[Rufus](https://rufus.ie/zh/)｜其他

  <hr>

- **写盘步骤：**

  1. 将下载的固件`解压为`后缀名为`.img`格式的文件;<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220128204540222.png" alt="image-20220128204540222" style="zoom: 50%;" />

  2. `打开`写盘软件（`这里以Mac使用BalenaEtcher写盘为例`），`插入`装好mSATA硬盘的转接卡到你的PC或者Mac上；<img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220128232559873.png" alt="image-20220128232559873" style="zoom:50%;" />

  3. `选择`需要写入的固件并`选中`你插入的这块mSATA硬盘，点击`写入`；<img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220128232822383.png" alt="image-20220128232822383" style="zoom:50%;" /><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220128233020868.png" alt="image-20220128233020868" style="zoom:50%;" />

  4. 刷写成功，安全弹出；

     `将mSATA硬盘装入软路由，插电即可启动刷入的软路由系统。`



<hr>

②**借助`Windows PE`和`physdiskwrite.exe`写盘程序：**

- **所需工具：**

  - 一份OpenWrt固件；`推荐：`｜[eSir固件](https://openwrt.club/dl)｜[SulingGG](https://github.com/SuLingGG/OpenWrt-Buildbot)｜[HomeLede](https://github.com/xiaoqingfengATGH/HomeLede) ｜

  - U盘1个或2个，用于安装**Windows PE系统**和拷贝`physdiskwrite.exe`写盘程序；<br>**|  [Physidiskwrite.exe写盘程序下载](https://m0n0.ch/wall/physdiskwrite.php)   |**`下载后重命名文件名为physdiskwrite.exe`
  - Windows PE系统安装程序，`推荐：`[微PE工具箱](https://www.wepe.com.cn/download.html)<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220128234331704.png" alt="image-20220128234331704" style="zoom: 36%;" />

- **安装步骤：**

  1. 使用前面准备的`微PE工具箱`，制作Windows PE系统；

  2. 拷贝OpenWrt固件（必须为`.img格式`）和`physdiskwrite.exe`写盘程序至另一块优盘或当前PE系统盘的储存空间内；

     `注意：`<br>`1、OP固件必须为.img格式，且为了后续安装方便，建议固件重命名为1.img;` <br>`2、需要记住physdiskwrite.exe拷贝至的盘符和路径`

  3. 将制作好PE系统的优盘插入软路由上，并通过按住进入BIOS的按键进入到BIOS，设置从优盘启动，保存并应用；

     `注意：不同工控机，甚至型号相同主板不同的机器，进入BIOS快捷键都未必一致，通常来说，可以尝试以下方式：Delete键、F11、F2、F7`

  4. 机器重新启动后会从优盘内引导进入到WinPE系统；<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220128235432385.png" alt="image-20220128235432385" style="zoom:67%;" />

  5. 先使用PE系统内的DiskGenius把mSATA硬盘格式化，切记  ***不要***  `新建分区`，保存并应用；

  6. 以`管理员`身份打开`命令提示符`，输入`physdiskwrite -U 1.eSir_07.img`将OpenWrt固件写入到mSATA硬盘中；<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220128235730049.png" alt="image-20220128235730049" style="zoom:67%;" />

     - -U：表示进入到磁盘盘符为U的磁盘内（该磁盘存有`physdiskwrite.exe`程序）；
     - eSir_07.img：为你重命名的固件名，带`.img`后缀

  7. 操作第6步命令后，会要求你输入固件需要写入的磁盘序号，请自行确认mSATA固态盘的序号；

  8. 选择盘序号后，系统弹出是否擦除写入，输入`y`开始写入，写入完成后，弹出`x/x bytes written in total`即表示写入成功；

  9. 拔出优盘，重新断电重启软路由即可进入到软路由后台

     `软路由后台登陆地址，会因为你选择的固件不同而不同，烦请查看固件作者Github说明！`







