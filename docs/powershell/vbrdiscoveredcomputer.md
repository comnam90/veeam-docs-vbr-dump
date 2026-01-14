---
title: "VBRDiscoveredComputer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrdiscoveredcomputer.html"
last_updated: "10/23/2025"
product_version: "13.0.1.1071"
---

# VBRDiscoveredComputer

In this article

Contains a discovered computer.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| State | VBRDiscoveredComputerState | The state of the discovered computer:   * Unknown * Online * Offline |
| AgentStatus | VBRAgentStatus | The state of a Veeam Agent installed on the discovered computer:   * Installed * NotInstalled * UpgradeAvailable * Failed * UnsupportedOperatingSystem |
| AgentVersion | Version | The version of a backup agent installed on the discovered computer. |
| DriverStatus | VBRDriverStatus | The state of a driver installed on the discovered computer:   * Unknown  * Installed * NotInstalled * Stopped * Failed * UpgradeAvailable |
| DriverVersion | Version | The version of a driver installed on the discovered computer. |
| CdpFilterStatus | VBRCDPGuestStatus | The state of the Veeam CDP Volume Filter Driver installed on the discovered computer:   * Installed * NotInstalled * UpgradeAvailable * Failed * UnsupportedOperatingSystem * Unknown |
| CdpFilterVersion | Version | The version of the Veeam CDP Volume Filter Driver installed on the discovered computer. |
| CdpGuestStatus | VBRCDPGuestStatus | The state of the Veeam CDP Agent Service installed on the discovered computer:   * Installed * NotInstalled * UpgradeAvailable * Failed * UnsupportedOperatingSystem * Unknown |
| CdpGuestVersion | Version | The version of the Veeam CDP Agent Service installed on the discovered computer. |
| RebootRequired | bool | Indicates if the discovered computer must be rebooted. |
| IPAddress | string[] | The array of the discovered computer IP addresses. |
| LastConnected | DateTime? | The date and time of the last connection with Veeam Agent installed on this discovered computer. |
| OperatingSystem | VBROperatingSystem | The type of the discovered computer operating system.   * Unknown * WindowsXP * Windows2003 * Windows2008 * WindowsVista * Windows7 * Windows8 * Windows81 * Windows10 * Windows11 * WindowsServer2008R2 * WindowsServer2012 * WindowsServer2012R2 * WindowsServer2016 * WindowsServer2016Nano * WindowsServer2019 * WindowsServer2022 * AzureStackHCI * Linux |
| OpeartingSystemVersion | Version | The version of the discovered computer operating system. |
| OperatingSystemPlatform | VBROperatingSystemPlatform | The architecture of the discovered computer operating system:   * Unknown, * x86 * x64 * PPC64le |
| OperatingSystemUpdateVersion | integer | The updated version of the discovered computer operating system. |
| ObjectID | GUID | The discovered computer ID. |
| BiosUuid | String | The discovered computer BIOS UUID. |

Related Commands

[Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)

Page updated 10/23/2025

Page content applies to build 13.0.1.1071
