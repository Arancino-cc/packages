#
# Copyright (C) 2015, 2017-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-parsley
PKG_VERSION:=1.3
PKG_RELEASE:=3

PKG_SOURCE:=Parsley-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/P/Parsley
PKG_HASH:=9444278d47161d5f2be76a767809a3cbe6db4db822f46a4fd7481d4057208d41

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-parsley-$(PKG_VERSION)

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-parsley
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  URL:=http://launchpad.net/parsley
  TITLE:=python-parsley
  DEPENDS:=+PACKAGE_python-parsley:python-light
  VARIANT:=python
endef

define Package/python-parsley/description
Parsing and pattern matching made easy.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix="/usr" --root="$(PKG_INSTALL_DIR)")
endef

$(eval $(call PyPackage,python-parsley))
$(eval $(call BuildPackage,python-parsley))
