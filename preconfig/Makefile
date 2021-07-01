include $(TOPDIR)/rules.mk

PKG_NAME:=preconfig
PKG_VERSION:=v1.0
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/preconfig
  SECTION:=system
  CATEGORY:=XUEGAONET
  TITLE:=Preconfig
  DEPENDS:=+luci-ssl-nginx +dnsmasq-full +luci-theme-bootstrap +luci-i18n-base-zh-cn +ttyd
  MAINTAINER:=Harris <i@xuegaogg.com>
  URL:=https://blog.xuegaogg.com/
endef

define Package/preconfig/description
	XUEGAONET Preconfig
endef

define Package/preconfig/install
	# install system config
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/system $(1)/etc/config
	$(INSTALL_CONF) ./files/dhcp $(1)/etc/config
	$(INSTALL_CONF) ./files/fstab $(1)/etc/config
	$(INSTALL_CONF) ./files/luci $(1)/etc/config
	
	# install sysctl config
	$(INSTALL_DIR) $(1)/etc/sysctl.d
	$(INSTALL_CONF) ./files/13-rp_filter.conf $(1)/etc/sysctl.d/13-rp_filter.conf
	
	# install nginx.conf
	$(INSTALL_DIR) $(1)/etc/nginx
	$(INSTALL_BIN) ./files/nginx.conf $(1)/etc/nginx
endef

define Build/Compile
	true
endef

$(eval $(call BuildPackage,preconfig))


