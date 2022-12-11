include $(TOPDIR)/rules.mk

PKG_NAME:=simple-kanban
PKG_RELEASE:=4
PKG_VERSION:=4.0.1
CMAKE_INSTALL:=1

# PKG_SOURCE_PROTO:=git
# PKG_SOURCE_DATE:=2022-11-25
# PKG_SOURCE_VERSION:=861c03b12ceaa5f5d7feb4fe7e487dbe2d721af0
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/fumiama/simple-kanban/tar.gz/$(PKG_VERSION)?
PKG_HASH:=405507bfaf9889439806e8e9cc0fc87896d80663e31da8e24ab09283f52680d2

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/simple-kanban-server
  SECTION:=utils
  CATEGORY:=Server
  DEPENDS:=+libpthread +libspb
  TITLE:=simple-kanban-server
  MAINTAINER:=fumiama
endef

define Package/simple-kanban-server/description
 simple-kanban-server
endef

define Package/simple-kanban-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/simple-kanban $(1)/usr/bin/
endef

define Package/simple-kanban-server/postinst
	#!/bin/sh
	chown 65534:65534 /usr/bin/simple-kanban
	chmod 6755 /usr/bin/simple-kanban
	sed -i '/exit 0/d' /etc/rc.local
	sed -i '/simple-kanban/d' /etc/rc.local
	mkdir -p /home/nobody
	chown 65534:65534 /home/nobody
	echo "#/usr/bin/simple-kanban -d 12315 1 /home/nobody/kanban /home/nobody/data /home/nobody/cfg.sp 2>&1 > /dev/null" >> /etc/rc.local
	echo "exit 0" >> /etc/rc.local
	exit 0
endef

define Package/simple-kanban-server/postrm
	#!/bin/sh
	sed -i '/simple-kanban-server/d' /etc/rc.local
	exit 0
endef

$(eval $(call BuildPackage,simple-kanban-server))
