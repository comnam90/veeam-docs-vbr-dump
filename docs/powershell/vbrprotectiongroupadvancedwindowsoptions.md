---
title: "VBRProtectionGroupAdvancedWindowsOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrprotectiongroupadvancedwindowsoptions.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRProtectionGroupAdvancedWindowsOptions


Contains settings for Veeam Agent for Microsoft Windows machines.

Properties

| Property | Type | Description |
| --- | --- | --- |
| EnableBandwidthThrottling | bool | Enables the bandwidth limit. |
| BandwidthThrottlingValue | int | Bandwidth limit value. |
| BandwidthThrottlingUnitType | [VBRSpeedUnit](enums.md#VBRSpeedUnit) | Measure units for measure limits. |
| UseSpecifiedWiFiNetworks | bool | Uses specific networks. |
| WiFiNetworks | string[] | Specifies the SSID of the allowed Wi-Fi network. |
| DisableBackupOverMeteredConnection | bool | Disables backup over metered connections. |
| DisableBackupOverVPNConnections | bool | Disables backup over VPN connections. |
| EnableAgentThrottling | bool | Enables throttling. |
| ThrottleAgentOn | [VBREpThrottlingAgentType](enums.md#VBREpThrottlingAgentType) | Type of computers for which Veeam Backup & Replication throttles activities. |
| EnableFLRWithoutAdministrativeAccount | bool | Allows file-level restore without administrative privileges. |

Related Commands

[New-VBRProtectionGroupAdvancedWindowsOptions](new-vbrprotectiongroupadvancedwindowsoptions.md)


