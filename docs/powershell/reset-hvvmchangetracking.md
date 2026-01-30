---
title: "Reset-HvVmChangeTracking"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-hvvmchangetracking.html"
last_updated: "6/11/2024"
product_version: "13.0.1.1071"
---

# Reset-HvVmChangeTracking


Short Description

Clears change tracking data for a specific VM or specific virtual disk (VHD).

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Clear change tracking data for a specific VM.

|  |
| --- |
| Reset-HvVmChangeTracking -Server <CHost> [-VMName <String>]  [<CommonParameters>] |

* Clear change tracking data for a specific virtual disk (VHD).

|  |
| --- |
| Reset-HvVmChangeTracking -Server <CHost> [-VhdPath <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet clears and resets change tracking data for a specific VM or for a specific virtual disk (VHD).

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the server where the VM reside. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 1 | False |
| VMName | Specifies the VM. The cmdlet will reset change tracking data for this VM. | String | False | Named | False |
| VhdPath | Specifies the virtual disk (VHD). The cmdlet will reset change tracking data for this disk. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Resetting Change Tracking Data for VM

|  |  |
| --- | --- |
| This example shows how to reset change tracking data for the Fileserver VM located on host represented by the $server variable.  |  | | --- | | $server = Get-VBRServer -Name "MyServer"  Reset-HvVmChangeTracking -Server $server -VMName "Fileserver" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Reset-HvVmChangeTracking cmdlet. Set the $server variable as the Server parameter value. Specify the VMName parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Resetting Change Tracking Data for Specified Virtual Disk

|  |  |
| --- | --- |
| This example shows how to reset change tracking data for the specified virtual disk. The VM is located on host represented by the $server variable.  |  | | --- | | $server = Get-VBRServer -Name "MyServer"  Reset-HvVmChangeTracking -Server $server -VhdPath "C:\Users\Public\Hyper-V\Virtual Hard Disks\hv\_dns.vhdx" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Reset-HvVmChangeTracking cmdlet. Set the $server variable as the Server parameter value. Specify the VhdPath parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)


