#
# Copyright (C) 2014-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-setuptools-scm
PKG_VERSION:=5.0.2
PKG_RELEASE:=1

PKG_SOURCE:=setuptools_scm-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/56/c9/09f4a531720b1bf54f316fdff926fbb937c59a9c4a34e3a533b26e501898/
PKG_MD5SUM:=8ddd44e0cd3a243350fe709024ec7224

PKG_LICENSE:=PSF

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-setuptools-scm-$(PKG_VERSION)
PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-setuptools-scm
	SUBMENU:=Python
	SECTION:=lang
	CATEGORY:=Languages
	TITLE:=Tool for installing Python $(PYTHON3_VERSION) packages.
	URL:=https://bitbucket.org/pypa/setuptools
	DEPENDS:=+python3 +python3-dev +python3-lib2to3 +python3-setuptools
	MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>
endef

define Package/python3-setuptools-scm/description
	Easily download, build, install, upgrade, and uninstall Python $(PYTHON3_VERSION) packages
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,\
		install --root="$(PKG_INSTALL_DIR)" --prefix="/usr" \
		--single-version-externally-managed \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(PYTHON3_LIB_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(PYTHON3_LIB_DIR)
endef

$(eval $(call Py3Package,python3-setuptools-scm))
$(eval $(call BuildPackage,python3-setuptools-scm))
