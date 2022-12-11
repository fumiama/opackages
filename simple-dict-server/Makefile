include $(TOPDIR)/rules.mk

PKG_NAME:=simple-dict
PKG_RELEASE:=10
PKG_VERSION:=10.0.0
CMAKE_INSTALL:=1

# PKG_SOURCE_PROTO:=git
# PKG_SOURCE_DATE:=2022-10-28
# PKG_SOURCE_VERSION:=14d4aeda4cf9671808aa4251489c783d58f116bf
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/fumiama/simple-dict/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=701d5a265fa5915906e18548982e702b4e31d409673ccb0b48f9895cb4df2e1d

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/simple-dict-server
  SECTION:=utils
  CATEGORY:=Server
  DEPENDS:=+libpthread +libspb +libscrypto
  TITLE:=simple-dict-server
  MAINTAINER:=fumiama
endef

define Package/simple-dict-server/description
 simple-dict-server
endef

define Package/simple-dict-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/simple-dict-server $(1)/usr/bin/
endef

define Package/simple-dict-server/postinst
	#!/bin/sh
	chown 65534:65534 /usr/bin/simple-dict-server
	chmod 6755 /usr/bin/simple-dict-server
	sed -i '/exit 0/d' /etc/rc.local
	sed -i '/simple-dict-server/d' /etc/rc.local
	mkdir -p /home/nobody
	chown 65534:65534 /home/nobody
	echo "#/usr/bin/simple-dict-server -d 8000 /home/nobody/dict.sp /home/nobody/cfg.sp 2>&1 > /dev/null" >> /etc/rc.local
	echo "exit 0" >> /etc/rc.local
	exit 0
endef

define Package/simple-dict-server/postrm
	#!/bin/sh
	sed -i '/simple-dict-server/d' /etc/rc.local
	exit 0
endef

$(eval $(call BuildPackage,simple-dict-server))
