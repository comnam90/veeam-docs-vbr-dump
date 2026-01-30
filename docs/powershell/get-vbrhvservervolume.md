---
title: "Get-VBRHvServerVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrhvservervolume.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRHvServerVolume


Short Description

Returns volume-specific settings for Microsoft Hyper-V hosts.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRHvServerVolume -Server <CHost> [-Type <EVBRHvVolumeType[]> {Csv | Cluster | Local | ScaleOut | LocalShare}] [-MountPoint <string>] [-VolumeId <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns volume-specific settings for Microsoft Hyper-V hosts.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Microsoft Hyper-V host added to the backup infrastructure. The cmdlet will return the volume-specific settings of this Microsoft Hyper-V host. | Accepts the CHost object. To create this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Type | Specifies a type of volume that is added to a Microsoft Hyper-V host. The cmdlet will return Microsoft Hyper-V hosts with the specified types of volumes of the specified types:   * Csv * Cluster * Local * ScaleOut * LocalShare | EVBRHvVolumeType[] | False | Named | True (ByValue, ByPropertyName) |
| MountPoint | Specifies a mount point of a Microsoft Hyper-V host. The cmdlet will return a Microsoft Hyper-V host with the specified mount point. | String | False | Named | True (ByValue, ByPropertyName) |
| VolumeId | Specifies an ID of the volume that is added to a Microsoft Hyper-V host. The cmdlet will return Microsoft Hyper-V host with the specified volume ID. | Guid | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvServerVolume object that contains volume-specific settings for Microsoft Hyper-V hosts.

Examples

Getting Volume Settings for Microsoft Hyper-V Hosts

This example shows how to get volume settings for Microsoft Hyper-V hosts. The cmdlet output will contain the following settings Id, ServerId, MountPoint, Type, VssProvider and MaxSnapshots.

|  |
| --- |
| $server = Get-VBRServer -Name hyperv09.tech.local  Get-VBRHvServerVolume -Server $server  Id           : 5f11f8e1-f10e-43a0-b1ea-b7307c97331a  ServerId     : 0216cada-ed31-4c33-bdfe-b3b24beda391  MountPoint   : C:\  Type         : Local  VssProvider  : Veeam.Backup.PowerShell.Infos.VSSProviderObject  MaxSnapshots : 5    Id           : 3e1c1860-9632-4b9a-adb1-b70297c9669e  ServerId     : 617fb448-6aac-47cb-a94c-893eef8dc224  MountPoint   : D:\  Type         : Local  VssProvider  : Veeam.Backup.PowerShell.Infos.VSSProviderObject  MaxSnapshots : 4 |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the Get-VBRHvServerVolume cmdlet. Set the $server variable as the Server parameter value.

Related Commands

[Get-VBRServer](get-vbrserver.md)


