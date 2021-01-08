#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-pyserial
PKG_VERSION:=3.1.1
PKG_RELEASE:=1

PKG_SOURCE:=pyserial-$(PKG_VERSION).tar.gz
PPKG_SOURCE_URL:=http://pypi.python.org/packages/3c/d8/a9fa247ca60b02b3bebbd61766b4f321393b57b13c53b18f6f62cf172c08/
PKG_HASH:=d657051249ce3cbd0446bcfb2be07a435e1029da4d63f53ed9b4cdde7373364c
PKG_BUILD_DIR:=$(BUILD_DIR)/pyserial-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3-setuptools
#PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-pyserial
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=MQTT Python client library
	URL:=http://www.eclipse.org/paho/
	DEPENDS:=+python3
endef

define Package/python3-pyserial/description
 This code provides a client class which enable applications to connect to an MQTT broker to publish messages, 
 and to subscribe to topics and receive published messages. It also provides some helper functions to make publishing 
 one off messages to an MQTT server very straightforward.
endef

#define Build/Configure
#endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python3-pyserial/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,python3-pyserial))
