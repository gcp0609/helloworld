include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-ssr-plus
PKG_VERSION:=184
PKG_RELEASE:=9

PKG_CONFIG_DEPENDS:= \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Trojan \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Libev_Client \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Simple_Obfs \
	

	#CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Kcptun \
	#CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_NaiveProxy \
	#CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Redsocks2 \

	#CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Libev_Server \
	#CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Rust_Client \
	#CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Rust_Server \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Libev_Client \
	#CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Libev_Server \
	CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_V2ray_Plugin \
	#CONFIG_PACKAGE_$(PKG_NAME)_INCLUDE_Xray

LUCI_TITLE:=SS/Trojan interface
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+coreutils +coreutils-base64 +dns2socks +dnsmasq-full +ipset \
	+ip-full +iptables-mod-tproxy +lua +libuci-lua +microsocks +pdnsd-alt \
	+tcping +resolveip  +uclient-fetch \
	+ipt2socks \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Trojan:trojan \
	+PACKAGE_$(PKG_NAME)_INCLUDE_Simple_Obfs:simple-obfs \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Libev_Client:shadowsocks-libev-ss-redir \
	
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Trojan:ipt2socks \
	# +shadowsocksr-libev-ssr-check \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Libev_Client:shadowsocks-libev-ss-local \

	#+PACKAGE_$(PKG_NAME)_INCLUDE_Kcptun:kcptun-client \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_NaiveProxy:naiveproxy \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Redsocks2:redsocks2 \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Libev_Server:shadowsocks-libev-ss-server \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Rust_Client:shadowsocks-rust-sslocal \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Rust_Server:shadowsocks-rust-ssserver \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Libev_Client:shadowsocksr-libev-ssr-local \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Libev_Client:shadowsocksr-libev-ssr-redir \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Libev_Server:shadowsocksr-libev-ssr-server \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_V2ray_Plugin:v2ray-plugin \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Xray:curl \
	#+PACKAGE_$(PKG_NAME)_INCLUDE_Xray:xray-core

define Package/$(PKG_NAME)/config
menu "Include libustream-ssl"
	depends on PACKAGE_$(PKG_NAME)
	config PACKAGE_$(PKG_NAME)_INCLUDE_libustream-wolfssl
		bool "Include libustream-wolfssl"
		default y if DEFAULT_libustream-wolfssl
		select PACKAGE_libustream-wolfssl
	
	config PACKAGE_$(PKG_NAME)_INCLUDE_libustream-openssl
		depends on !PACKAGE_$(PKG_NAME)_INCLUDE_libustream-wolfssl
		bool "Include libustream-openssl"
		default y if DEFAULT_libustream-openssl
		select PACKAGE_libustream-openssl

	config PACKAGE_$(PKG_NAME)_INCLUDE_libustream-mbedtls
		depends on !(PACKAGE_$(PKG_NAME)_INCLUDE_libustream-wolfssl || PACKAGE_$(PKG_NAME)_INCLUDE_libustream-openssl)
		bool "Include libustream-mbedtls"
		default y if DEFAULT_libustream-mbedtls
		select PACKAGE_libustream-mbedtls

endmenu
config PACKAGE_$(PKG_NAME)_INCLUDE_Kcptun
	bool "Include Kcptun"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_NaiveProxy
	bool "Include NaiveProxy"
	depends on !(arc||armeb||mips||mips64||powerpc)
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_Redsocks2
	bool "Include Redsocks2"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Libev_Client
	bool "Include Shadowsocks Libev Client"
	default y if i386||x86_64||arm

config PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Libev_Server
	bool "Include Shadowsocks Libev Server"
	default y if i386||x86_64||arm

config PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Rust_Client
	bool "Include Shadowsocks Rust Client"
	depends on aarch64||arm||i386||mips||mipsel||x86_64
	default y if aarch64

config PACKAGE_$(PKG_NAME)_INCLUDE_Shadowsocks_Rust_Server
	bool "Include Shadowsocks Rust Server"
	depends on aarch64||arm||i386||mips||mipsel||x86_64
	default y if aarch64

config PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Libev_Client
	bool "Include ShadowsocksR Libev Client"
	default y

config PACKAGE_$(PKG_NAME)_INCLUDE_ShadowsocksR_Libev_Server
	bool "Include ShadowsocksR Libev Server"
	default y if i386||x86_64||arm

config PACKAGE_$(PKG_NAME)_INCLUDE_Simple_Obfs
	bool "Include Shadowsocks Simple Obfs Plugin"
	default y if i386||x86_64||arm

config PACKAGE_$(PKG_NAME)_INCLUDE_Trojan
	bool "Include Trojan"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_V2ray_Plugin
	bool "Include Shadowsocks V2ray Plugin"
	default n

config PACKAGE_$(PKG_NAME)_INCLUDE_Xray
	bool "Include Xray"
	default y if aarch64||arm||i386||x86_64
endef

define Package/$(PKG_NAME)/conffiles
/etc/config/shadowsocksr
/etc/ssrplus/
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
