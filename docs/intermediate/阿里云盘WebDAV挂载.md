# 2.4 使用阿里云盘插件挂载阿里云盘WebDAV

> 阿里云盘是阿里巴巴全球资深技术团队倾力打造的一款个人网盘，主要功能为速度快、不打扰、够安全、易于分享，为C端用户提供存储备份及智能相册等服务的网盘产品。 最近一段时间阿里云盘可谓是火出了太阳系（还不是因为115太贵，百度网盘太慢），各种资源无论是影视作品还是素材都在阿里云盘上层出不穷。

<img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210819205217351.png" alt="1" style="zoom:33%;" />

<hr>

**挂载步骤：**

1. 注册阿里云盘账号；⏩[点击注册](https://pages.aliyundrive.com/mobile-page/web/beinvited.html?code=90683f1)

2. 设备端安装好支持WebDAV协议的软件
   - MAC端：Infuse 7 
   - iOS端：NPlayer & NPlayer PLUS
   - Android端：支持WebDAV传输协议的文件管理器
3. 获取阿里云盘的Refresh Token先通过浏览器（`建议chrome`）登陆阿里云盘账号；[⏩一键登陆](https://www.aliyundrive.com/sign/in)

4. 登陆成功后，按`F12`调出开发者工具，点击`Console`，并输入以下代码后回车确认；

```
JSON.parse(window.localStorage.getItem("token"))["refresh_token"];
```

5. 控制台输出的`字符串`即是你账号的` Refresh Token`<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210819210600145.png" style="zoom:33%;" />



6.  在左侧的`服务`版块中找到`阿里云盘WebDAV`，点击进入；<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129221541174.png" alt="image-20220129221541174" style="zoom:25%;" />

   `具体设置：`

   - **RefreshToken：**填写前面步骤获取到的字符串

   - **主机：**填写软路由后台地址，示例`192.168.1.1`

   - **端口：**自定义，建议`8080`

   - **用户名：**自定义

   - **密码：**自定义

     `其他不需要进行设置`

7. 保存并应用。

   <hr>

**使用方法：**

以Mac端Infuse 7设置为例：如下图：<br><img src="https://www-jackeroo-org.oss-cn-shenzhen.aliyuncs.com/blog/photosimage-20210819211552832.png" alt="image-20210819211552832" style="zoom:50%;" />



`其他设备，设置方法类似，请自行设置`   

   

   

   