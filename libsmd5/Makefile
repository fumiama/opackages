#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=simple-crypto
PKG_RELEASE:=2
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2021-12-11
PKG_SOURCE_VERSION:=634b4c14261a6c857d7fbb7c1bd99729c2df07d8
PKG_SOURCE_URL:=https://github.com/fumiama/simple-crypto.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_DATE).tar.gz

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libscrypto
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Simple crypto library
  URL:=https://github.com/fumiama/simple-crypto
endef

define Package/libscrypto/description
 This package contains a library for simple-* apps.
endef

define Package/libscrypto/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libscrypto.so $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/simplecrypto.h $(1)/usr/include/
	
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libscrypto.so $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libscrypto))
