---
title: "Add-VBRViApplicationGroup (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrviapplicationgroup.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Add-VBRViApplicationGroup (obsolete)

In this article

Short Description

Creates VMware application groups for SureBackup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete and not supported. Run the [Add-VBRApplicationGroup](add-vbrapplicationgroup.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViApplicationGroup -VM <VBRSureBackupVM[]> [-Name <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates application groups for SureBackup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VM | Specifies an array of VMs. The cmdlet will add these VMs to the application group. | Accepts the VBRSureBackupVM[] object. To get this object, run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies a name of an application group. The cmdlet will create the application group with this name. | String | False | Named | False |
| Description | Specifies a description of an application group. The cmdlet will create the application group with this description. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRApplicationGroup object that contains settings of application groups for SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Application Group

|  |  |
| --- | --- |
| This example shows how to create an application group with default name and description.  |  | | --- | | $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job  $vm = New-VBRSureBackupVM -VM $backupobject  Add-VBRViApplicationGroup -VM $vm |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $job variable. 3. Run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. Set the $backupobject variable as the VM parameter value. Save the result to the $vm variable. 4. Run the Add-VBRViApplicationGroup cmdlet. Set the $vm variable as the VM parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Application Group with Name

|  |  |
| --- | --- |
| This example shows how to create an application group with the Microsoft Exchange Appgroup name.  |  | | --- | | $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job  $vm = New-VBRSureBackupVM -VM $backupobject  Add-VBRViApplicationGroup -VM $vm -Name "Microsoft Exchange Appgroup" |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $job variable. 3. Run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. Set the $backupobject variable as the VM parameter value. Save the result to the $vm variable. 4. Run the Add-VBRViApplicationGroup cmdlet. Set the $vm variable as the VM parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Application Group with Name and Description

|  |  |
| --- | --- |
| This example shows how to create an application group with the Microsoft Exchange Appgroup name and the Application group for Exchange-related VMs description.  |  | | --- | | $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job  $vm = New-VBRSureBackupVM -VM $backupobject  Add-VBRViApplicationGroup -VM <VBRSureBackupVM[]> -Name "Microsoft Exchange Appgroup" -Description "Application group for Exchange-related VMs" |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $job variable. 3. Run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. Set the $backupobject variable as the VM parameter value. Save the result to the $vm variable. 4. Run the Add-VBRViApplicationGroup cmdlet. Specify the following settings:  * Set the $vm variable as the VM parameter value. * Specify the Name parameter value. * Specify the Description parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRJobObject](get-vbrjobobject.md)
* [New-VBRSureBackupVM](new-vbrsurebackupvm.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
