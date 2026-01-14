---
title: "Minor Non-Breaking Changes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/minor_changes_v13.0.1.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Minor Non-Breaking Changes

In this article

The following minor non-breaking changes were introduced in Veeam PowerShell 13.0.1.

Backup Infrastructure

Virtualization Servers and Hosts

In this version, the Type parameter in the [Get-VBRServer](get-vbrserver.md) cmdlet now accepts the VBRHostType type.

Data Recovery

Disk Publishing (Data Integration API)

In this version, the [Unpublish-VBRBackupContent](unpublish-vbrbackupcontent.md) cmdlet now accept pipeline input for the Session parameter.

Veeam Agent Management

Veeam PowerShell Types

In this version, the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md) object has a new property: BiosUuid.

Microsoft EntraID Support

Veeam PowerShell Enumerations

In this version, the [VBREntraIDTenantItemType](enums.md#VBREntraIDTenantItemType) enum has a new property: DeviceConfiguration.

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
