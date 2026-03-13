# macOS 26 降级 15

> 机器型号：MacBook Air M4 24 + 512GB

## 备份系统数据

- 时间机器

- 手动备份

### 软件备份

- [x] MySQL
- [x] Tomcat
- [x] Docker 容器备份
- [x] Cherry-Studio 数据备份
- [x] Zotero 备份 & 插件
- [x] Clash Verge 配置备份

### 软件清单

```
Advanced Renamer.app
AltTab.app
BaiduNetdisk_mac.app
calibre.app
Cherry Studio.app
Clash Verge.app
Cursor.app
Docker.app
Foxit PDF Editor.app
GarageBand.ap
Google Chrome.app
i4Tools.app
IINA.app
iMovie.app
Infuse.app
IntelliJ IDEA.app
iShot.app
Keka.app
KeyCastr.app
Keynote.app
LANDrop.app
Mos.app
Navicat Premium Lite.app
Numbers.app
OBS.app
Ollama.app
OpenVPN Connect
OpenVPN Connect.app
Pages.app
Paintbrush.app
Pearcleaner.app
PicGo.app
PyCharm.app
qbittorrent.app
QQ.app
Safari.app
Steam.app
Synology Drive Client.app
TencentMeeting.app
ToDesk.app
Typora.app
Utilities
UUBooster.app
Visual Studio Code.app
VMware Fusion.app
WeChat.app
wpsoffice.app
Xcode.app
Xmind.app
Zotero.app
小绿鲸英文文献阅读器.app
```

### 文件

- [x] 苹果相册
- [x] 电脑截图
- [x] 文稿文件夹
- [x] 个人数据（群晖同步）
- [x] 下载 文件夹
- [ ] Git 仓库 Push 到 GitHub（pytoch模型分开备份）
- [x] 星露谷 Mods
- [x] Programs 文件夹
- [x] 同步 iCloud
- [x] SSH 密钥：路径 `~/.ssh` 文件夹（隐藏文件，可在个人目录下按 `Cmd + Shift + .` 显示隐藏文件）
- [x] 备份 VS Code 配置
- [x] 备份 idea 配置

### 聊天记录

- [x] 同步微信聊天记录到手机
- [x] 同步QQ微信记录到手机
- [x] 邮箱 NEU 配置导出

## 下载系统镜像

1. 确保你用来下载 macOS 的 Mac [与相应 macOS 兼容](https://support.apple.com/zh-cn/102662#compatibility)。
2. 如果你下载 macOS 是为了[制作可引导的安装器](https://support.apple.com/zh-cn/102662#bootable)，请确保你的 Mac 使用的是 macOS Mojave 10.14 或更高版本。
3. 使用以下链接在 App Store 中找到相应 macOS。如果这些链接无法正常使用，请用 Safari 浏览器再试一次；Safari 浏览器位于“应用程序”文件夹中。
	- Tahoe 26（使用“[软件更新](https://support.apple.com/zh-cn/102662#softwareupdate)”或“[终端](https://support.apple.com/zh-cn/102662#terminal)”）
	- [Sequoia 15](macappstores://apps.apple.com/cn/app/macos-sequoia/id6596773750?mt=12)
	- [Sonoma 14](macappstores://apps.apple.com/cn/app/macos-sonoma/id6450717509?mt=12)
	- [Ventura 13](macappstores://apps.apple.com/cn/app/macos-ventura/id1638787999?mt=12)
	- [Monterey 12](macappstores://apps.apple.com/cn/app/macos-monterey/id1576738294?mt=12)
	- [Big Sur 11](macappstores://apps.apple.com/cn/app/macos-big-sur/id1526878132?mt=12)
	- [Catalina 10.15](macappstores://apps.apple.com/cn/app/macos-catalina/id1466841314?mt=12)
	- [Mojave 10.14](macappstores://apps.apple.com/cn/app/macos-mojave/id1398502828?mt=12)
	- [High Sierra 10.13](macappstores://apps.apple.com/cn/app/macos-high-sierra/id1246284741?mt=12)

下载到“应用程序”文件夹后，安装器会自动打开。请按照屏幕上的安装说明操作。或者，在不安装的情况下退出，将安装器留在“应用程序”文件夹中供以后使用。

## 制作系统安装盘

1. 准备一个 U 盘
2. 使用 macOS 磁盘工具格式化 U 盘，并将 U 盘重命名为 `MyVolume`
3. 打开终端，使用命令开始制作系统安装盘到 U 盘

```shell
sudo /Applications/Install\ macOS\ Sequoia.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```

退出 Apple ID 关闭设备查找

## 更改启动磁盘安全性级别

1. 在搭载 Apple 芯片的 Mac 上，选取苹果菜单 <img src="https://help.apple.com/assets/68FBBA193607B5D7D10E93FA/68FBBA1F3B0411BD870E56D1/zh_CN/2f77cc85238452e25cb517130188bf99.png" alt="img" style="zoom: 25%;" /> >“关机”。
2. 按住电源按钮直至“正在载入启动选项”出现。
3. 点按“选项”，然后点按“继续”。
4. 选择启动磁盘，然后点按“下一步”。
5. 选择管理员账户，然后点按“下一步”。
6. 输入管理员账户的密码，然后点按“继续”。
7. 在“恢复” App 中，选取“实用工具”>“启动安全性实用工具”。
8. 选择要用来设定安全策略的系统。
9. 如果磁盘已使用文件保险箱加密，请点按“解锁”，输入密码，然后点按“解锁”。
10. 点按“安全策略”。
11. 选择以下一个安全性选项：
    - *完整安全性：*确保只有当前的操作系统或者当前 Apple 信任的签名操作系统软件才能运行。此模式要求在安装软件时接入网络。
    - *降低安全性：*允许运行 Apple 信任过的任何版本的签名操作系统软件。
12. 如果选择了“降低安全性”，请选择以下任一选项（如果需要）：
    - *允许用户管理来自被认可开发者的内核扩展：*允许安装使用旧版内核扩展的软件。
    - *允许远程管理内核扩展和软件自动更新：*使用设备管理服务授权远程管理旧版内核扩展和软件更新。
13. 点按“好”。
14. 如果更改了安全性，请点按“用户”弹出式菜单，选取管理员账户，输入该账户的密码，然后点按“好”。
15. 选取苹果菜单 >“重新启动”。你必须重新启动 Mac 以使更改生效。

## 重装系统

1. 将 Mac 关机或关闭 Mac 电源。
2. 将可引导的安装器直接连接到 Mac。
3. 按住 Mac 上的电源按钮。随着你继续按住这个按钮，Mac 会启动并载入[启动选项](https://support.apple.com/zh-cn/102342)，其中会显示可引导宗卷，包括可引导的安装器。
4. 选择可引导的安装器，然后点按“继续”。
5. macOS 安装器打开后，请按照屏幕上的说明操作。

## 总结

一次不完美的降级，代码仓库下深度学习代码里面有体积大的模型文件。疏忽没看到 push 失败，导致代码丢失。

## 参考

- [在搭载 Apple 芯片的 Mac 上更改启动磁盘的安全性设置](https://support.apple.com/zh-cn/guide/mac-help/mchl768f7291/mac)
- [如何下载和安装 macOS](https://support.apple.com/zh-cn/102662)
- [创建可引导的 macOS 安装器](https://support.apple.com/zh-cn/101578)
