# 2.2.2 使用动态DDNS插件实现外网访问

> 和前面2.2.1使用阿里云插件实现方法类似，仅使用的插件不一样，方法和原理一致。相同部分不再赘述。

**设置步骤：**

1. 在`服务`下面找到`动态DDNS`，点击并进入；<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129214045072.png" alt="image-20220129214045072" style="zoom:33%;" />
2. 点击`修改`，首先修改`DDNS服务提供商[IPv4]`为`aliyun.com`<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129214313788.png" alt="image-20220129214313788" style="zoom: 33%;" />

3. 具体设置如下：

   `基础设置：`

   - **查询主机名：**填写你想自定义的二级查询域名。示例：`router.xxx.com`，其中`xxx.com`为你在阿里云申请的主域名；
   - **域名：**和查询主机名保持一致。
   - **用户名：**阿里云后台获取的AccessKey ID，`具体获取方式参考2.2.1`
   - **密码：**阿里云后台获取的AccessKey Secret，`具体获取方式参考2.2.1`<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129215430697.png" alt="image-20220129215430697" style="zoom:33%;" />

   `高级设置：`

   - **IP地址来源[IPv4]：**网络
   - **网络[IPv4]：**WAN<br><img src="https://iswott.oss-cn-shenzhen.aliyuncs.com/blog/imgimage-20220129215509311.png" alt="image-20220129215509311" style="zoom:33%;" />

   `以上未提及修改的地方，均保持默认设置即可`

4. 保存并应用即可；

`端口转发设置参考2.2.1，步骤一样`