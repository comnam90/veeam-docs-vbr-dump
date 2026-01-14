---
title: "VBRInstalledLicense"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrinstalledlicense.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRInstalledLicense

In this article

Contains installed license details.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Status | [VBRLicenseStatus](enums.md#VBRLicenseStatus) | License status. |
| ExpirationDate | DateTime | License expiration date. |
| Type | [VBRLicenseType](enums.md#VBRLicenseType) | License type. |
| Edition | [VBRLicenseEdition](enums.md#VBRLicenseEdition) | License edition. |
| LicensedTo | String | Person or organization to which the license was issued. |
| SocketLicenseSummary | [VBRSocketLicenseSummary](vbrsocketlicensesummary.md) | Per-socket license usage. |
| InstanceLicenseSummary | [VBRInstanceLicenseSummary](vbrinstancelicensesummary.md) | Per-instance license usage. |
| SupportId | String | Support ID required for contacting Veeam Support. |
| SupportExpirationDate | DateTime | Date when the support expires. |
| AutoUpdateEnabled | Bool | Defines the state of automatic license update:   * True - Enabled * False - Disabled |
| FreeAgentInstanceConsumptionEnabled | Bool | Defines the state of instance consumption by Veeam Agents:   * True - Enabled * False - Disabled |
| CloudConnect | [VBRCloudConnectedLicenseMode](enums.md#VBRCloudConnectedLicenseMode) | Defines Cloud Connect license mode. |

Related Commands

[Get-VBRInstalledLicense](get-vbrinstalledlicense.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
