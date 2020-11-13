#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-can
PKG_RELEASE:=1

PKG_VERSION:=2.1.0
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/04/87/0d5b0f2f4e5d7f64a44f74b7f0bc1668457e6aa7e90b04ad15c3b9a44411
PKG_MD5SUM:=4a5c01dd67feeda35f88e6c12ea14ac8cabd426b9be0cc5f9fd083fe90a9dbfc
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

HOST_PYTHON3_PACKAGE_BUILD_DEPENDS:="dev"

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-host.mk)
$(call include_mk, python3-package.mk)

define Package/python3-can
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-can
  DEPENDS:=+python3
endef

define Package/python3-can/description
  NumPy is the fundamental package for scientific computing with Python.
endef

define PyPackage/python3-can/filespec
+|$(PYTHON_PKG_DIR)
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Host/Compile
	$(call Build/Compile/HostPy3Mod,,install --prefix="" --root="$(STAGING_DIR_HOSTPKG)")
endef

define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR)/$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(STAGING_DIR)/$(PYTHON_PKG_DIR)
endef

define Host/Install
endef

$(eval $(call HostBuild))

$(eval $(call Py3Package,python3-can))
$(eval $(call BuildPackage,python3-can))
