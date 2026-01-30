---
title: "Add-VBRTapeFilesJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrtapefilesjob.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Add-VBRTapeFilesJob (obsolete)


Short Description

Creates a new files to tape copy job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to create a new files to tape copy job using the [Add-VBRFileToTapeJob](add-vbrfiletotapejob.md) cmdlet. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Add-VBRTapeFilesJob [-Name <String>] -Server <CHost> -Path <String[]> -MediaPool <MediaPool> [-MediaPoolIncremental <MediaPool>] [-Description <String>] [-Credentials <CCredentials>] [-Masks <String>] [-IgnoreCase] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new job copying files from Veeam Backup & Replication to tape. The tape job looks for changes in the specified files that have been made from the moment of the last tape job run.

Note that when you create a copy job, you need to run it manually.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the created job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the new files to tape copy job.  You can input string up to 255 symbols. | String | False | Named | False |
| Server | Specifies the source server where the files you need are located. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Path | Specifies the path to the folders you need to copy. Use Masks and IgnoreCase parameters to select particular files.  You can specify multiple names separated by commas. | String[] | True | Named | True (ByValue, ByProperty Name) |
| MediaPool | Specifies the target media pool that will be used for full backups. | Accepts the MediaPool object. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| MediaPool Incremental | Specifies the target media pool that will be used for incremental backups. | Accepts the MediaPool object. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| Description | Specifies the description for the new files to tape copy job. | String | False | Named | False |
| Credentials | Specifies the credentials you want to use for authenticating with the source server. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | False | Named | False |
| Masks | Used to specify search conditions for Path paramater.  Specifies masks to select files in folders. | String | False | Named | False |
| IgnoreCase | Used to specify search conditions for Path paramater.  If set, the search by name will be non case sensitive. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating New Files to Tape Job

|  |  |
| --- | --- |
| This example shows how to create a new files to tape job named Contacts Copy Job.  |  | | --- | | $server = Get-VBRServer -Name "srv01"  $full = Get-VBRTapeMediaPool -Name "File Backup Media Pool Full"  $increment = Get-VBRTapeMediaPool -Name "File Backup Media Pool Incremental"  Add-VBRTapeFilesJob -Name "Contacts Copy Job" -Server $server -Path "D:\Users\UserInfo\Contacts.xls" -MediaPool $full -MediaPoolIncremental $increment |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save it to the $server variable. 2. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $full variable. 3. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $increment variable. 4. Run the Add-VBRTapeFilesJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Set the $full variable as the MediaPool parameter value. * Set the $increment variable as the MediaPoolIncremental parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Files to Tape Job with Masks

|  |  |
| --- | --- |
| This example shows how to create the Agreements Copy Job files to tape job copying .pdf files from the Signed folder.  |  | | --- | | $server = Get-VBRServer -Name "srv01"  $full = Get-VBRTapeMediaPool -Name "File Backup Media Pool Full"  $increment = Get-VBRTapeMediaPool -Name "File Backup Media Pool Incremental"  $Administrator = Get-VBRCredentials  Add-VBRTapeFilesJob -Name "Agreements Copy Job" -Server $server -Path "D:\Agreements\Signed" -MediaPool $full -MediaPoolIncremental $increment -Description "Agreements File Copy Job" -Credentials $Administrator -Masks "\*.pdf" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save it to the $server variable. 2. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $full variable. 3. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $increment variable. 4. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save it to the $Administrator variable. 5. Run the Add-VBRTapeFilesJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $server variable as the Server parameter value. * Specify the Path parameter value. * Set the $full variable as the MediaPool parameter value. * Set the $increment variable as the MediaPoolIncremental parameter value. * Specify the Description parameter value. * Set the $Administrator variable as the Credentials parameter value. * Specify the Masks parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [Get-VBRCredentials](get-vbrcredentials.md)


