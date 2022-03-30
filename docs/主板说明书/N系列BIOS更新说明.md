# N5105/N5095/N6005 BIOS 2022/3/30更新

[![](https://img.shields.io/badge/下载-BIOS-brightgreen)](/主板说明书/BIOS for N5105/N5095/N6005 2022/03/30 Updated.zip)

> [!note]
>
> 更新日志：

1. 修正插SATA硬盘在BIOS没有选项显示的问题。

2. 修正插2条部份内存有出现花屏问题。

3. 修改F10键为保存退出。

4. 修正部分CPU核心电压问题。

5. 加速开箱第一次开机慢问题。



**更新教程**[![](https://img.shields.io/badge/下载-BIOS-brightgreen)](/主板说明书/BIOS for N5105/N5095/N6005 2022/03/30 Updated.zip)

1. 将优盘格式化成`FAT32`格式；
2. 将下载的BIOS文件（.zip格式）解压出来的到`EFI` 文件夹；[![](https://img.shields.io/badge/下载-BIOS-brightgreen)](/主板说明书/BIOS for N5105/N5095/N6005 2022/03/30 Updated.zip)
3. 将`EFI`文件夹的`所有文件`复制到优盘`根目录`;
4. 机器上电后，按`F7`进入bios刷写界面；
    ![](https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/img1648624041289258.png)
5. 选择UEFI：`U盘（UEFI + U盘名称）`选项
6. 进入到`UEFI：U盘`后，按`1`进行烧录；
7. 等待**自动烧录完成**（会出现sucessful相关字样），重启主机即可完成更新

> [!warning]
>
> 如果有装硬盘是 系统是UEFI模式的，建议 把硬盘拆掉，在更新。 不拆可能会 误进到硬盘的 EFI 造成无法更新； 不是UEFI 引导的系统不影响。