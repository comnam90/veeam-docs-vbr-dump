---
title: "Add-VSBHvApplicationGroup (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vsbhvapplicationgroup.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Add-VSBHvApplicationGroup (obsolete)

In this article

Short Description

Creates a Hyper-V application group for SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. Run the [Add-VBRApplicationGroup](add-vbrapplicationgroup.md) cmdlet instead. |

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VSBHvApplicationGroup [-Name <String>] [-VmFromBackup <CHvVmItem[]>] [-RestorePoint <COib[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new Hyper-V application group.

This cmdlet provides two scenarios. You can add VMs to your application group either by searching for existing VMs or by adding a restore point containing the VMs you need.

Note that you can set the order the VMs in the application group will be powered on when the SureBackup job starts. This may be important if any of the applications must be started prior to other. The VMs are powered in the order they were added to the VM object in this cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the application group. | String | False | Named | False |
| VmFromBackup | Specifies the array of Hyper-V VMs. The cmdlet will add these VMs to the application group. | Accepts the CHvVmItem[] object. To create this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| RestorePoint | Specifies the array of VM restore points. The cmdlet will find the VMs backed up in these restore points and add them to the application group. | Accepts the COib[] object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating New Application Group [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create the Microsoft Exchange Appgroup application group.  |  | | --- | | Find-VBRHvEntity -Name "DC", "DNSServer" | Add-VSBHvApplicationGroup -Name "Microsoft Exchange Appgroup" |  Perform the following steps:   1. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Add-VSBHvApplicationGroup cmdlet. Specify the Name parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating New Application Group [Using Variable]

|  |  |
| --- | --- |
| This example shows how to create the MailServer Appgroup application group.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Id 2ee79fec-9aa8-4058-a147-ff6b76ef2924  Add-VSBHvApplicationGroup -Name "MailServer Appgroup" -RestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Id parameter value. Save the result to the $restorepoint variable. 2. Run the Add-VSBHvApplicationGroup cmdlet. Specify the Name parameter value. Set the $restorepoint variable as the RestorePoint parameter value. |

Related Commands

* [Find-VBRHvEntity](find-vbrhventity.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
