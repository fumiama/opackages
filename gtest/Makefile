#
# Copyright (C) 2017 Steven Hessing
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libgtest
PKG_RELEASE:=1
PKG_VERSION:=1.10.0
PKG_MAINTAINER:= Google

PKG_REV:=703bd9caab50b139428cea1aaff9974ebee5742e
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/google/googletest.git
PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

CMAKE_INSTALL:=1
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libgtest
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=libgtest 
	URL:=https://github.com/google/googletest
	DEPENDS:=+libstdcpp
endef

define Package/libgtest/description
	libgtest
endef

define Build/InstallDev
    $(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,libgtest))
