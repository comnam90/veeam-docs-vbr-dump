---
title: "Set-VBRHvServerVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvservervolume.html"
last_updated: "5/20/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvServerVolume


Short Description

Modifies volume-specific settings for Microsoft Hyper-V hosts.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvServerVolume -Volume <VBRHvServerVolumeObject[]> [-VSSProvider <VSSProviderObject>] [-MaxSnapshots <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies volume-specific settings for Microsoft Hyper-V hosts.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies an array of volume-specific settings for Microsoft Hyper-V hosts. The cmdlet will modify these settings. | Accepts the VBRHvServerVolumeObject[] object. To create this object, run the [Get-VBRHvServerVolume](get-vbrhvservervolume.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| VSSProvider | Specifies the VSS provider for a volume. The cmdlet will set this VSS provider to take a VSS snapshot of the volume. | Accepts the VSSProviderObject object. To create this object, run the [Get-VBRHvVssProvider](get-vbrhvvssprovider.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| MaxSnapshots | Specifies a number of snapshots that you can store simultaneously for one volume. The cmdlet will set the specified number of snapshots for the volume. | Int32 | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvServerVolume object that contains volume-specific settings for Microsoft Hyper-V hosts.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying VSS Provider Settings

|  |  |
| --- | --- |
| This example shows how to modify volume-specific settings and set a VSS provider for a volume located on the Microsoft Hyper-V host. Veeam Backup & Replication will use the Microsoft File Share Shadow Copy provider to create VSS snapshots of the volume.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  $volume = Get-VBRHvServerVolume -Server $server  $provider = Get-VBRHvVssProvider -Server $server -Name "Microsoft File Share Shadow Copy provider"  Set-VBRHvServerVolume -Volume $volume -VSSProvider $provider |  Perform the following steps:   1. Get the volume settings:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerVolume](get-vbrhvservervolume.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $volume variable.  1. Run the [Get-VBRHvVssProvider](get-vbrhvvssprovider.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the result to the $provider variable. 2. Run the Set-VBRHvServerVolume cmdlet. Set the $volume variable as the Volume parameter value. Set the $provider variable as the VSSProvider parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Number of Snapshots

|  |  |
| --- | --- |
| This example shows how to modify volume-specific settings and set a number of snapshots that you can store simultaneously on one volume. Veeam Backup & Replication will store a maximum 3 snapshots on the volume.  |  | | --- | | $server = Get-VBRServer -Name hyperv09.tech.local  $volume = Get-VBRHvServerVolume -Server $server  Set-VBRHvServerVolume -Volume $volume -MaxSnapshots 3 |  Perform the following steps:   1. Get the volume settings:  1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerVolume](get-vbrhvservervolume.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $volume variable.  1. Run the Set-VBRHvServerVolume cmdlet. Set the $volume variable as the Volume parameter value. Specify the MaxSnapshots parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerVolume](get-vbrhvservervolume.md)


