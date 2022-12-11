include $(TOPDIR)/rules.mk

PKG_NAME:=simple-crypto
PKG_RELEASE:=4
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2022-10-15
PKG_SOURCE_VERSION:=4b09328d0cf4f04a3f340ec6f53baedbbdbf3252
PKG_SOURCE_URL:=https://github.com/fumiama/simple-crypto.git
PKG_SOURCE:=https://github.com/fumiama/simple-crypto/archive/refs/tags/$(PKG_RELEASE).tar.gz

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
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libscrypto.{a,so*} $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libscrypto))
