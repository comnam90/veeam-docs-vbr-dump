---
title: "Add-VBRCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcopyjob.html"
last_updated: "3/17/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCopyJob


Short Description

Creates VM and file copy jobs.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRCopyJob [-Name] <String> [-Type] <ESourceType> -Objects <Object[]> [-Server <CHost>] [-Folder <String>] [-FileName <String>] [-SourceServer <CHost>] [-Description <String>] [-Repository <CBackupRepository>] [-Force] [<CommonParameters>] |

Detailed Description

This cmdlet creates a new job that copies the selected VMs to another location.

With a VM copy job, you can create a fully-functioning copy of a VM that will require no manual editing and adjustments. VM copying can be helpful if you want to move your datacenter, mirror your production environment to test lab storage, etc.

Note that when you create a copy job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the created job.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set schedule for the job.

Run the [Copy-VBRJob](copy-vbrjob.md) cmdlet to create a copy of a job.

|  |
| --- |
| Note: |
| The cmdlet will not run if the geographic location of the VMs added to the job and the job target host location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the new copy job. | String | True | 1 | False |
| Type | Specifies the type of the created copy job which defines how VM data is retrieved:   * VDDK – Virtual Disk Development Kit (VMware vStorage API): used for VM backup jobs data. * Files: used for file backup data. * Backup: not supported (legacy mode). * Hyper-V: not supported (legacy mode). * VCB: not supported (legacy mode). * NET: not supported (legacy mode). * Tape: used for the tape jobs data. * ObjectStorage: used for object storage backup job data. * EntraIdTenant: used for a tenant backup job. | ESourceType | True | 2 | False |
| Objects | Specifies an array of names for VMs that you want to copy. | Object[] | True | Named | True (ByValue, |
| Server | Specifies the host where the created copy should be stored. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Folder | Specifies the string with full path to the folder where the created VM copy should be stored. | String | False | Named | False |
| FileName | Specifies the string with the file name for the created VM copy (by default, a copied file is given the same name as the VM). | String | False | Named | False |
| SourceServer | Specifies the server where the target files for file copy job are located. | Accepts the CHost or string (host name) object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Description | Specifies the description of the copy job. | String | False | Named | False |
| Repository | Specifies the backup repository to which you want to place the copied VMs.  You cannot use scale-out backup repository as target to the VM copy job. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a VM copy job even if the geographic location of the VMs added to the job and the target host location do not match. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating VM Copy to Repository Job

|  |  |
| --- | --- |
| This example shows how to create a VM copy job.  |  | | --- | | $machine = Find-VBRViEntity -Name "Serv49"  $repository = Get-VBRBackupRepository  Add-VBRCopyJob -Name "Copy02" -Type VDDK -Objects $machine -Repository $repository |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $machine variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Save the result to the $repository variable. 3. Run the Add-VBRCopyJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the VDDK option for the Type parameter. * Set the $machine variable as the Objects parameter value. * Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating VM Copy to Datastore Job

|  |  |
| --- | --- |
| This example shows how to create a job that copies a VM to a datastore.  |  | | --- | | $entity = Find-VBRViEntity -Name "ubuntusrv20"  $server = Get-VbrServer -name "pdctwesx07.tech.local"  Add-VBRCopyJob -Type VDDK -Name "Copy to Datastore" -Server $server -Folder "/vmfs/volumes/66fe8d59-97af39be-3e73-3cecef89ae04/User/" -Objects $entity |  Perform the following steps:   1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $entity variable. 2. Run the [Get-VbrServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the Add-VBRCopyJob cmdlet. Specify the following settings:  * Set the VDDK option for the Type parameter. * Specify the Name parameter value. * Set the $server variable as the Server parameter value. * Specify the Folder parameter value. * Set the $entity variable as the Objects parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRLocation](get-vbrlocation.md)
* [Find-VBRViEntity](find-vbrvientity.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


