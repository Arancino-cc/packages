#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=RPi.GPIO
PKG_VERSION:=0.6.5
PKG_RELEASE:=1
PKG_MAINTAINER:=Ben Croston <ben@croston.org>
PKG_LICENSE:=MIT
PKG_LICENSE_FILE=COPYING-MIT

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/af/2f/407b6e4cc8a0bdf434825a160bba1807991886b63cce16a5f1a6e1f24cdf/
PKG_HASH:=a4210ad63bfe844e43995286de0d3950dfacfa0f3799bb9392770ac54a7d2e47

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python-rpi-gpio
  CATEGORY:=Languages
  SECTION:=lang
  SUBMENU:=Python
  TITLE:=Python module interface to the Raspberry Pi GPIOs
  URL:=http://sourceforge.net/projects/raspberry-gpio-python/
  DEPENDS:=+python
endef

define Package/python-rpi-gpio/description
Python module interface to the Raspberry Pi GPIOs
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Package/python-rpi-gpio/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
		$(1)$(PYTHON_PKG_DIR)
endef

$(eval $(call BuildPackage,python-rpi-gpio))
