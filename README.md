# chflags TrollHelper
## 不保证 100% 成功，不过比起隔壁需要依靠多任务的 TrollStore 我这个靠谱多了，但是出了问题也不要来找我，我就提供个方法给你参考而已
## 锁定已拥有的 TrollHelper 并通过 OTA 带上 iOS 16.6.1 或者 iOS 17.0
### 一、请先安装最新版本的 TrollStore 和通过 AppStore 安装 Tips（提示）

这个自己安装去，不想写教程

请保证使用当前 opa334 提供的最新版本

这里教程使用 Tips 作为 TrollHelper，所以请已经卸载的用户从 AppStore 中重新安装
### 二、安装 TrollStore 版 Filza 备用

建议从 TIGI Software 处下载 TorllStore 版本的 Filza

具体下载链接可以在下面的网页内找到

	https://www.tigisoftware.com/default/?page_id=78
### 三、使用 TrollStore 释放 TrollHelper

**请已经释放的用户手动重新释放，保证 TrollHelper 是最新版本**

0.打开 TrollStore 点击右下角选项卡 Settings

0-1.已安装用户请先点击 Uninstall Persistence Helper 来卸载掉目前已释放的 TrollHelper

1.在 PERSISTENCE 处点击 Install Persistence Helper 来安装 TrollHelper

2.然后弹出来的菜单中点击 Tips
### 四、使用 Filza 锁定已有的 TrollHelper 防止更新过程中被系统替换为新版的 Tips

01.打开 Filza

02.点击下面中央的五角星

03.点击 App 管理器

04.往下滑找到 “提示”，接下来点击右边蓝色的带外圆圈的 i

05.点击 “主程序”

06.点击右上角编辑，然后选中 Tips.app，然后点击左下角的复制

07.随便找个有文本框 App 粘贴，然后将路径后面的 /Tips.app 删除，前面加上 chflags -R schg,schange,simmutable 

下面是一个实际的例子：

你从 Filza 复制出来粘贴的样子

	/var/containers/Bundle/Application/1A3ED567-B13E-491D-8C88-2F5058CD8C4A/Tips.app

请修改为

	chflags -R schg,schange,simmutable /var/containers/Bundle/Application/1A3ED567-B13E-491D-8C88-2F5058CD8C4A

**请留意后方的 /Tips.app 应当移除，我留意到几个幸运儿没有移除，仅仅只是锁定了 Tips.app 文件夹，应该锁定 Tips.app 的上层文件夹**

08.将刚刚合成的命令复制到剪切板

09.找到 /usr/bin/vm_stat 并且点击运行

10.粘贴刚刚的命令，回车运行

这会锁定住 Tips，防止系统更新时将其修改为新版本的 Tips

~~你可以现在尝试验证，只需回到刚刚的目录尝试将 Tips.app 往左划，然后点击删除~~

~~应该会提示删除失败，未能储存该文件，因为您没有权限，这是正常的，说明已经锁定了~~

你可以现在尝试验证，只需回到刚刚的目录中，尝试在 Tips.app 的旁边新建一个文件夹，随便什么名字，你开心吧

你应该会看到“无法建立目录，未能储存该文件，因为您没有权限”，这是正常的，说明 Tips.app 的上层文件夹已被锁定

若成功建立，请删除建立的文件夹，并重新按照上方教程操作
### 五、延迟更新到 16.6.1 或者 17.0

本来不想写的，还是写一点吧

找到下面这个文件

	/var/containers/Shared/SystemGroup/systemgroup.com.apple.configurationprofiles/Library/ConfigurationProfiles/CloudConfigurationDetails.plist

将 IsSupervised 从 no 修改为 yes，这会让你设备处于监督模式，可以进行延迟更新，需要重启生效

接下来自行安装描述文件，我从这里安装的

	https://dhinakg.github.io/delayed-otas.html

感谢 Dhinak G

接下来正常更新，这个方法只需要更新后解锁 Tips 锁定

**小提示：如果你想要更保险，应该两个方法一起用，同时打开 TrollStore，保留在多任务中，为自己留下后路**
### 六、更新后的处理
#### 6-1 刷新图标缓存

更新后 TrollStore 桌面图标点击无法打开，请直接打开 TrollHelper（Tips）

点击 Refresh App Registrations 来刷新桌面图标缓存，当设备注销后 TrollStore 应该可以正常打开

**请继续按照下面的步骤解锁 Tips，要不然你的 TrollHelper 可能后续无法安装 TrollStore**
#### 6-2 接下来打开 Filza 解除 Tips 锁定

依然无法启动请重复第二部的步骤重新安装 Filza

01.打开 Filza

02.点击下面中央的五角星

03.点击 App 管理器

04.往下滑找到 “提示”，接下来点击右边蓝色的带外圆圈的 i

05.点击 “主程序”

06.点击右上角编辑，然后选中 Tips.app，然后点击左下角的复制

07.随便找个有文本框 App 粘贴，然后将路径后面的 /Tips.app 删除，前面加上 chflags -R noschg,noschange,nosimmutable 

下面是一个实际的例子：

你从 Filza 复制出来粘贴的样子

	/var/containers/Bundle/Application/1A3ED567-B13E-491D-8C88-2F5058CD8C4A/Tips.app

请修改为

	chflags -R noschg,noschange,nosimmutable /var/containers/Bundle/Application/1A3ED567-B13E-491D-8C88-2F5058CD8C4A

08.将刚刚合成的命令复制到剪切板

09.找到 /usr/bin/vm_stat 并且点击运行

10.粘贴刚刚的命令，回车运行

11.桌面找到提示，长按删除，然后从 AppStore 重新安装提示

12.打开 TrollStore 点击右下角选项卡 Settings

13.在 PERSISTENCE 处点击 Install Persistence Helper 来安装 TrollHelper

14.然后弹出来的菜单中点击 Tips
