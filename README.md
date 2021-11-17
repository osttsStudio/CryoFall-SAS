## CryoFall-SAS CryoFall 末日觉醒 一键安装&启动脚本

有任何bug和疑问请提交issues

仅保证在ubuntu20.04下正常运行（测试环境：阿里云和腾讯云） 其他版本和系统参照微软官方文档[在 Linux 上安装 .NET](https://docs.microsoft.com/zh-cn/dotnet/core/install/linux)

目前版本（v1.31.8.1）服务端为.NET 5.0及以上（仅需runtime）

使用前请确定拥有root账号或者root权限

**不推荐使用大陆服务器**

**如需使用大陆服务器建议注释掉cryofall_setup中`wget https://atomictorch.com/Files/CryoFall_Server_v1.31.8.1.zip `**

**然后手动下载[官方链接](https://atomictorch.com/Files/CryoFall_Server_v1.31.8.1.zip)（美国节点）并将压缩包保存到home文件夹（最新版本请查看[官方wiki](https://wiki.atomictorch.com/CryoFall/Server/Setup)）**

**文件在Windows编辑过 可能会存在无法运行的问题**

可尝试使用下面的方法修复：

**在脚本所在目录（可以是根目录）**

```
sed -i 's/\r$//' cryofall_*
```
cryofall_setup->一键安装&初次运行脚本<br>
cryofall_first_or_reset->一键重置脚本<br>
cryofall_start->重启服务器或结束掉screen后的一键启动脚本<br>

**注：不能且不应该在停止游戏进程却没有停止该screen时使用该脚本**<br>

**而是使用`dotnet CryoFall_Server.dll load`加载存档**<br>

**或者使用`dotnet CryoFall_Server.dll new`重置存档**<br>

**在初次启动服务器生成配置文件和存档后需要修改配置文件**，具体参考[官方wiki（English）](https://wiki.atomictorch.com/CryoFall/Server/Setup)

#### How to setup your own server (on any OS):

5. Usually it takes about 1-2 minutes to create a new world (or load a savegame). After that the server will keep writing performance statistics information every 20 seconds among other information such as the spawn scripts reporting and network events.
6. Stop the server. To do so enter the command below and press Enter key.
7. The server will save and quit. Now you have the "SettingsServer.xml" and "ModsConfig.xml" files.
8. Now you need to navigate to the subfolder "Data" (in the root of the server folder, **not** in the "Binaries/Server") and modify "SettingsServer.xml" to set the unique server **name** and set other settings, etc (there are XML comments explaining every setting so it should be straightforward). *Please note that you can (and should) edit **Description** and **Welcome message** from the **CURRENT GAME** menu right from the game after connecting to your server.*
9. If you are interested in making your server visible in the community servers list make sure to edit <is_public_server> and change the value from 0 to 1. Also, please make sure your router is configured correctly (port forwarding) to enable other people to connect to your machine from outside. But ideally, you should use dedicated server hardware (VPS or VDS) to host public servers.
10. While you're still editing "SettingsServer.xml" file, please find the value **<server_operators_list>** and change it to include **your nickname**! Otherwise, you will be unable to access your server console from the game and also you will be unable to edit the server's Description and Welcome message.
11. If you want to have a custom server icon, please replace the ServerIcon.png file in the "Data" subfolder.
      The icon image file requirements: **PNG24 format, 256x256 size, up to 100 KB**

#### 如何设置您自己的服务器（在任何操作系统上）：

5. 通常创建一个新世界（或加载一个存档）大约需要 1-2 分钟。之后，服务器将每 20 秒继续写入性能统计信息以及其他信息，例如 spawn 脚本报告和网络事件。
5. 停止服务器。为此，请输入以下命令并按 Enter 键。
6. 服务器将保存并退出。现在您有了“SettingsServer.xml”和“ModsConfig.xml”文件。
7. 现在您需要导航到子文件夹“Data”（在服务器（游戏）文件夹的根目录中，**而不是**在“Binaries/Server”中）并修改**“SettingsServer.xml”**以设置唯一的服务器**名称**并设置其他设置等（有解释每个设置的 XML 注释，所以它应该很简单）。*请注意，您可以（并且应该）在连接到服务器后直接从游戏中 的**当前游戏**菜单中编辑**描述**和**欢迎消息**。*
8. 如果您有兴趣让您的服务器在社区服务器列表中可见，请编辑 <is_public_server> 并将值从 0 改为 1。此外，请确保您的路由器配置正确（端口转发）以允许其他人连接从外面到您的机器。但理想情况下，您应该使用专用服务器硬件（VPS 或 VDS）来托管公共服务器。
12. 当您仍在编辑“SettingsServer.xml”文件时，请找到值**<server_operators_list>**并将其更改为包含 **您的昵称**（游戏ID）！否则，您将无法从游戏访问服务器控制台，也无法编辑服务器的描述和欢迎消息。
      10果您想要自定义服务器图标，请替换“Data”子文件夹中的 ServerIcon.png 文件。
      图标图片文件要求：**PNG24格式，256x256大小，最大100KB**。

## 路径

cryofall_start-> /<br>
cryofall_setup-> /<br>
cryofall_first_or_reset-> /<br>

`/ 服务器根目录`<br>

## 使用方法

使用脚本安装的服务器文件夹**默认在home文件夹**下，如需保存在其他位置可修改脚本内容

```
su #使用root账号（建议不要使用sudo，而是使用su登录为root账号）
cd <脚本所在目录>
cp cryofall_* /
/cryofall_setup
```

脚本文件如果**保存在根目录**，可在任意目录运行

```
/cryofall_setup
/cryofall_start
/cryofall_first_or_reset
```

如果脚本文件**保存在其他文件夹**，需在脚本所在目录运行

```
./cryofall_setup
./cryofall_start
./cryofall_first_or_reset
```

或添加环境变量（不推荐）

```
cryofall_setup
cryofall_start
cryofall_first_or_reset
```

设置开机启动（**未测试**）

```
cd /
or
cd <脚本所在目录>
systemctl enable cryofall_start 
```
