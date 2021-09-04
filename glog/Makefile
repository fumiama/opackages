#
# Copyright (C) 2017 Steven Hessing
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libglog
PKG_RELEASE:=1
PKG_VERSION:=0.4.0
PKG_MAINTAINER:= Google

PKG_REV:=96a2f23dca4cc7180821ca5f32e526314395d26a
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/google/glog.git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

CMAKE_INSTALL:=1
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libglog
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=libglog 
	URL:=https://github.com/google/glog
	DEPENDS:=+libstdcpp
endef

define Package/libglog/description
	libglog
endef

define Build/InstallDev
    $(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,libglog))
