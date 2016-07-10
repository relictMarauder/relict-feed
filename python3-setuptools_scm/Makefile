#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-setuptools_scm
PKG_VERSION:=1.11.1
PKG_RELEASE:=1

PKG_SOURCE:=setuptools_scm-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/84/aa/c693b5d41da513fed3f0ee27f1bf02a303caa75bbdfa5c8cc233a1d778c4
PKG_MD5SUM:=4d19b2bc9580016d991f665ac20e2e8f
PKG_BUILD_DIR:=$(BUILD_DIR)/python3-setuptools_scm-$(PKG_VERSION)
PKG_UNPACK=tar -C $(PKG_BUILD_DIR)  --strip 1 -xzvf $(DL_DIR)/$(PKG_SOURCE)


PKG_BUILD_DEPENDS:=python3 python3-setuptools 

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Ronny Pfannschmidt


include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

#TARGET_CFLAGS += -I$(STAGING_DIR)/opt/include/fuse
define Package/python3-setuptools_scm
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python3-setuptools_scm
	URL:=https://github.com/pypa/setuptools_scm/
	DEPENDS:=+python3 +python3-setuptools
endef

define Package/python3-setuptools_scm/description
the blessed package to manage your versions by scm tags

setuptools_scm handles managing your python package versions in scm metadata instead of declaring them as the version argument or in a scm managed file.

It also handles file finders for the supported scm’s.
endef


define Build/Compile
	$(call Build/Compile/Py3Mod,,\
		install --root="$(PKG_INSTALL_DIR)" --prefix="/opt" \
		--single-version-externally-managed \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(PYTHON3_LIB_DIR)
	$(CP) \
		$(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
		$(PYTHON3_LIB_DIR)
endef

$(eval $(call Py3Package,python3-setuptools_scm))
$(eval $(call BuildPackage,python3-setuptools_scm))
