**Mac系统无法连接Windows2012**

**问题现象：**

远程桌面连接提示远程桌面连接无法验证您希望连接的计算机的身份，如图：

![1.png](https://img1.jcloudcs.com/cms/21c5dd2e-d2d5-4cd3-b1f9-ed2f29224c4920180709141624.png)

**解决方法：**

1. 通过连接管理终端功能连接进入云服务器。

2. 点击任务栏powershell,然后输入命令gpedit.msc，输入完成后回车，回车后会显示本地组策略编辑器。

3. 依次找到【计算机配置】->【管理模板】->【windows组件】->【远程桌面服务】->【远程桌面会话主机】->【安全】->【远程（RDP）连接要求使用指定的安全层】，如下图：

![2.png](https://img1.jcloudcs.com/cms/5caf3a8f-468a-45c7-a076-9eecba8a687f20180709141742.png)

4. 双击【远程（RDP）连接要求使用指定的安全层】，出现下图：

![3.png](https://img1.jcloudcs.com/cms/2c07b2bc-4b2e-48ba-a038-b079909d469a20180709141933.png)

5. 将截图中的未配置，修改为已启用，安全层选择 rdp，最后点击应用确认。之后就可以通过Mac系统正常远程桌面连接Windows2012云主机了。

如无法解决您的问题，请向我们提工单。