#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=etaprogress
PKG_VERSION:=1.1.1
PKG_RELEASE:=1

PKG_SOURCE:=etaprogress-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/9c/53/b9696f50f491ff0ab27984714c8b37c2ee58eac45ecdf8d060f17f9aafe4
PKG_HASH:=9fe72db81b04792155081d4710acf65140e7c59df48d51b8d309ba7a24ab3a91
PKG_BUILD_DIR:=$(BUILD_DIR)/etaprogress-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3-setuptools
#PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python3-etaprogress
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=MQTT Python client library
	URL:=http://www.eclipse.org/paho/
	DEPENDS:=+python3
endef

define Package/python3-etaprogress/description
 This code provides a client class which enable applications to connect to an MQTT broker to publish messages, 
 and to subscribe to topics and receive published messages. It also provides some helper functions to make publishing 
 one off messages to an MQTT server very straightforward.
endef

#define Build/Configure
#endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python3-etaprogress/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,python3-etaprogress))
