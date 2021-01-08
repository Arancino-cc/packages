#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=arrow
PKG_VERSION:=0.12.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/e0/86/4eb5228a43042e9a80fe8c84093a8a36f5db34a3767ebd5e1e7729864e7b
PKG_MD5SUM:=a558d3b7b6ce7ffc74206a86c147052de23d3d4ef0e17c210dd478c53575c4cd
PKG_BUILD_DIR:=$(BUILD_DIR)/arrow-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3-setuptools
PKG_LICENSE:=BSD


HOST_PYTHON3_PACKAGE_BUILD_DEPENDS:="dev"

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-host.mk)
$(call include_mk, python3-package.mk)

define Package/python3-$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-arrow
  URL:=http://pandas.pydata.org
  DEPENDS:=+python3 +python3-numpy +python3-dateutil +python3-pytz +libstdcpp
endef

define Package/python3-$(PKG_NAME)/description
  Powerful data structures for data analysis, time series, and statistics.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python3-$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/$(PYTHON3_PKG_DIR)
	$(CP) $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* $(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

define Host/Compile
  $(call Build/Compile/HostPy3Mod,,install --prefix="" --root="$(STAGING_DIR_HOSTPKG)")
endef

define Host/Install
endef

$(eval $(call HostBuild))
$(eval $(call Py3Package,python3-$(PKG_NAME)))
$(eval $(call BuildPackage,python3-$(PKG_NAME)))
