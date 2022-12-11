#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=simple-protobuf
PKG_RELEASE:=4
PKG_VERSION:=4
CMAKE_INSTALL:=1

# PKG_SOURCE_PROTO:=git
# PKG_SOURCE_DATE:=2022-05-06
# PKG_SOURCE_VERSION:=e23ac9b6c0ad5d18097fc5f64e48cf55dfddef1a
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/fumiama/simple-protobuf/tar.gz/$(PKG_VERSION)?
PKG_HASH:=a3319f6399882d83f6a0b088f7f4fad74374fdaf345d857a5efc702c293a88fd

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libspb
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Simple protobuf library
  URL:=https://github.com/fumiama/simple-protobuf
endef

define Package/libspb/description
 This package contains a library for simple-* apps.
endef

define Package/libspb/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libspb.so $(1)/usr/lib/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/simple_protobuf.h $(1)/usr/include/
	
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libspb.{a,so*} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libspb))
