#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-paho-mqtt
PKG_VERSION:=1.3.1
PKG_RELEASE:=1

PKG_SOURCE:=paho-mqtt-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/2a/5f/cf14b8f9f8ed1891cda893a2a7d1d6fa23de2a9fb4832f05cef02b79d01f
PKG_HASH:=31911f6031de306c27ed79dc77b690d7c55b0dcb0f0434ca34ec6361d0371122
PKG_BUILD_DIR:=$(BUILD_DIR)/paho-mqtt-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3-setuptools
#PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk
include ../python3-package.mk

define Package/python-paho-mqtt
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=MQTT Python client library
	URL:=http://www.eclipse.org/paho/
	DEPENDS:=+python3
endef

define Package/python3-paho-mqtt
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=MQTT Python client library
	URL:=http://www.eclipse.org/paho/
	DEPENDS:=+python3
endef

define Package/python-paho-mqtt/description
 This code provides a client class which enable applications to connect to an MQTT broker to publish messages, 
 and to subscribe to topics and receive published messages. It also provides some helper functions to make publishing 
 one off messages to an MQTT server very straightforward.
endef

define Package/python3-paho-mqtt/description
 This code provides a client class which enable applications to connect to an MQTT broker to publish messages, 
 and to subscribe to topics and receive published messages. It also provides some helper functions to make publishing 
 one off messages to an MQTT server very straightforward.
endef

#define Build/Configure
#endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-paho-mqtt/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
#	$(CP) $(PKG_BUILD_DIR)/paho-mqtt.py $(1)$(PYTHON3_PKG_DIR)
endef

define Package/python3-paho-mqtt/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,python3-paho-mqtt))
