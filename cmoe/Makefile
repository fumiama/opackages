include $(TOPDIR)/rules.mk

PKG_NAME:=cmoe
PKG_RELEASE:=4
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2022-03-05
PKG_SOURCE_VERSION:=6c21890f632f7a1f29cc84273460cc24526143af
PKG_SOURCE_URL:=https://github.com/fumiama/CMoe-Counter.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_DATE).tar.gz

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/cmoe
  SECTION:=utils
  CATEGORY:=Server
  DEPENDS:=+libspb
  TITLE:=cmoe
  MAINTAINER:=fumiama
endef

define Package/cmoe/description
 a simple http server cgi by Fumiama
endef

define Package/cmoe/install
	$(INSTALL_DIR) $(1)/usr/share/cmoe
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/cmoe $(1)/usr/share/cmoe/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/assets/index.html $(1)/usr/share/cmoe/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/assets/favicon.ico $(1)/usr/share/cmoe/
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/assets/style.css $(1)/usr/share/cmoe/
endef

define Package/cmoe/postinst
	#!/bin/sh
	chown 65534:65534 /usr/share/cmoe
	chown 65534:65534 /usr/share/cmoe/*
	chmod 6755 /usr/share/cmoe/cmoe
	sed -i '/exit 0/d' /etc/rc.local
	sed -i '/cmoe/d' /etc/rc.local
	echo "#/usr/bin/shttps -d 42412 /usr/share/cmoe/ 2>&1 > /dev/null" >> /etc/rc.local
	echo "exit 0" >> /etc/rc.local
	exit 0
endef

define Package/cmoe/postrm
	#!/bin/sh
	sed -i '/cmoe/d' /etc/rc.local
	exit 0
endef

$(eval $(call BuildPackage,cmoe))
