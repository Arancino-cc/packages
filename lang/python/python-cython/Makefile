#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=Cython
PKG_RELEASE:=2

PKG_VERSION:=0.29.21
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/6c/9f/f501ba9d178aeb1f5bf7da1ad5619b207c90ac235d9859961c11829d0160/
PKG_MD5SUM:=12c5e45af71dcc6dff28cdcbcbef6f39

PKG_SOURCE:=Cython-$(PKG_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/Cython-$(PKG_VERSION)
HOST_BUILD_DIR:=$(BUILD_DIR_HOST)/Cython-$(PKG_VERSION)

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)
$(call include_mk, python-host.mk)

PKG_BUILD_DEPENDS:=python

HOST_PKG_BUILD_DEPENDS:=python/host

define Package/python-cython
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Cython for python3
  URL:=http://www.pypi.org
  DEPENDS:=+python
endef

define Package/python-cython/description
	The Cython compiler for writing C extensions for the Python language.
endef

define PyPackage/python-cython/filespec
+|$(PYTHON_PKG_DIR)
endef

define Build/Compile
	# <--no-cython-compile> required, otherwise setup.py calls the target-gcc to create so-files which obviously can't be used by <python> on the host system.
	$(call Build/Compile/PyMod,,install --no-cython-compile --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Host/Compile
	# <--no-cython-compile> required, otherwise setup.py calls the target-gcc to create so-files which obviously can't be used by <python> on the host system.
	$(call Build/Compile/HostPyMod,,install --no-cython-compile --prefix="" --root="$(STAGING_DIR_HOSTPKG)")
endef

define Build/InstallDev
	$(INSTALL_DIR) $(STAGING_DIR)/$(PYTHON3_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(STAGING_DIR)/$(PYTHON_PKG_DIR)
endef

$(eval $(call HostBuild))

$(eval $(call PyPackage,python-cython))
$(eval $(call BuildPackage,python-cython))
