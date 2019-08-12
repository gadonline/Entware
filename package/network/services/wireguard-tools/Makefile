include $(TOPDIR)/rules.mk

PKG_NAME:=wireguard-tools
PKG_VERSION:=0.0.20190406
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/WireGuard-$(PKG_VERSION)
PKG_SOURCE:=WireGuard-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://git.zx2c4.com/WireGuard/snapshot/
PKG_HASH:=2f06f3adf70b95e74a7736a22dcf6e9ef623b311a15b7d55b5474e57c3d0415b
MAKE_PATH:=src/tools

include $(INCLUDE_DIR)/package.mk

define Package/wireguard-tools
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=VPN
  TITLE:=WireGuard userspace control program (wg)
  URL:=https://www.wireguard.com
  DEPENDS:=+libmnl
endef

define Package/wireguard-tools/Default/description
  WireGuard is a novel VPN that runs inside the Linux Kernel and utilizes
  state-of-the-art cryptography. It aims to be faster, simpler, leaner, and
  more useful than IPSec, while avoiding the massive headache. It intends to
  be considerably more performant than OpenVPN.  WireGuard is designed as a
  general purpose VPN for running on embedded interfaces and super computers
  alike, fit for many different circumstances. It uses UDP.
endef

define Package/wireguard-tools/install
		$(INSTALL_DIR) $(1)/opt/sbin/
		$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/tools/wg $(1)/opt/sbin/
		$(INSTALL_BIN) ./files/wireguard_watchdog $(1)/opt/sbin/
		$(INSTALL_DIR) $(1)/opt/lib/netifd/proto/
		$(INSTALL_BIN) ./files/wireguard.sh $(1)/opt/lib/netifd/proto/
endef

$(eval $(call BuildPackage,wireguard-tools))