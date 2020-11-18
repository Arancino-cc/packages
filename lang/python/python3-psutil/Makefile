#
# Copyright (C) 2020 CZ.NIC, z. s. p. o. (https://www.nic.cz/)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=psutil
PKG_VERSION:=5.7.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/33/e0/82d459af36bda999f82c7ea86c67610591cf5556168f48fd6509e5fa154d/$(PKG_SOURCE)
PKG_MD5SUM:=b07a067e6a930608235f4e5d9b1f90f5

PKG_MAINTAINER:=Jan Pavlinec <jan.pavlinec@nic.cz>
PKG_LICENSE:=BSD 3-Clause
PKG_LICENSE_FILES:=LICENSE
	
PKG_BUILD_DEPENDS:=python3 python3-setuptools

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)
$(call include_mk, python3-host.mk)

define Package/python3-psutil
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=psutil (process and system utilities)
  URL:=https://github.com/giampaolo/psutil
  DEPENDS:=+python3-light
endef

define Package/python3-psutil/description
  psutil is a cross-platform library for retrieving information
  on running processes and system utilization.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,,install --prefix="/usr" --root="$(PKG_INSTALL_DIR)")
endef

define Host/Compile
	$(call Build/Compile/HostPyMod,,install --prefix="" --root="$(STAGING_DIR_HOST)")
endef

define Host/Install
endef

$(eval $(call HostBuild))

$(eval $(call Py3Package,python3-psutil))
$(eval $(call BuildPackage,python3-psutil))