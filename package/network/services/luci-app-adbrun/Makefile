include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-adbrun
PKG_VERSION:=20240331

include $(INCLUDE_DIR)/package.mk

define Package/luci-app-adbrun
 	SECTION:=luci
	CATEGORY:=LuCI
	SUBMENU:=3. Applications
	TITLE:=LuCI Support for adb
	PKGARCH:=all
	DEPENDS:=+adb
endef

define Package/luci-app-adbrun/description
	adb tool
endef

define Build/Compile
endef

define Package/luci-app-adbrun/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci
	cp -pR ./luasrc/* $(1)/usr/lib/lua/luci
	$(INSTALL_DIR) $(1)/usr/adbrun
	$(INSTALL_BIN) ./files/adbrun/* $(1)/usr/adbrun
	$(INSTALL_DIR) $(1)/usr/adbrun/input
	$(INSTALL_BIN) ./files/input/* $(1)/usr/adbrun/input
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/adbrun.conf $(1)/etc/config/adbrun
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/adbrun.init $(1)/etc/init.d/adbrun
	$(INSTALL_DIR) $(1)/etc/hotplug.d/usb
	$(INSTALL_BIN) ./files/hotplug $(1)/etc/hotplug.d/usb/30-adb_init
	$(INSTALL_DIR) $(1)/usr/share/rpcd/acl.d
	$(CP) ./files/luci-app-adbrun.json $(1)/usr/share/rpcd/acl.d
endef

$(eval $(call BuildPackage,luci-app-adbrun))
