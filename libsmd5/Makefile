#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=simple-md5
PKG_RELEASE:=1.0
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2021-06-01
PKG_SOURCE_VERSION:=bd25ddf9f6fac93bc768611ec223bf517b29b689
PKG_SOURCE_URL:=https://github.com/fumiama/simple-md5-lib.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_DATE).tar.gz

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libsmd5
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Simple md5 library
  URL:=https://github.com/fumiama/simple-md5-lib
endef

define Package/libsmd5/description
 This package contains a library for simple-* apps.
endef

define Package/libsmd5/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsmd5.so $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/simplemd5.h $(1)/usr/include/
	
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsmd5.so $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libsmd5))
