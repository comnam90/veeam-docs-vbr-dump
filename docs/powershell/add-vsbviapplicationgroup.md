---
title: "Add-VSBViApplicationGroup (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vsbviapplicationgroup.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Add-VSBViApplicationGroup (obsolete)


Short Description

Creates an application group for SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. Run the [Add-VBRApplicationGroup](add-vbrapplicationgroup.md) cmdlet instead |

Applies to

Platform: VMware

For Hyper-V, run the [Add-VSBHvApplicationGroup](add-vsbhvapplicationgroup.md) cmdlet.

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VSBViApplicationGroup [-Name <string>] [-VmFromBackup <CViVmItem[]>] [-VmFromReplica <CViVmItem[]>] [-RestorePoint <COib[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates an application group containing virtual machines that the application server is dependent on.

You can add to the same application groups VMs from backups and VMs from replicas. All VMs from the application group must have at least one valid restore point created by the time the SureBackup job starts.

Note that you can set the order the VMs in the application group will be powered on when the SureBackup job starts. This may be important if any of the applications must be started prior to other. The VMs are powered in the order they were added to the VM object in this cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the application group. | String | False | Named | False |
| VmFromBackup | Used for adding VMs from backup.  Specifies the VMs that you want to add to the application group. Veeam Backup & Replication will search for backup jobs that contain the specified VMs and use the most recent restore points of them.  You can assign multiple VMs to this object. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| VmFromReplica | Used for adding VMs from replicas.  Specifies the VMs that you want to add to the application group. Veeam Backup & Replication will search for replication  jobs that contain the specified VMs and use the most recent restore points of them.  You can assign multiple VMs to this object. | Accepts the CViVmItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| RestorePoint | Specifies the particular restore points of the VMs you want to add to the application group.  You can assign multiple restore points to this object. | Accepts the COib[] object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating New Application Group [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create the Microsoft Exchange Appgroup application group.  |  | | --- | | Find-VBRViEntity -Name "DC", "DNSServer" | Add-VSBViApplicationGroup -Name "Microsoft Exchange Appgroup" |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Add-VSBViApplicationGroup cmdlet. Specify the Name parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating New Application Group [Using Variable]

|  |  |
| --- | --- |
| This example shows how to create the Microsoft Exchange Appgroup application group.  |  | | --- | | $restorepoint = Get-VBRRestorePoint -Id 2ee79fec-9aa8-4058-a147-ff6b76ef2924  Add-VSBViApplicationGroup -Name "MailServer Appgroup" -RestorePoint $restorepoint |  Perform the following steps:   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Id parameter value. Save the result to the $restorepoint variable. 2. Run the Add-VSBViApplicationGroup cmdlet. Specify the Name parameter value. Set the $restorepoint variable as the RestorePoint parameter value. |

Related Commands

* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)


