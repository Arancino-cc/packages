#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=smbus2
PKG_VERSION:=0.2.1
PKG_RELEASE:=1
PKG_LICENSE:=BSD-2-Clause

PKG_SOURCE:=$(PKG_VERSION).zip
#PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/b5/a1/3de5a2d35fc34939672f4e1bd7d68cca359a31b76926f00d95f434c63aaa
PKG_SOURCE_URL:=https://github.com/kplindegaard/smbus2/archive/
PKG_MD5SUM:=8d536877fdc1a58b8cacd1b4c800083e3f8db15a
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
  URL:=https://github.com/kplindegaard/smbus2
  DEPENDS:=+python3
endef

define Package/python3-$(PKG_NAME)/description
A drop-in replacement for smbus-cffi/smbus-python in pure Python 
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
