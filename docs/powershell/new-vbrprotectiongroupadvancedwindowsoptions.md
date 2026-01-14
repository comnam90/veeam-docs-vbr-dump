---
title: "New-VBRProtectionGroupAdvancedWindowsOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrprotectiongroupadvancedwindowsoptions.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# New-VBRProtectionGroupAdvancedWindowsOptions

In this article

Short Description

Creates additional settings for Veeam Agent for Microsoft Windows.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRProtectionGroupAdvancedWindowsOptions [-EnableBandwidthThrottling] [-BandwidthThrottlingValue <int>] [-BandwidthThrottlingUnitType <VBRSpeedUnit> {MbitPerSec | MbytePerSec | KbytePerSec}] [-DisableBackupOverMeteredConnection] [-DisableBackupOverVPNConnections] [-UseSpecifiedWiFiNetworks] [-WiFiNetworks <string[]>] [-EnableAgentThrottling] [-ThrottleAgentOn <VBREpThrottlingAgentType> {Workstations | Servers | AllHosts}] [-EnableFLRWithoutAdministrativeAccount]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRProtectionGroupAdvancedWindowsOptions](vbrprotectiongroupadvancedwindowsoptions.md) object. This object contains additional settings for Veeam Agent for Microsoft Windows machines. These settings will be applied to Veeam Agent deployed on computers added to a protection group. You can specify the following types of settings:

* Network usage settings
* Throttling settings
* Security settings

|  |
| --- |
| Tip |
| To apply the settings to an existing protection group, save the [VBRProtectionGroupAdvancedWindowsOptions](vbrprotectiongroupadvancedwindowsoptions.md) object to the variable and run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| EnableBandwidthThrottling | Enables the bandwidth limit.  Use the BandwidthThrottlingValue and the BandwidthThrottlingUnitType parameters to set the value and the unit type for bandwidth limit. | SwitchParameter | False | Named | True (ByProperty Name) |
| BandwidthThrottlingValue | Specifies the bandwidth limit value. | Int | False | Named | True (ByProperty Name) |
| BandwidthThrottlingUnitType | Specifies the measure units for measure limit. You can select the following type of measure units:   * MbitPerSec: for megabit per second unit * MbytePerSec: for megabyte per second unit * KbytePerSec: for kilobyte per second unit | VBRSpeedUnit | False | Named | True (ByProperty Name) |
| DisableBackupOverMeteredConnection | Defines that backup over metered connections will be disabled. | SwitchParameter | False | Named | True (ByPropertyName) |
| DisableBackupOverVPNConnections | Defines that backup over VPN connections will be disabled. | SwitchParameter | False | Named | True (ByPropertyName) |
| UseSpecifiedWiFiNetworks | Defines that Veeam Backup & Replication will restrict the WiFi usage to the specified networks.  Use the WiFiNetworks parameter to specify the networks over which backup will be allowed. | SwitchParameter | False | Named | True (ByPropertyName) |
| WiFiNetworks | Specifies the SSID of the Wi-Fi network. Veeam Agent will perform backup over the specified SSID only. | String[] | False | Named | True (ByPropertyName) |
| EnableAgentThrottling | Enables throttling for Veeam Agent activities during backup.  Use the ThrottleAgentOn parameter to specify the type of computers. | SwitchParameter | False | Named | True (ByPropertyName) |
| ThrottleAgentOn | Specifies the type of computers. Veeam Backup & Replication will throttle Veeam Agent activities during backup on computers of these types.  You can select one of the following types of the computers:   * Workstations * Servers * AllHosts | VBREpThrottlingAgentType | False | Named | True (ByPropertyName) |
| EnableFLRWithoutAdministrativeAccount | Defines that users without administrative privileges will be able to perform file-level restore on Veeam Agent computers.  Note: This parameter works only for backups located on Veeam Backup & Replication. | SwitchParameter | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRProtectionGroupAdvancedWindowsOptions](vbrprotectiongroupadvancedwindowsoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Additional Settings for Microsoft Windows Machines

|  |  |
| --- | --- |
| This command creates additional settings for Veeam Agent for Microsoft Windows machines. The additional settings will have the following options:   * Bandwidth limit is enabled and set to 20 megabytes per second. * Backup over metered connections option is enabled. * Throttling for Veeam Agent activities is enabled on all machines. * Users without administrative privileges will be able to perform the file-level restore on Veeam Agent computers.   |  | | --- | | New-VBRProtectionGroupAdvancedWindowsOptions -EnableBandwidthThrottling -BandwidthThrottlingValue 20  -BandwidthThrottlingUnitType MbytePerSec -DisableBackupOverMeteredConnection:$false  -EnableAgentThrottling -ThrottleAgentOn AllHosts -EnableFLRWithoutAdministrativeAccount | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying Additional Settings to Protection Group

|  |  |
| --- | --- |
| This example shows how to create additional settings for the protection group and apply these settings to the Windows machines protection group.  |  | | --- | | $options = New-VBRProtectionGroupAdvancedWindowsOptions -EnableBandwidthThrottling -BandwidthThrottlingValue 20 -BandwidthThrottlingUnitType MbytePerSec -DisableBackupOverMeteredConnection:$false -EnableAgentThrottling -ThrottleAgentOn AllHosts -EnableFLRWithoutAdministrativeAccount  $group = Get-VBRProtectionGroup -Name "Windows machines"  Set-VBRProtectionGroup -ProtectionGroup $group -AdvancedOptions $options |  Perform the following steps:   1. Run the New-VBRProtectionGroupAdvancedWindowsOptions cmdlet. Specify the necessary parameters. Save the result to the $options variable. 2. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 3. Run the [Set-VBRProtectionGroup](set-vbrprotectiongroup.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Set the $options variable as the AdvancedOptions parameter value. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Set-VBRProtectionGroup](set-vbrprotectiongroup.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
