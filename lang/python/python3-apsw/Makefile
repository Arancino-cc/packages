#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=apsw
PKG_VERSION:=3.24.0
PKG_RELEASE:=1
PKG_LICENSE:=BSD-2-Clause

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-r1.zip
#PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/b5/a1/3de5a2d35fc34939672f4e1bd7d68cca359a31b76926f00d95f434c63aaa
PKG_SOURCE_URL:=https://github.com/rogerbinns/apsw/releases/download/$(PKG_VERSION)-r1/
PKG_MD5SUM:=0ad33cd6f7e556a377bfb45a2549167dfb3b910cbf3c0269791dd11c1440c2a8
#PKG_BUILD_DEPENDS:=libcap

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=unzip -q -d $(PKG_BUILD_DIR) $(DL_DIR)/$(PKG_SOURCE); mv $(PKG_BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)-r1/* $(PKG_BUILD_DIR); rm -rf $(PKG_BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)-r1
HOST_UNPACK:=unzip -q -d $(PKG_BUILD_DIR) $(DL_DIR)/$(PKG_SOURCE); 


define Package/python3-$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-apsw
  URL:=https://github.com/rogerbinns/apsw/
  DEPENDS:=+python3
endef

define Package/python3-$(PKG_NAME)/description
APSW is a Python wrapper for the SQLite embedded relational database engine. In contrast to other wrappers such as pysqlite it focuses on being a minimal layer over SQLite attempting just to translate the complete SQLite API into Python. The documentation has a section on the differences between APSW and pysqlite. APSW supports CPython 2.3 onwards and CPython 3.1 onwards.
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
