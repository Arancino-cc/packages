#
# Copyright (C) 2008-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=PyYAML
PKG_VERSION:=3.12
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://pyyaml.org/download/pyyaml/
PKG_HASH:=592766c6303207a20efc445587778322d7f73b161bd994f227adaa341ba212ab

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=Nicolas Thill <nico@openwrt.org>

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-$(PKG_NAME)-$(PKG_VERSION)
PKG_UNPACK=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-yaml
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  URL:=http://pyyaml.org/wiki/PyYAML
  DEPENDS:=+libyaml
  TITLE:=YAML parser and emitter for Python3
  DEPENDS+=+PACKAGE_python3-yaml:python3-light +PACKAGE_python3-yaml:python3-codecs
  VARIANT:=python3
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,\
		--with-libyaml install --prefix="$(PKG_INSTALL_DIR)/usr" \
	)
endef

$(eval $(call Py3Package,python3-yaml))
$(eval $(call BuildPackage,python3-yaml))
