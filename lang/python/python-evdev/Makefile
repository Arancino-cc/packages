#
# Copyright (C) 2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=python-evdev
PKG_VERSION:=0.7.0
PKG_RELEASE:=1

PKG_LICENSE:=BSD-3-Clause
PKG_MAINTAINER:=Paulo Costa <me@paulo.costa.nom.br>, Alexandru Ardelean <ardeleanalex@gmail.com>

PKG_SOURCE:=evdev-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/67/15/eac376f3e1fc1960a54439c21459b2582e68340001aff83b4ace9e5bd110
PKG_HASH:=57edafc469a414f58b51af1bfb9ee2babb9f626dd2df530d71c1176871850aa1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(BUILD_VARIANT)-evdev-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python-evdev
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  URL:=https://github.com/gvalkov/python-evdev
  TITLE:=python-evdev
  DEPENDS:= \
     +PACKAGE_python-evdev:python-light \
     +PACKAGE_python-evdev:python-ctypes
  VARIANT:=python
endef

define Package/python-evdev/description
	Bindings to the Linux input handling subsystem
endef

define Build/Compile
	$(call Build/Compile/PyMod,, build \
		build_ecodes  --evdev-headers="$(LINUX_DIR)/include/uapi/linux/input.h:$(LINUX_DIR)/include/uapi/linux/input-event-codes.h" \
		build_ext \
		install --root="$(PKG_INSTALL_DIR)" --prefix="/usr")
endef

$(eval $(call PyPackage,python-evdev))
$(eval $(call BuildPackage,python-evdev))
