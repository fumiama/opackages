include $(TOPDIR)/rules.mk

PKG_NAME:=simple-kanban-server
PKG_RELEASE:=3
CMAKE_INSTALL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2022-03-06
PKG_SOURCE_VERSION:=1ae1138496e545e6a85b8ca55d2f8ede4ccd82b0
PKG_SOURCE_URL:=https://github.com/fumiama/simple-kanban.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_SOURCE_DATE).tar.gz

PKG_MAINTAINER:=Fumiama <nbd@nbd.name>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING

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
