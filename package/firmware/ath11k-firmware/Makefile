#
# Copyright (C) 2021 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ath11k-firmware
PKG_SOURCE_DATE:=2021-07-20
PKG_SOURCE_VERSION:=d4003c1921810adcc455d46f17776a3392b29436
PKG_MIRROR_HASH:=skip
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://git.codelinaro.org/clo/ath-firmware/ath11k-firmware.git

PKG_MAINTAINER:=Robert Marko <robimarko@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/ath11k-firmware-default
  SECTION:=firmware
  CATEGORY:=Firmware
  URL:=$(PKG_SOURCE_URL)
  DEPENDS:=
endef

define Package/ath11k-firmware-ipq6018
$(Package/ath11k-firmware-default)
  TITLE:=ath11k firmware for IPQ6018 devices
endef

define Package/ath11k-firmware-ipq8074
$(Package/ath11k-firmware-default)
  TITLE:=ath11k firmware for IPQ8074 devices
endef

define Build/Compile
	true
endef

define Package/ath11k-firmware-ipq6018/install
	$(INSTALL_DIR) $(1)/lib/firmware/ath11k/IPQ6018/hw1.0
	$(INSTALL_DIR) $(1)/lib/firmware/IPQ6018
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/IPQ6018/hw1.0/2.5.0.1/WLAN.HK.2.5.0.1-01100-QCAHKSWPL_SILICONZ-1/* \
		$(1)/lib/firmware/IPQ6018/
	$(INSTALL_DATA) ./files/board-2.bin.IPQ6018 \
		$(1)/lib/firmware/ath11k/IPQ6018/hw1.0/board-2.bin
	$(INSTALL_DATA) ./files/qdss_trace_config.bin \
		$(1)/lib/firmware/ath11k/IPQ6018/hw1.0/qdss_trace_config.bin
endef

define Package/ath11k-firmware-ipq8074/install
	$(INSTALL_DIR) $(1)/lib/firmware/ath11k/IPQ8074/hw2.0
	$(INSTALL_DIR) $(1)/lib/firmware/IPQ8074
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/IPQ8074/hw2.0/board-2.bin \
		$(1)/lib/firmware/ath11k/IPQ8074/hw2.0/
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/IPQ8074/hw2.0/2.5.0.1/WLAN.HK.2.5.0.1-01100-QCAHKSWPL_SILICONZ-1/* \
		$(1)/lib/firmware/IPQ8074/
endef

$(eval $(call BuildPackage,ath11k-firmware-ipq6018))
$(eval $(call BuildPackage,ath11k-firmware-ipq8074))
