#
# Copyright (C) 2019 Daniel Engberg <daniel.engberg.lists@pyret.net>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=jsoncpp
PKG_VERSION:=1.9.4
PKG_RELEASE:=3

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/open-source-parsers/jsoncpp/tar.gz/$(PKG_VERSION)?
PKG_HASH:=e34a628a8142643b976c7233ef381457efad79468c67cb1ae0b83a33d7493999

PKG_MAINTAINER:=Jan Pavlinec <jan.pavlinec1@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=meson/host

include $(INCLUDE_DIR)/package.mk
include ../../devel/meson/meson.mk

HOSTCC=$(HOSTCC_NOCACHE)
HOSTCXX=$(HOSTCXX_NOCACHE)

define Package/jsoncpp
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=jsoncpp
  URL:=https://github.com/open-source-parsers/jsoncpp
  DEPENDS:=+libstdcpp
endef

define Package/jsoncpp/description
  JsonCpp is a C++ library that allows manipulating
  JSON values, including serialization and
  deserialization to and from strings. It can also
  preserve existing comment in
  unserialization/serialization steps, making it a
  convenient format to store user input files.
endef

MESON_ARGS += \
	-Db_lto=true \
	-Dtests=false

TARGET_LDFLAGS += -Wl,--gc-sections

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/json $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libjsoncpp.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/jsoncpp.pc $(1)/usr/lib/pkgconfig/
endef

define Package/jsoncpp/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libjsoncpp.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,jsoncpp))
