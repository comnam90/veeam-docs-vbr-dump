---
title: "VBRNetworkTrafficRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnetworktrafficrule.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# VBRNetworkTrafficRule

In this article

Contains network traffic rule details.

Properties

| Property | Type | Description |
| --- | --- | --- |
| SourceIPStart | string | Specifies the first IP address of the IP source range. |
| SourceIPEnd | string | Specifies the last IP address of the IP source range. |
| TargetIPStart | string | Specifies the first IP address of the IP target range. |
| TargetIPEnd | string | Specifies the last IP address of the IP target range. |
| EncryptionEnabled | boolean | Indicates if the encryption for a network traffic rule is enabled. |
| ThrottlingEnabled | boolean | Indicates if throttling in a network traffic rule is enabled. |
| RestoreThrottlingAllowed | boolean | Indicates if throttling for restore operations in a network traffic rule is enabled. |
| ThrottlingUnit | VBRSpeedUnit | Specifies the measuring unit for the ThrottlingValue parameter:   * MbitPerSec * MbytePerSec * KbytePerSec |
| ThrottlingValue | int32 | Specifies the maximum speed value that must be used to transfer VM machine data from source to target. |
| ThrottlingWindowEnabled | SwitchParameter | Defines that a schedule for a network traffic rule is enabled. |
| ThrottlingWindowOptions | VBRBackupWindowOptions | Specifies the time interval during which Veeam Backup & Replication must apply a network traffic rule. |

Related Commands

[Add-VBRNetworkTrafficRule](add-vbrnetworktrafficrule.md)

Page updated 8/21/2025

Page content applies to build 13.0.1.1071
