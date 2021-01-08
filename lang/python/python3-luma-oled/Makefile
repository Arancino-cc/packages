#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=luma.oled
PKG_VERSION:=2.5.1
PKG_RELEASE:=1
PKG_LICENSE:=BSD-2-Clause

PKG_SOURCE:=$(PKG_VERSION).zip
#PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/b5/a1/3de5a2d35fc34939672f4e1bd7d68cca359a31b76926f00d95f434c63aaa
PKG_SOURCE_URL:=https://github.com/rm-hull/luma.oled/archive/
PKG_MD5SUM:=a6a60ea4bb7e643bb609b8c9f8f620597ec94e32
#PKG_BUILD_DEPENDS:=libcap

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

PKG_UNPACK:=unzip -q -d $(PKG_BUILD_DIR) $(DL_DIR)/$(PKG_SOURCE); mv $(PKG_BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/* $(PKG_BUILD_DIR); rm -rf $(PKG_BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
HOST_UNPACK:=unzip -q -d $(PKG_BUILD_DIR) $(DL_DIR)/$(PKG_SOURCE); 


define Package/python3-$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-apsw
  URL:=https://github.com/rm-hull/luma.oled/
  DEPENDS:=+python3
endef

define Package/python3-$(PKG_NAME)/description
Python module to drive a SSD1306 / SSD1322 / SSD1325 / SSD1327 / SSD1331 / SSD1351 / SH1106 OLED https://luma-oled.readthedocs.io
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python3-$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/$(PYTHON3_PKG_DIR)
	$(CP) $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* $(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,python3-$(PKG_NAME)))
