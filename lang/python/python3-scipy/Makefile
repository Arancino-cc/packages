#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=scipy
PKG_RELEASE:=1

#PKG_VERSION:=1.1.0
#PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/07/76/7e844757b9f3bf5ab9f951ccd3e4a8eed91ab8720b0aac8c2adcc2fdae9f
#PKG_MD5SUM:=878352408424dffaa695ffedf2f9f92844e116686923ed9aa8626fc30d32cfd1
PKG_VERSION:=0.19.1
PKG_SOURCE_URL:=https://github.com/scipy/scipy/releases/download/v0.19.1
PKG_MD5SUM:=03b1092cf0e0bdebcbe98a44d289208a1e597416

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

HOST_PYTHON3_PACKAGE_BUILD_DEPENDS:="dev"

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python-host.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-scipy
  URL:=http://www.scipy.org
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

#$(eval $(call HostBuild))

#$(eval $(call Py3Package,python3-$(PKG_NAME)))
$(eval $(call BuildPackage,python3-$(PKG_NAME)))
