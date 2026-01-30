---
title: "Set-VBRApplicationGroup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrapplicationgroup.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRApplicationGroup


Short Description

Modifies settings of application groups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRApplicationGroup -ApplicationGroup <VBRApplicationGroup> [-VM <VBRSureBackupVM[]>] [-Name <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of application groups.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ApplicationGroup | Specifies an application group. The cmdlet will modify this application group. | Accepts the VBRApplicationGroup object. To get this object, run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. | True | Named | True (ByValue, |
| VM | Specifies an array of VMs. The cmdlet will add these VMs to the application group. | Accepts the VBRSureBackupVM[] object. To get this object, run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. | False | Named | False |
| Name | Specifies a name of an application group. The cmdlet will create the application group with this name. | String | False | Named | False |
| Description | Specifies a description of an application group. The cmdlet will create the application group with this description. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRApplicationGroup object that contains settings of application groups for SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying VMs Added to Application Group

|  |  |
| --- | --- |
| This example shows how to add new VMs to the existing application group.  |  | | --- | | $job = Get-VBRJob -Name "Exchange backup"  $backupobject = Get-VBRJobObject -Job $job  $vm = New-VBRSureBackupVM -VM $backupobject  $appgroup = Get-VBRApplicationGroup  Set-VBRApplicationGroup -ApplicationGroup $appgroup -VM $vm |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $backupobject variable. 3. Run the [New-VBRSureBackupVM](new-vbrsurebackupvm.md) cmdlet. Set the $backupobject variable as the VM parameter value. Save the result to the $vm variable. 4. Run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. Save the result to the $appgroup variable. 5. Run the Set-VBRApplicationGroup cmdlet. Set the $appgroup variable as the ApplicationGroup parameter value. Set the $vm variable as the VM parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Name of Application Group

|  |  |
| --- | --- |
| This example shows how to modify a name of the application group added to the Veeam Backup & Replication infrastructure.  |  | | --- | | $appgroup = Get-VBRApplicationGroup  Set-VBRApplicationGroup -ApplicationGroup $appgroup -Name "Additional Application Group" |  Perform the following steps:   1. Run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. Save the result to the $appgroup variable. 2. Run the Set-VBRApplicationGroup cmdlet. Set the $appgroup variable as the ApplicationGroup parameter value. Specify the Name parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Description of Application Group

|  |  |
| --- | --- |
| This example shows how to modify a description of the application group added to the Veeam Backup & Replication infrastructure.  |  | | --- | | $appgroup = Get-VBRApplicationGroup  Set-VBRApplicationGroup -ApplicationGroup $appgroup -Description "Application Group for Exchange verification" |  Perform the following steps:   1. Run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. Save the result to the $appgroup variable. 2. Run the Set-VBRApplicationGroup cmdlet. Set the $appgroup variable as the ApplicationGroup parameter value. Specify the Description parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRJobObject](get-vbrjobobject.md)
* [New-VBRSureBackupVM](new-vbrsurebackupvm.md)
* [Get-VBRApplicationGroup](get-vbrapplicationgroup.md)


