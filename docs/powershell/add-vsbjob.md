---
title: "Add-VSBJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vsbjob.html"
last_updated: "2/23/2024"
product_version: "13.0.1.1071"
---

# Add-VSBJob (obsolete)


Short Description

Creates a VMware SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Add-VBRSureBackupJob](add-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Platform: VMware

For Hyper-V, run the [Add-VSBHvJob](add-vsbhvjob.md) cmdlet.

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VSBJob [-Name <String>] -VirtualLab <CViSbVirtualLab> [-AppGroup <CSbAppGroup>] [-LinkedJob <CBackupJob[]>] [-Description <String>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new VMware SureBackup job.

To add VMs that you want to verify to the SureBackup job, you can use an application group containing the list of VMs, or link a backup job which will act as a VM container.

Note that if you link a backup job, the SureBackup job will verify all VMs added to the linked job.

When you create a SureBackup job, you need to run it manually unless you enable a job schedule.

Run the [Start-VSBJob](start-vsbjob.md) cmdlet to start the created SureBackup job.

Run the [Set-VSBJobScheduleOptions](set-vsbjobscheduleoptions.md) cmdlet to set schedule for the SureBackup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the SureBackup job. | String | False | Named | False |
| VirtualLab | Specifies the virtual lab you want to use for verification. | Accepts the CViSbVirtualLab object. To get this object, run the [Get-VSBVirtualLab](get-vsbvirtuallab.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| AppGroup | Specifies the application group you want to use to provide the copy of the production environment of the verified VM.  If you do not use an application group, make sure that the LinkedJob parameter is set. | Accepts the CSbAppGroup object. To get this object, run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| LinkedJob | Specifies the array of backup, replication or copy jobs containing VM you want to verify.  If you do not use a linked backup job, make sure that the AppGroup parameter is set. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| Description | Specifies the description of the new SureBackup job. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating SureBackup Job Using Virtual Lab, Application Group and Linked Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create the Exchange SureJob SureBackup job using a virtual lab, an application group and a linked job.  |  | | --- | | $ExchangeAppgroup = Get-VSBApplicationGroup -Name "MailServer Appgroup"  $VLab01 = Get-VSBVirtualLab -Name "MailServer VLab 01"  Get-VBRJob -Name "Exchange Backup Job" | Add-VSBJob -Name "Exchange SureJob" -VirtualLab $VLab01 -AppGroup $ExchangeAppgroup |  Perform the following steps:   1. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeAppgroup variable. 2. Run the [Get-VSBVirtualLab](get-vsbvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $VLab01 variable. 3. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 4. Pipe the cmdlet output to the Add-VSBJob cmdlet. Specify the Name parameter value. Set the $VLab01 variable as the VirtualLab parameter value. Set the $ExchangeAppgroup variable as the AppGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating SureBackup Job Using Virtual Lab and Application Group [Using Variable]

|  |  |
| --- | --- |
| This example shows how to create the Exchange SureJob SureBackup job using a virtual lab and an application group.  |  | | --- | | $ExchangeAppgroup = Get-VSBApplicationGroup -Name "MailServer Appgroup"  $VLab01 = Get-VSBVirtualLab -Name "MailServer VLab 01"  Add-VSBJob -Name "Exchange SureJob" -VirtualLab $VLab01 -AppGroup $ExchangeAppgroup |  Perform the following steps:   1. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeAppgroup variable. 2. Run the [Get-VSBVirtualLab](get-vsbvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $VLab01 variable. 3. Run the Add-VSBJob cmdlet. Specify the Name parameter value. Set the $VLab01 variable as the VirtualLab parameter value. Set the $ExchangeAppgroup variable as the AppGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating SureBackup Job Using Virtual Lab and Application Group [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create the Exchange SureJob SureBackup job using a virtual lab and an application group.  |  | | --- | | $ExchangeAppgroup = Get-VSBApplicationGroup -Name "MailServer Appgroup"  Get-VSBVirtualLab -Name "Exchange VLab 01" | Add-VSBJob -Name "Exchange SureJob" -AppGroup $ExchangeAppgroup |  Perform the following steps:   1. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeAppgroup variable. 2. Run the [Get-VSBVirtualLab](get-vsbvirtuallab.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Add-VSBJob cmdlet. Specify the Name parameter value. Set the $ExchangeAppgroup variable as the AppGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Creating SureBackup Job Using Virtual Lab and Linked Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to create the Exchange SureJob SureBackup job using a virtual lab and a linked job.  |  | | --- | | $ExchangeBackup = Get-VBRJob -Name "Exchange Backup Job"  $VLab01 = Get-VSBVirtualLab -Name "MailServer VLab 01"  Add-VSBJob -Name "Exchange SureJob" -VirtualLab $VLab01 -LinkedJob $ExchangeBackup |  Perform the following steps:   1. Run the [Get-VSBApplicationGroup](get-vsbapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $ExchangeAppgroup variable. 2. Run the [Get-VSBVirtualLab](get-vsbvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $VLab01 variable. 3. Run the Add-VSBJob cmdlet. Specify the Name parameter value. Set the $VLab01 variable as the VirtualLab parameter value. Set the $ExchangeAppgroup variable as the AppGroup parameter value. |

Related Commands

* [Get-VSBVirtualLab](get-vsbvirtuallab.md)
* [Get-VSBApplicationGroup](get-vsbapplicationgroup.md)
* [Get-VBRJob](get-vbrjob.md)


