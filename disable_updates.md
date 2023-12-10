# Disable Updates

**没越狱用户**

将下面命令复制到剪切板，然后使用 Filza 找到 /usr/bin/vm_stat 点击运行，然后粘贴下面命令并回车运行

	killall -9 softwareupdateservicesd & killall -9 softwareupdated & killall -9 com.apple.MobileSoftwareUpdate.CleanupPreparePathService & killall -9 Preferences & chflags -R noschg,noschange,nosimmutable '/var/MobileSoftwareUpdate/MobileAsset/' & mkdir -p '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && rm -rf '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && mkdir -p '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && chmod -R 0777 '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && chown -R mobile:mobile '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/' && chflags schg,schange,simmutable '/var/MobileSoftwareUpdate/MobileAsset/AssetsV2/'
 
后续重新启用请在 Filza 运行下面的命令

	chflags -R noschg,noschange,nosimmutable '/var/MobileSoftwareUpdate/MobileAsset/'

**已越狱用户**

请添加软件源

	https://invalidunit.github.io/repo/

安装 Disable Updates

后续重新启用直接卸载即可

**没越狱也没 TrollStore 的用户**

别看了洗洗睡吧
