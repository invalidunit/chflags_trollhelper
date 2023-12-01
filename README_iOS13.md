# chflags TrollHelper
## 不保证 100% 成功，反正出了问题不要来找我就行，我就提供个方法给你参考而已
## 锁定已拥有的 TrollHelper 并通过 OTA 带上 iOS 16.6.1 或者 iOS 17.0
### 一、请先越狱你的设备

这个自己安装去，不想写教程
### 二、从 Havoc 源中安装 TrollHelper

若还没添加源，请在你的包管理器中添加下列源地址

	https://havoc.app/

截至到写这个教程的之时，当前 Havoc 提供的最新版本为 2.0.7，请不要安装低于这个版本的 TrollHelper
### 三、使用 TrollHelper 释放 TrollStore

打开桌面多出来的 TrollHelper，点击 “Install TrollStore”

**如果你从越狱商店安装的 TrollHelper 是直接闪退的，请不要往教程后面看**

当桌面出现蓝色的 TrollStore 视为成功

正常情况下 TrollStore 应该是无法正常打开的，会直接**闪退**，不用管他
### 四、安装 Filza 备用

推荐在官方源进行安装，其他软件源打包的有时候有奇怪的权限问题，官方源的不购买不会限制任何功能使用，仅仅在 Filza 内使用多任务窗口时有个小小的弹窗

官方源地址

	https://tigisoftware.com/cydia/

安装好 Filza File Manager 64-bit 备用
### 五、使用 Filza 自己释放 TrollHelper 到 Tips

01.从 TrollStore 储存库中下载最新版本的 PersistenceHelper_Embedded，截止到写教程时最新版本为 2.0.8，请不要低于这个版本

	https://github.com/opa334/TrollStore/releases

将下载下来的文件分享到 Filza 备用

02.打开 Filza

03.点击下面中央的五角星

04.点击 App 管理器

05.往下滑找到 “提示”，接下来点击右边蓝色的带外圆圈的 i

06.点击 “主程序”

07.打开 Tips.app 文件夹

08.找到原本的 Tips 文件，重命名为 Tips.bak

09.将刚刚准备好的 PersistenceHelper_Embedded 文件复制过来，重命名为 Tips

10.点击 Tips.bak 右边蓝色的带外圆圈的 i，记下“所有权”下面的“所有者”和“组”，然后点击“访问权限”下方的“粘贴”，记下顶部的数字

11.点击 Tips 右边蓝色的带外圆圈的 i，将“所有权”下面的“所有者”和“组”设置为刚刚 Tips.bak 中看见的值，随后点击“访问权限”下方的“粘贴”，将顶部文本框的数字修改为刚刚 Tips.bak 的数字，然后按下右下角的储存

12.回到桌面打开“提示”app，应该能看到 TrollHelper，如果**闪退了**，请按照刚刚步骤，**重新设置** Tips 文件的权限

### 六、锁定 Tips

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

09.在越狱商店中检查自己有没有安装 file-cmds，没有的话请先去安装

09.找到 /usr/bin/vm_stat 并且点击运行，或者你使用其他越狱终端运行都可以，随便吧

10.粘贴刚刚的命令，回车运行

这会锁定住 Tips，防止系统更新时将其修改为新版本的 Tips

你可以现在尝试验证，只需回到刚刚的目录中，尝试在 Tips.app 的旁边新建一个文件夹，随便什么名字，你开心吧

你应该会看到“无法建立目录，未能储存该文件，因为您没有权限”，这是正常的，说明 Tips.app 的上层文件夹已被锁定

若成功建立，请删除建立的文件夹，并重新按照上方教程操作
### 七、延迟更新到 16.6.1 或者 17.0

本来不想写的，还是写一点吧

找到下面这个文件

	/var/containers/Shared/SystemGroup/systemgroup.com.apple.configurationprofiles/Library/ConfigurationProfiles/CloudConfigurationDetails.plist

将 IsSupervised 从 no 修改为 yes，这会让你设备处于监督模式，可以进行延迟更新，需要重启生效

接下来自行安装描述文件，我从这里安装的

	https://dhinakg.github.io/delayed-otas.html

感谢 Dhinak G

接下来正常更新，这个方法只需要更新后解锁 Tips 锁定
### 八、更新后的处理
#### 8-1 刷新图标缓存

更新后 TrollStore 桌面图标点击无法打开，请直接打开 TrollHelper（Tips）

点击 Refresh App Registrations 来刷新桌面图标缓存，当设备注销后 TrollStore 应该可以正常打开

**请继续按照下面的步骤解锁 Tips，要不然你的 TrollHelper 可能后续无法安装 TrollStore**
#### 8-2 接下来打开 Filza 解除 Tips 锁定

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
