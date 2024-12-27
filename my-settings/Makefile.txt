#
# Copyright (C) 2025 GitHub 
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=my-settings
PKG_VERSION:=1
PKG_RELEASE:=1
PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/mypackage/my-settings
  SECTION:=luci
  CATEGORY:=LuCI
  TITLE:=LuCI support for My X86 Default Settings
  PKGARCH:=all
  DEPENDS:=+luci-base +luci +@LUCI_LANG_zh_Hans +libev +libnetsnmp +libpam +liblzma +curl +v2ray-geoip +v2ray-geosite +tcpproxy +openssh-sftp-avahi-service +openssh-sftp-client +openssh-sftp-server +openvpn-easy-rsa +openvpn-openssl +tailscale +microsocks +6in4 +6to4 +adblock +sing-box +v2ray-core +xray-core +unzip +nano +vim +qrencode +luci +luci-nginx +luci-compat +luci-proto-wireguard +luci-app-acme +acme +acme-acmesh +acme-acmesh-dnsapi +acme-common +luci-app-banip +luci-app-cloudflared +luci-app-ddns +ddns-scripts +ddns-scripts-cloudflare +ddns-scripts-gcp +ddns-scripts-utils +luci-app-hd-idle +luci-app-mwan3 +luci-app-nlbwmon +luci-app-openvpn +luci-app-p910nd +luci-app-upnp +kmod-lp +kmod-usb-printer +kmod-tcp-bbr +shadowsocks-libev-ss-rules +shadowsocks-libev-ss-tunnel +v2raya +luci-app-smartdns +luci-app-sshtunnel +luci-app-tor +luci-app-ttyd +luci-app-uhttpd +luci-app-accesscontrol +luci-app-adguardhome +luci-app-gost +luci-app-homeproxy +luci-app-openclash +luci-app-parentcontrol +luci-app-passwall +luci-app-ssr-plus +luci-app-tailscale +luci-app-turboacc +luci-app-vlmcsd +luci-app-wolplus +kmod-nf-conntrack-timeout

endef

define Package/mypackage/my-settings/description
    Language Support Packages.
endef

define Build/Compile
endef

define Package/mypackage/my-settings/install
    $(INSTALL_DIR) $(1)/etc/uci-defaults
    $(INSTALL_BIN) ./files/my-default-settings $(1)/etc/uci-defaults/99-my-settings
    
    $(INSTALL_DIR) $(1)/usr/share/linshi
    $(INSTALL_CONF) ./files/dhcp $(1)/usr/share/linshi/
    $(INSTALL_CONF) ./files/shadowsocksr $(1)/usr/share/linshi/

endef

$(eval $(call BuildPackage,my-settings))
