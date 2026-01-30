---
title: "Add-VSBApplicationGroup (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vsbapplicationgroup.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Add-VSBApplicationGroup (obsolete)


Short Description

Creates a VMware application group for SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to create backup to tape copy jobs using the [Add-VSBViApplicationGroup](add-vsbviapplicationgroup.md) or [Add-VSBHvApplicationGroup](add-vsbhvapplicationgroup.md) cmdlets. |

Applies to

Platform: VMware

Syntax

|  |
| --- |
| Add-VSBApplicationGroup [-Name <String>] [-Vm <CVm[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>]  -OR-  Add-VSBApplicationGroup [-Name <String>] [-RestorePoint <COib[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new VMware application group.

An application group is a component of SureBackup technology providing verification of virtual machines that need other virtual machines or services running, i.e. a domain controller, a DNS server or SQL database. To test such machines for recoverability, you need to create a SureBackup job and provide the copy of the production architecture running in a fenced-off environment that is performed by creating a virtual lab and an application group. The VMs in the application group are started first to ensure the proper testing environment for the primary VM.

Note that you can set the order the VMs in the application group will be powered on when the SureBackup job starts. This may be important if any of the applications must be started prior to other. The VMs are powered in the order they were added to the VM object in this cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the string with the name you want to assign to the application group. | String | True | 1 | False |
| Vm | Specifies the VMs you want to include into the application group.  You can assign multiple VMs to this object. | Accepts the CVm[] object. To create this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | 2 | True (ByValue, ByProperty Name) |
| RestorePoint | Specifies the restore points of VMs that should be added to the application group.  You can assign multiple restore points to this object. | Accepts the COib[] object. To create this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 2 | True (ByValue, ByProperty Name) |

<CommonParameters>

Examples

Creating Application Group

This example allows you to create the AppGroup application group.

|  |
| --- |
| $vms = Find-VBRViEntity -Name "srv001", "srv002" -DatastoresAndVMs  Add-VSBApplicationGroup –Name “AppGroup” –VM $vms |

Perform the following steps:

1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Provide the DatastoresAndVMs parameter. Save the result to the $vms variable.
2. Run the Add-VSBApplicationGroup cmdlet. Specify the Name parameter value. Set the $vms variable as the VM parameter value.

Related Commands

[Get-VBRRestorePoint](get-vbrrestorepoint.md)


