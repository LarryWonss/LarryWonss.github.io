# N5105/N5095/N6005 BIOS 2022/3/30更新

> [!note]
>
> 更新日志：
>
> 1. 修正插SATA硬盘在BIOS没有选项显示的问题。
>
> 2. 修正插2条部份内存有出现花屏问题。
>
> 3. 修改F10键为保存退出。
>
> 4. 修正部分CPU核心电压问题。
>
> 5. 加速开箱第一次开机慢问题。





> [!warning]
>
> 更新BIOS是比较⚠️危险⚠️的操作，谨慎考虑是否更新。**更新失败**⚠️会导致机器*无法开机*；本教程近针对本渠道所出N5095、N5105、N6005有效。因操作失误导致更新BIOS失败无法开机等后果，需要消费者自行寄回（消费者需承担来回运费）售后强刷。
> [![](https://img.shields.io/badge/下载-BIOS-brightgreen)](https://github.com/LarryWonss/LarryWonss.github.io/raw/main/docs/others/BIOS_for_N5105_N5095_N6005%202022_03_30_Updated.zip)｜[![](https://img.shields.io/badge/下载-格式化工具-brightgreen)](https://github.com/LarryWonss/LarryWonss.github.io/blob/main/docs/others/HP%E4%BC%98%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98%E6%A0%BC%E5%BC%8F%E5%8C%96%E5%B7%A5%E5%85%B7.zip)

1. 将优盘格式化成`FAT32` 的DOS盘；

    - 格式化工具下载：[![](https://img.shields.io/badge/下载-格式化工具-brightgreen)](https://github.com/LarryWonss/LarryWonss.github.io/blob/main/docs/others/HP%E4%BC%98%E7%9B%98%E5%90%AF%E5%8A%A8%E7%9B%98%E6%A0%BC%E5%BC%8F%E5%8C%96%E5%B7%A5%E5%85%B7.zip)
    - 格式化步骤：
      ![使用说明图解](https://s2.loli.net/2022/03/30/GLehRtDQarxkow2.png)

2. 将下载的BIOS文件（.zip格式）解压出来的到`EFI` 文件夹；[![](https://img.shields.io/badge/下载-BIOS-brightgreen)](https://github.com/LarryWonss/LarryWonss.github.io/raw/main/docs/others/BIOS_for_N5105_N5095_N6005%202022_03_30_Updated.zip)

3. 将`EFI`文件夹的`所有文件`复制到优盘`根目录`;

4. 机器上电后，按`F7`进入bios刷写界面；
   
    ![](https://s2.loli.net/2022/03/30/fhQ95XmiMlcNxRE.png)
    
5. 选择UEFI：`U盘（UEFI + U盘名称）`选项

6. 进入到`UEFI：U盘`后，按`1`进行烧录；

7. 等待**自动烧录完成**（会出现`process completed`相关字样，如下图），重启主机即可完成更新。
    ![IMG_1236](https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgIMG_1236.jpg)

> [!warning]
>
> 如果有装硬盘是 系统是UEFI模式的，建议 把硬盘拆掉，在更新。 不拆可能会 误进到硬盘的 EFI 造成无法更新； 不是UEFI 引导的系统不影响。