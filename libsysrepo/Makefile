#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libsysrepo
PKG_VERSION:=2015-04-20
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_LICENSE:=GPL-2.0+
PKG_MAINTAINER:=Luka Perkov <luka.perkov@sartura.hr>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sysrepo/libsysrepo.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=0869990f91799ce7043f2f30d0bba2bef5669772
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libsysrepo
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=sysrepo libraries
  URL:=https://github.com/sysrepo/libsysrepo
  DEPENDS:=+libroxml
endef

CMAKE_OPTIONS = \
	-DCMAKE_INSTALL_PREFIX=/ \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/sysrepo
	$(CP) \
		$(PKG_BUILD_DIR)/include/sysrepo/sysrepo.h \
		$(1)/usr/include/sysrepo/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_BUILD_DIR)/libsysrepo.so \
		$(1)/usr/lib/
endef

define Package/libsysrepo/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) \
		$(PKG_BUILD_DIR)/libsysrepo.so \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libsysrepo))
