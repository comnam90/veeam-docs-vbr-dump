---
title: "Add-VBRNetworkTrafficRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrnetworktrafficrule.html"
last_updated: "8/1/2025"
product_version: "13.0.1.1071"
---

# Add-VBRNetworkTrafficRule

In this article

Short Description

Creates network traffic rules.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRNetworkTrafficRule -Name <String> -SourceIPStart <IPAddress> -SourceIPEnd <IPAddress> -TargetIPStart <IPAddress> -TargetIPEnd <IPAddress> [-EnableEncryption] [-EnableThrottling] [-AllowRestoreThrottling] [-ThrottlingUnit <VBRSpeedUnit>] [-ThrottlingValue <Int32>] [-EnableThrottlingWindow] [-ThrottlingWindowOptions <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates network traffic rules. With network traffic rules, you can limit the traffic throughput between components in the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies a name that you want to assign to a network traffic rule. | String | True | Named | False |
| SourceIPStart | Specifies the first IP address of the IP source range. | IPAddress | True | Named | False |
| SourceIPEnd | Specifies the last IP address of the IP source range. | IPAddress | True | Named | False |
| TargetIPStart | Specifies the first IP address of the IP target range. | IPAddress | True | Named | False |
| TargetIPEnd | Specifies the last IP address of the IP target range. | IPAddress | True | Named | False |
| EnableEncryption | Enables encryption for a network traffic rule. Veeam Backup & Replication will encrypt the data that is passed between backup infrastructure components on the source and target side. | SwitchParameter | False | Named | False |
| EnableThrottling | Enables throttling for a network traffic rule. Veeam Backup & Replication will limit the traffic throughput between the backup infrastructure components within the specified IP range.  Use the following parameters to set the maximum value:   * ThrottlingValue * ThrottlingUnit | SwitchParameter | False | Named | False |
| ThrottlingValue | Specifies the maximum speed value that must be used to transfer VM machine data from source to target. | Int32 | False | Named | False |
| ThrottlingUnit | For the EnableThrottling parameter.  Specifies the measuring unit for the ThrottlingValue parameter: You can set the following units:   * MbitPerSec * MbytePerSec * KbytePerSec   Default: MbitPerSec. | VBRSpeedUnit | False | Named | False |
| EnableThrottlingWindow | Enables the schedule for a network traffic rule. | SwitchParameter | False | Named | False |
| ThrottlingWindowOptions | Specifies the time interval during which Veeam Backup & Replication must apply a network traffic rule. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| AllowRestoreThrottling | Enables throttling for restore operations. Veeam Backup & Replication will limit restore operation traffic between backup infrastructure components within the specified IP range. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNetworkTrafficRule](vbrnetworktrafficrule.md)

Examples

Creating Network Traffic Rule

This command creates a network traffic rule that also throttles restore operations.

|  |
| --- |
| Add-VBRNetworkTrafficRule -Name "New rule" -SourceIPStart 192.168.0.1 -SourceIPEnd 192.168.0.255 -TargetIPStart 192.168.0.1 -TargetIPEnd 192.168.0.255 -EnableThrottling -AllowRestoreThrottling -ThrottlingValue 5 -ThrottlingUnit MbitPerSec |

Page updated 8/1/2025

Page content applies to build 13.0.1.1071
