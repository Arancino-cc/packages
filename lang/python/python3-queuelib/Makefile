#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=queuelib
PKG_VERSION:=1.5.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/a5/dc/1221b4c92f27e95388cdeff6412a02edaf531162b79c67b9a8431760d955
PKG_HASH:=42b413295551bdc24ed9376c1a2cd7d0b1b0fa4746b77b27ca2b797a276a1a17
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3-setuptools
#PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python3-queuelib
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=MQTT Python client library
	URL:=http://www.eclipse.org/paho/
	DEPENDS:=+python3
endef

define Package/python3-queuelib/description
 This code provides a client class which enable applications to connect to an MQTT broker to publish messages, 
 and to subscribe to topics and receive published messages. It also provides some helper functions to make publishing 
 one off messages to an MQTT server very straightforward.
endef

#define Build/Configure
#endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python3-queuelib/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,python3-queuelib))
