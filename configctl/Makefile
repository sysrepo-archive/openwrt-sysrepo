#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=configctl
PKG_VERSION:=2015-10-26
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_LICENSE:=Apache-2.0
PKG_MAINTAINER:=Luka Perkov <luka.perkov@sartura.hr>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sysrepo/configctl.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=2283defd1bdad583d84392b281844b3bd9936fa9
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libconfigctl
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=configctl library
  URL:=https://github.com/sysrepo/configctl
  DEPENDS:=+libpcre +libyang
endef

define Package/configctl
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=configctl utility
  URL:=https://github.com/sysrepo/configctl
  DEPENDS:=+libconfigctl
endef

CMAKE_OPTIONS = \
	-DCMAKE_INSTALL_PREFIX=/ \
	-DENABLE_BUILD_TESTS=OFF \
	-DENABLE_GIT=OFF

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/libconfigctl
	$(CP) \
		$(PKG_INSTALL_DIR)/include/libconfigctl/configctl.h \
		$(1)/usr/include/libconfigctl/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/lib/libconfigctl.so* \
		$(1)/usr/lib/
endef

define Package/libconfigctl/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/lib/libconfigctl.so* \
		$(1)/usr/lib/
endef

define Package/configctl/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/bin/configctl \
		$(1)/usr/bin/
endef

$(eval $(call BuildPackage,libconfigctl))
$(eval $(call BuildPackage,configctl))
