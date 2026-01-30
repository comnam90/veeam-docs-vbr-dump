---
title: "Add-VSBHvJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vsbhvjob.html"
last_updated: "2/21/2024"
product_version: "13.0.1.1071"
---

# Add-VSBHvJob (obsolete)


Short Description

Creates a Hyper-V SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Add-VBRSureBackupJob](add-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VSBHvJob [-Name <String>] -VirtualLab <CHvSbVirtualLab> [-AppGroup <CSbAppGroup>] [-LinkedJob <CBackupJob[]>] [-Description <String>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new Hyper-V SureBackup job.

Note that when you create a SureBackup job, you need to run it manually unless you enable a job schedule.

Run the [Start-VSBJob](start-vsbjob.md) cmdlet to start the created SureBackup job.

Run the [Set-VSBJobScheduleOptions](set-vsbjobscheduleoptions.md) cmdlet to set schedule for the SureBackup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the SureBackup job. | String | False | Named | False |
| VirtualLab | Specifies the virtual lab you want to use for verification. | Accepts the CHvSbVirtualLab object. To get this object, run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| AppGroup | Specifies the application group you want to use to provide the copy of the production environment of the verified VM.  If you do not use an application group, make sure that the LinkedJob parameter is set. | Accepts the CSbAppGroup object. To get this object, run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md)  cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| LinkedJob | Specifies the array of backup, replication or copy jobs containing VMs you want to verify.  If you do not use a linked backup job, make sure that the AppGroup parameter is set. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Description | Specifies the description of the new SureBackup job. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding SureBackup Job with Virtual Lab, Application Group and Linked Job

|  |  |
| --- | --- |
| This example shows how to create the Exchange SureJob Sure Backup job using a virtual lab, an application group and a linked job.  |  | | --- | | $VLab01 = Get-VSBHvVirtualLab -Id 1022504c-9008-4883-b166-718bdf7280ea  $ExchangeAppgroup = Get-VSBApplicationGroup -Name "MailServer Appgroup"  Get-VBRJob -Name "Exchange Backup Job" | Add-VSBHvJob -Name "Exchange SureJob" -VirtualLab $VLab01 -AppGroup $ExchangeAppgroup |  Perform the following steps:   1. Run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. Specify the Id parameter value. Save the result to the $VLab01 variable. 2. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeAppgroup variable. 3. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 4. Pipe the cmdlet output to the Add-VSBHvJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $VLab01 variable as the VirtualLab parameter value. * Set the $ExchangeAppgroup variable as the AppGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding SureBackup Job with Virtual Lab and Application Group

|  |  |
| --- | --- |
| This example shows how to create the Exchange SureJob Sure Backup job using a virtual lab and an application group.  |  | | --- | | $VLab01 = Get-VSBHvVirtualLab -Id 1022504c-9008-4883-b166-718bdf7280ea  $ExchangeAppgroup = Get-VSBApplicationGroup -Name "MailServer Appgroup"  Add-VSBHvJob -Name "Exchange SureJob" -VirtualLab $VLab01 -AppGroup $ExchangeAppgroup |  Perform the following steps:   1. Run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. Specify the Id parameter value. Save the result to the $VLab01 variable. 2. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeAppgroup variable. 3. Run the Add-VSBHvJob cmdlet. Specify the Name parameter value. Set the $VLab01 variable as the VirtualLab parameter value. Set the $ExchangeAppgroup variable as the AppGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding SureBackup Job with Virtual Lab and Application Group [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create the Exchange SureJob Sure Backup job using a virtual lab and an application group.  |  | | --- | | $ExchangeAppgroup = Get-VSBApplicationGroup -Name "MailServer Appgroup"  Get-VSBHvVirtualLab -Name "Exchange VLab 01" | Add-VSBHvJob -Name "Exchange SureJob" -AppGroup $ExchangeAppgroup |  Perform the following steps:   1. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeAppgroup variable. 2. Run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Add-VSBHvJob cmdlet. Specify the Name parameter value. Set the $ExchangeAppgroup variable as the AppGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Adding SureBackup Job with Virtual Lab and Application Group [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create the Exchange SureJob Sure Backup job using a virtual lab and an application group.  |  | | --- | | $VLab01 = Get-VSBHvVirtualLab -Id 1022504c-9008-4883-b166-718bdf7280ea  $ExchangeBackup = Get-VBRJob -Name "Backup Copy Job"  Add-VSBHvJob -Name "Exchange SureJob" -VirtualLab $VLab01 -LinkedJob $ExchangeBackup |  Perform the following steps:   1. Run the [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md) cmdlet. Specify the Id parameter value. Save the result to the $VLab01 variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeBackup variable. 3. Run the Add-VSBHvJob cmdlet. Specify the Name parameter value. Set the $VLab01 variable as the VirtualLab parameter value. Set the $ExchangeBackup variable as the LinkedJob parameter value. |

Related Commands

* [Get-VSBHvVirtualLab](get-vsbhvvirtuallab.md)
* [Get-VSBApplicationGroup](get-vsbapplicationgroup.md)
* [Get-VBRJob](get-vbrjob.md)


