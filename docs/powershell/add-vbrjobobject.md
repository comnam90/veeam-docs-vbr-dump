---
title: "Add-VBRJobObject (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrjobobject.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Add-VBRJobObject (obsolete)

In this article

Short Description

Adds VMs to existing job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to create a new backup job using the [Add-VBRViJobObject](add-vbrvijobobject.md) or the [Add-VBRHvJobObject](add-vbrhvjobobject.md) cmdlets. |

Applies to

Platform: VMware

Syntax

This cmdlet provides parameter sets that allow you to:

* Add VMs to existing backup, replication or copy job.

|  |
| --- |
| Add-VBRJobObject -Job <CBackupJob> -Server <CHost> -Objects <String[]> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

* Add VM containers to existing backup, replication or copy job.

|  |
| --- |
| Add-VBRJobObject -Job <CBackupJob> -Server <CHost> -Entities <CEntity[]> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to add VMs or VM containers to existing backup, replication or copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job you want to add VMs to. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 1 | False |
| Server | Specifies the host where the VMs or VM containers you want to add reside. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 2 | False |
| Objects | Specifies the string with the names of VMs you want to add to the job.  You can assign multiple VMs to this object. | String[] | True | 3 | True (ByValue, ByProperty Name) |
| Entities | Specifies the VMs or VM containers you want to add to the job.  You can assign multiple VMs to this object. | Accepts the CEntity[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) or [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | True | 3 | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding VM to Existing Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to add the vm3 VM to the Backup Job job.  |  | | --- | | $server = Get-VBRServer -Name "Hv"  $job = Get-VBRJob -Name "Backup Job"  Add-VBRJobObject –Job $job –Server $server –Objects vm3 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save it to the $server variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save it to the $job variable. 3. Run the Add-VBRJobObject cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Set the $server variable as the Server parameter value. * Specify the Objects parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding VM to Existing Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to add the vm3 VM to the Backup Job job.  |  | | --- | | $server = Get-VBRServer -Name "Hv"  $job = Get-VBRJob -Name "Backup Job"  Find-VBRViEntity -Name "vm3" | Add-VBRJobObject -Job $job -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save it to the $server variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save it to the $job variable. 3. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. 4. Pipe the cmdlet output to the Add-VBRJobObject cmdlet. Set the $job variable as the Job parameter value. Set the $server variable as the Server parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRServer](get-vbrserver.md)

* [Find-VBRViEntity](find-vbrvientity.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
