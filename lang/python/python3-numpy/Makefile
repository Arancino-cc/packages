#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=numpy
PKG_RELEASE:=1

PKG_VERSION:=1.12.1
PKG_SOURCE_URL:=https://pypi.python.org/packages/a5/16/8a678404411842fe02d780b5f0a676ff4d79cd58f0f22acddab1b392e230/
PKG_MD5SUM:=c75b072a984028ac746a6a332c209a91
#PKG_VERSION:=1.14.3
#PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/b0/2b/497c2bb7c660b2606d4a96e2035e92554429e139c6c71cdff67af66b58d2
#PKG_MD5SUM:=9016692c7d390f9d378fc88b7a799dc9caa7eb938163dda5276d3f3d6f75debf

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).zip

HOST_PYTHON3_PACKAGE_BUILD_DEPENDS:="dev"

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-host.mk)
$(call include_mk, python3-package.mk)

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
