#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=Cython
PKG_RELEASE:=1

PKG_VERSION:=0.28.2
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/79/9d/dea8c5181cdb77d32e20a44dd5346b0e4bac23c4858f2f66ad64bbcf4de8
PKG_MD5SUM:=634e2f10fc8d026c633cffacb45cd8f4582149fa68e1428124e762dbc566e68a

PKG_SOURCE:=Cython-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/Cython-$(PKG_VERSION)
HOST_PKG_BUILD_DIR:=$(BUILD_DIR)/Cython-$(PKG_VERSION)

HOST_PYTHON3_PACKAGE_BUILD_DEPENDS:="dev"

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-numpy
  URL:=http://www.numpy.org
  DEPENDS:=+python3
endef

define Package/python3-$(PKG_NAME)/description
  NumPy is the fundamental package for scientific computing with Python.
endef

define PyPackage/python3-$(PKG_NAME)/filespec
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

$(eval $(call Py3Package,python3-$(PKG_NAME)))
$(eval $(call BuildPackage,python3-$(PKG_NAME)))
