include $(TOPDIR)/rules.mk

PKG_NAME:=simple-crypto
PKG_RELEASE:=4
PKG_VERSION:=4
CMAKE_INSTALL:=1

# PKG_SOURCE_PROTO:=git
# PKG_SOURCE_DATE:=2022-10-15
# PKG_SOURCE_VERSION:=4b09328d0cf4f04a3f340ec6f53baedbbdbf3252
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/fumiama/simple-crypto/tar.gz/$(PKG_VERSION)?
PKG_HASH:=d1053d004744dcdbc486500a857c84115cb7f6096958dc6d7bde207b9402848b

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

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
