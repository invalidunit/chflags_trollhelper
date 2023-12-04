# Disable Updates

**终端运行**

	rm -rf /var/MobileSoftwareUpdate/MobileAsset/AssetsV2/* && chflags schg,schange,simmutable /var/MobileSoftwareUpdate/MobileAsset/AssetsV2
 
后续启用
	chflags noschg,noschange,nosimmutable /var/MobileSoftwareUpdate/MobileAsset/AssetsV2
 
