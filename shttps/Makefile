include $(TOPDIR)/rules.mk

PKG_NAME:=shttps
PKG_RELEASE:=3
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2022-03-06
PKG_SOURCE_VERSION:=c6c61976b41fe1356baae745ccff53932def08a6
PKG_SOURCE_URL:=https://github.com/fumiama/simple-http-server.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_DATE).tar.gz

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/shttps
  SECTION:=utils
  CATEGORY:=Server
  DEPENDS:=+libpthread
  TITLE:=shttps
  MAINTAINER:=fumiama
endef

define Package/shttps/description
 simple http server by Fumiama
endef

define Package/shttps/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/simple-http-server $(1)/usr/bin/shttps
endef

define Package/shttps/postinst
	#!/bin/sh
	chown 65534:65534 /usr/bin/shttps
	chmod 6755 /usr/bin/shttps
	exit 0
endef

define Package/shttps/postrm
	#!/bin/sh
	sed -i '/shttps/d' /etc/rc.local
	exit 0
endef

$(eval $(call BuildPackage,shttps))
