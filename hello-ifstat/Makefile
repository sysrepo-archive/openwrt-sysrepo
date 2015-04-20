#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hello-ifstat
PKG_VERSION:=2015-04-20
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_LICENSE:=GPL-2.0+
PKG_MAINTAINER:=Luka Perkov <luka.perkov@sartura.hr>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sysrepo/hello-ifstat.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=97ac44262f3018e3de664f6bf372a9f4b6cff683
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/hello-ifstat
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=system repository daemon
  URL:=https://github.com/sysrepo/hello-ifstat
  DEPENDS:=+libroxml +libxml2
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		CC="$(TARGET_CC)" \
		LIBXML2_INCLUDE_PATH="$(STAGING_DIR)/usr/include/libxml2" \
        all
endef

define Package/hello-ifstat/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) \
		$(PKG_BUILD_DIR)/ifstat \
		$(1)/sbin/hello-ifstat
endef

$(eval $(call BuildPackage,hello-ifstat))
