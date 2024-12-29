# Copyright (C) 2025 GitHub 
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=mysettings

PKG_RELEASE:=$(COMMITCOUNT)
PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=luci
  CATEGORY:=LuCI
  TITLE:=LuCI support for My X86 Default Settings
  PKGARCH:=all
  DEPENDS:=+luci-base +luci +@LUCI_LANG_zh-cn +@LUCI_LANG_zh_Hans +@LUCI_LANG_en
endef

define Package/$(PKG_NAME)/description
	Language Support Packages.
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/my-default-settings $(1)/etc/uci-defaults/99-default-settings
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/i18n
	po2lmo ./po/zh-cn/default.po $(1)/usr/lib/lua/luci/i18n/default.zh-cn.lmo
	$(INSTALL_DIR) $(1)/usr/share/linshi
	$(INSTALL_CONF) ./files/dhcp $(1)/usr/share/linshi/dhcp
	$(INSTALL_CONF) ./files/shadowsocksr $(1)/usr/share/linshi/shadowsocksr
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
