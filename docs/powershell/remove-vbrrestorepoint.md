---
title: "Remove-VBRRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrrestorepoint.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRRestorePoint

In this article

Short Description

Removes individual VMs from backup or replicas.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRRestorePoint -Oib <COib[]> [-Name <String[]>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup of a selected VMs or replicas.

The backup is removed from disk. If you remove a replica, the replicated VM is removed from infrastructure.

If you need to remove replicated VM, run the [Remove-VBRReplica](remove-vbrreplica.md) cmdlet.

|  |
| --- |
| Important |
| This cmdlet removes all restore points of the selected VMs or replicas. Keep in mind that the subsequent backup jobs may fail to produce valid backup after you run this cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Oib | Specifies the array of VM restore points. The cmdlet will use these restore point to locate the VMs and remove the backups of these VMs. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet.  [For restore points from archive extents and capacity extents]  Accepts the [VBRSOBRObjectStorageRestorePoint](vbrsobrobjectstoragerestorepoint.md) object. To get this object, run the [Get-VBRSOBRObjectStorageRestorePoint](get-vbrsobrobjectstoragerestorepoint.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| Name | This parameter is legacy and not supported. | String[] | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Restore Points of Certain VM

|  |  |
| --- | --- |
| This example shows how to remove restore points of the Webserver03 VM.  |  | | --- | | $backup = Get-VBRBackup -Name "Webservers Backup Job"  $vm = Get-VBRRestorePoint -Backup $backup -Name "Webserver03"  Remove-VBRRestorePoint -Oib $vm |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Save the result to the $vm variable. 3. Run the Remove-VBRRestorePoint cmdlet. Set the $vm variable as the Oib parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Restore Points from Capacity Extent

|  |  |
| --- | --- |
| This example shows how to remove backup of the Webserver03 VM from the capacity extent. The Confirm prompt is disabled.  |  | | --- | | $backup = Get-VBRBackup -Name "Webservers Backup Job"  $vm = Get-VBRSOBRObjectStorageRestorePoint -Id "c2befce4-c7f4-4a53-a08b-e37580a682e7", "9577ab06-8ca5-4a5a-bd5c-d6124b0a4058" -CapacityTier  Remove-VBRRestorePoint -Oib $vm -Confirm:$false |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.  1. Run the [Get-VBRSOBRObjectStorageRestorePoint](get-vbrsobrobjectstoragerestorepoint.md) cmdlet. Specify the Id parameter value. Save the result to the $vm variable.  1. Run the Remove-VBRRestorePoint cmdlet. Set the $vm variable as the Oib parameter value. Set the Confirm parameter to $false. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing Restore Points from Archive Extent

|  |  |
| --- | --- |
| This example shows how to remove backup of the Webserver03 VM from the archive extent.  |  | | --- | | $backup = Get-VBRBackup -Name "Webservers Backup Job"  $vm = Get-VBRSOBRObjectStorageRestorePoint -Id "c2befce4-c7f4-4a53-a08b-e37580a682e7", "9577ab06-8ca5-4a5a-bd5c-d6124b0a4058" -Archive  Remove-VBRRestorePoint -Oib $vm |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.  1. Run the [Get-VBRSOBRObjectStorageRestorePoint](get-vbrsobrobjectstoragerestorepoint.md) cmdlet. Specify the Id parameter value and provide the Archive parameter. Save the result to the $vm variable.  1. Run the Remove-VBRRestorePoint cmdlet. Set the $vm variable as the Oib parameter value. |

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRSOBRObjectStorageRestorePoint](get-vbrsobrobjectstoragerestorepoint.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
