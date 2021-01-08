#
# Copyright (C) 2008-2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=pyarrow
PKG_VERSION:=0.9.0
PKG_RELEASE:=1

PKG_SOURCE:=apache-arrow-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/apache/arrow/archive/
PKG_MD5SUM:=c695a5ddc8d26c977b5ecd0c55212e900726953e
PKG_BUILD_DIR:=$(BUILD_DIR)/apache-arrow-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python3-setuptools python3-cython python3-arrow
PKG_LICENSE:=BSD

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)
$(call include_mk, python3-package.mk)

define Package/python3-$(PKG_NAME)
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-pandas
  URL:=http://pandas.pydata.org
  DEPENDS:=+python3 +python3-arrow
endef

define Package/python3-$(PKG_NAME)/description
  Powerful data structures for data analysis, time series, and statistics.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,python/,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python3-$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/$(PYTHON3_PKG_DIR)
	$(CP) $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* $(1)$(PYTHON3_PKG_DIR)/
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

$(eval $(call BuildPackage,python3-$(PKG_NAME)))
