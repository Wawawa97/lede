#
# Copyright (C) 2015-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=v2ray
PKG_VERSION:=v3.12
#PKG_VERSION:=$(shell wget https://api.github.com/repos/v2ray/v2ray-core/releases/latest -q -O -|grep tag_name|awk {'print $2'}|cut -d '"' -f 2)
#PKG_RELEASE:=$(shell wget https://api.github.com/repos/v2ray/v2ray-core/releases/latest -q -O -|grep published_at|awk {'print $2'}|cut -d '"' -f 2|cut -d 'T' -f 1)
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

ifeq ($(ARCH),x86_64)
	PKG_ARCH_V2RAY:=linux-64
endif
ifeq ($(ARCH),mipsel)
	PKG_ARCH_V2RAY:=linux-mipsle
endif
ifeq ($(ARCH),mips)
	PKG_ARCH_V2RAY:=linux-mips
endif
ifeq ($(ARCH),i386)
	PKG_ARCH_V2RAY:=linux-32
endif
ifeq ($(ARCH),arm)
	PKG_ARCH_V2RAY:=linux-arm
endif
ifeq ($(ARCH),aarch64)
	PKG_ARCH_V2RAY:=linux-arm64
endif
#PKG_SOURCE:=v2ray-$(PKG_ARCH_V2RAY).zip
#PKG_SOURCE_URL:=https://github.com/v2ray/v2ray-core/releases/download/$(PKG_VERSION)
#PKG_SOURCE_SUBDIR:=v2ray-$(PKG_VERSION)-$(V2RAY_PKG_ARCH)
#PKG_CAT:=unzip

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=net
	CATEGORY:=Network
	TITLE:=V2Ray is a cross-platform proxy software
	DEPENDS:=
	URL:=https://github.com/v2ray/v2ray-core
endef

define Package/$(PKG_NAME)/description
V2Ray is a cross-platform proxy software
endef

define Build/Prepare
	wget https://github.com/v2ray/v2ray-core/releases/download/$(PKG_VERSION)/v2ray-$(PKG_ARCH_V2RAY).zip -O $(PKG_BUILD_DIR)/v2ray-$(PKG_VERSION)-$(PKG_ARCH_V2RAY).zip
	unzip -o $(PKG_BUILD_DIR)/v2ray-$(PKG_VERSION)-$(PKG_ARCH_V2RAY).zip -d $(PKG_BUILD_DIR)
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin/v2ray
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/v2ray-$(PKG_VERSION)-$(PKG_ARCH_V2RAY)/v2ray $(1)/usr/bin/v2ray/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/v2ray-$(PKG_VERSION)-$(PKG_ARCH_V2RAY)/v2ctl $(1)/usr/bin/v2ray/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
