#
# Copyright (C) 2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-llfuse
PKG_VERSION:=1.1
PKG_RELEASE:=1

PKG_SOURCE:=llfuse-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://pypi.python.org/packages/bb/17/8f5d98f5f005cd041635fc6836ad8a91f92dea4d41459f13763f630924c6/
PKG_MD5SUM:=a11a1bc606511fe0933c3e3d41237f0e
PKG_CAT:=bzcat
PKG_BUILD_DIR:=$(BUILD_DIR)/python3-llfuse-$(PKG_VERSION)
PKG_UNPACK=$(PKG_CAT) $(DL_DIR)/$(PKG_SOURCE)| tar -C $(PKG_BUILD_DIR)  --strip 1 -xvf -
PKG_BUILD_DEPENDS:=python3 python3-setuptools fuse

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Nikolaus Rath


include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

TARGET_CFLAGS += -I$(STAGING_DIR)/opt/include/fuse
define Package/python3-llfuse
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python3-llfuse
	URL:=https://github.com/python-llfuse/python-llfuse
	DEPENDS:=+python3 +python3-setuptools +fuse +libfuse
        
endef

define Package/python3-llfuse/description
Python-LLFUSE is a set of Python bindings for the low level FUSE API. It requires at least FUSE 2.8.0 and supports both Python 2.x and 3.x. Like FUSE itself, Python-LLFUSE is developed for Linux systems. However, we try to maintain compatibility with OS-X, FreeBSD and NetBSD as well (but due to lack of pre-release testers we can’t guarantee that every Python-LLFUSE release will run on these platforms - please report any bugs and we will try to fix them).
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,, install --prefix="/opt" --root="$(PKG_INSTALL_DIR)")
endef

$(eval $(call Py3Package,python3-llfuse))
$(eval $(call BuildPackage,python3-llfuse))
