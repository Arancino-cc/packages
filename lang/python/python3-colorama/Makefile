#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=colorama
PKG_VERSION:=0.3.9
PKG_RELEASE:=1

PKG_SOURCE:=colorama-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/e6/76/257b53926889e2835355d74fec73d82662100135293e17d382e2b74d1669
PKG_HASH:=48eb22f4f8461b1df5734a074b57042430fb06e1d61bd1e11b078c0fe6d7a1f1
PKG_BUILD_DIR:=$(BUILD_DIR)/colorama-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3-setuptools
#PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-colorama
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=MQTT Python client library
	URL:=http://www.eclipse.org/paho/
	DEPENDS:=+python3
endef

define Package/python3-colorama/description
 This code provides a client class which enable applications to connect to an MQTT broker to publish messages, 
 and to subscribe to topics and receive published messages. It also provides some helper functions to make publishing 
 one off messages to an MQTT server very straightforward.
endef

#define Build/Configure
#endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python3-colorama/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,python3-colorama))
