include $(TOPDIR)/rules.mk

PKG_NAME:=libbs
PKG_VERSION:=1
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/libbs-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/andersthomson/libbs.git
PKG_SOURCE_VERSION=c59b0b44e29307335fd561ba954ac360d31c95f5
PKG_MIRROR_HASH=650c9f946cef67b71a40cdddbfb6152daac70d1d54845755c003ad0214dc7f00
PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/libbs
  SECTION:=base
  CATEGORY:=Utilities
  TITLE:=LibBS, C API for talking to BlinkSticks
  #DESCRIPTION:=This variable is obsolete. use the Package/name/description define instead!
  URL:=https://github.com/thejk/libbs
  DEPENDS:=+libusb-1.0
endef

define Package/libbs/description
        LibBS, C API for talking to BlinkSticks

        Supports BlinkStick, BlinkStick Pro and BlinkStick Strip/Square but I've only
        tested the last one as of yet.

        A work in progress but seems to work fairly well
endef

define Build/Configure
  $(call Build/Configure/Default,--with-linux-headers=$(LINUX_DIR))
endef

define Package/libbs/install
        $(INSTALL_DIR) $(1)/usr/bin
        $(INSTALL_DIR) $(1)/usr/lib
        $(INSTALL_BIN) $(PKG_BUILD_DIR)/src/.libs/bs $(1)/usr/bin/
        $(INSTALL_DATA) $(PKG_BUILD_DIR)/src/.libs/libbs.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libbs))
