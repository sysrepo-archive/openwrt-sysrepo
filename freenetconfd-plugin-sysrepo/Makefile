#
# Copyright (C) 2014-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=freenetconfd-plugin-sysrepo
PKG_VERSION:=2015-05-14
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_LICENSE:=GPL-2.0+
PKG_MAINTAINER:=Luka Perkov <luka.perkov@sartura.hr>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/freenetconf/freenetconfd-plugins.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=af2240288a7b4990fec198c52639f19d029a0417
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/freenetconfd-plugin-sysrepo
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=freenetconfd plugin for sysrepo
  URL:=http://www.freenetconf.org/
  DEPENDS:=+freenetconfd
endef

define Package/freenetconfd-plugin-sysrepo/install
	$(INSTALL_DIR) $(1)/usr/lib/freenetconfd
	$(CP) \
		$(PKG_BUILD_DIR)/lib/freenetconfd/sysrepo-ifstat.so \
		$(1)/usr/lib/freenetconfd/

	$(INSTALL_DIR) $(1)/etc/yang
	$(INSTALL_CONF) \
		$(PKG_BUILD_DIR)/sysrepo/yang/ifstat@2015-03-11.yang \
		$(1)/etc/yang/
endef

$(eval $(call BuildPackage,freenetconfd-plugin-sysrepo))
