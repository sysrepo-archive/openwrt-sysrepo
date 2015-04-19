#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=sysrepod
PKG_VERSION:=2015-04-20
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_LICENSE:=GPL-2.0+
PKG_MAINTAINER:=Luka Perkov <luka.perkov@sartura.hr>

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sysrepo/sysrepod.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=ceb7c108dafc14176c69b68c4e5fa942893eb4b7
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/sysrepod
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=system repository daemon
  URL:=https://github.com/sysrepo/sysrepod
  DEPENDS:=+libstdcpp +libxml2
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) \
		AR="$(TARGET_CROSS)ar" \
		CC="$(TARGET_CC)" \
		CXX="$(TARGET_CXX)" \
		LIBXML2_INCLUDE_PATH="$(STAGING_DIR)/usr/include/libxml2" \
        all
endef

define Package/sysrepod/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) \
		$(PKG_BUILD_DIR)/sysrepod \
		$(1)/sbin/

	$(INSTALL_DIR) $(1)/etc/sysrepod
	$(INSTALL_CONF) \
		$(PKG_BUILD_DIR)/server/param \
		$(1)/etc/sysrepod/
	$(INSTALL_CONF) \
		$(PKG_BUILD_DIR)/server/deviceConfig.xml \
		$(1)/etc/sysrepod/
endef

$(eval $(call BuildPackage,sysrepod))
