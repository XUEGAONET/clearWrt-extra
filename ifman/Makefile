#
# Copyright (C) 2018-2021 xuegao
#
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ifman
PKG_VERSION:=1.2.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/XUEGAONET/ifman.git

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=ifman
GO_PKG_LDFLAGS:=-s -w

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/ifman
  TITLE:=IfMan
  URL:=https://blog.xuegaogg.com
  SECTION:=system
  CATEGORY:=XUEGAONET
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-certificates
  MAINTAINER:=Harris <i@xuegaogg.com>
endef

define Package/ifman/description
  XUEGAONET IfMan
endef

define Build/Compile
	$(eval GO_PKG_BUILD_PKG:=$(GO_PKG)/cmd)
	$(call GoPackage/Build/Compile)
	mv -f $(GO_PKG_BUILD_BIN_DIR)/cmd $(GO_PKG_BUILD_BIN_DIR)/ifman
endef

define Package/ifman/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/ifman $(1)/bin

	# install init.d
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/ifman $(1)/etc/init.d

	# install config
	$(INSTALL_DIR) $(1)/etc/ifman
	$(INSTALL_CONF) ./files/config.sample.yaml $(1)/etc/ifman/config.yaml
endef

$(eval $(call GoBinPackage,ifman))
$(eval $(call BuildPackage,ifman))
