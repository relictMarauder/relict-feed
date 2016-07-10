#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-borg
PKG_VERSION:=1.0.3
PKG_RELEASE:=1

PKG_SOURCE:=borgbackup-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/c9/c6/1efc338724b054d4d264dfeadfcba11cefa6c3c50f474cec91b8f0c21d3a
PKG_MD5SUM:=94b81bdba533d1f9f70785cd8c2234a0
PKG_BUILD_DIR:=$(BUILD_DIR)/python3-borg-$(PKG_VERSION)
PKG_UNPACK=tar -C $(PKG_BUILD_DIR)  --strip 1 -xzvf $(DL_DIR)/$(PKG_SOURCE)


PKG_BUILD_DEPENDS:=python3 python-pyopenssl python3-setuptools python3-setuptools_scm python3-llfuse liblz4 libacl

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Thomas Waldmann


include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

#TARGET_CFLAGS += -I$(STAGING_DIR)/opt/include/fuse
define Package/python3-borg
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python3-borg
	URL:=https://borgweb.readthedocs.io
	DEPENDS:=+python3 +python-pyopenssl +python3-setuptools +python3-setuptools_scm +python3-llfuse +liblz4 +libacl       
endef

define Package/python3-borg/description
BorgBackup (short: Borg) is a deduplicating backup program. Optionally, it supports compression and authenticated encryption.
endef


define Build/Compile
	$(call Build/Compile/Py3Mod,, install --prefix="/opt" --root="$(PKG_INSTALL_DIR)",BORG_OPENSSL_PREFIX="$(STAGING_DIR)/opt" BORG_LZ4_PREFIX="$(STAGING_DIR)/opt" )
endef


$(eval $(call Py3Package,python3-borg))
$(eval $(call BuildPackage,python3-borg))
