---
title: "Set-VBRJobAdvancedViOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobadvancedvioptions.html"
last_updated: "3/21/2024"
product_version: "13.0.1.1071"
---

# Set-VBRJobAdvancedViOptions


Short Description

Customizes VMware job settings.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobAdvancedViOptions [-EnableChangeTracking <Boolean>] [-ExcludeSwapFile <Boolean>] -Job <CBackupJob[]> [-SetResultsToVmAttribute <Boolean>] [-UseChangeTracking <Boolean>] [-VmAttributeName <String>] [-VMToolsQuiesce <Boolean>]  [<CommonParameters>] |

Detailed Description

This cmdlet sets special options for the selected VMware job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will modify advanced VMware backup options of these jobs. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| ExcludeSwapFile | Defines whether the swap file will be excluded from backup.   * True: the swap file will be excluded from backup. * False: the swap file will not be excluded from backup.   Default: True. | Bool | False | Named | False |
| VmAttributeName | Specifies the custom attributes field name. | String | False | Named | False |
| SetResultsToVmAttribute | Defines whether the job results will be written to custom attributes field of the VM.   * True: the job results will be written to custom attributes field of the VM. * False: the job results will not be written to custom attributes field of the VM. | Bool | False | Named | False |
| EnableChangeTracking | Defines whether the changed block tracking will be enabled.   * True: the changed block tracking will be enabled. * False: the changed block tracking will be disabled.   Default: True. | Bool | False | Named | False |
| UseChangeTracking | Defines whether the changed block tracking will be used even if CBT is disabled on the ESXi host.   * True: the changed block tracking will be used. * False: the changed block tracking will not be used.   Default: True. | Bool | False | Named | False |
| VMToolsQuiesce | Defines whether the VMware quiescence mechanism will be enabled.   * True: the VMware quiescence mechanism will be enabled. * False: the VMware quiescence mechanism will not be enabled.   Use this mechanism if the application-aware processing cannot be used.  Default: False. | Bool | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Editing Advanced Job Settings to Specific Backup Job [Using Pipeline]

This example shows how to edit the advanced job settings to backup job named Backup Job 01:

* The VMware quiescence is enabled.
* The changed block data is enabled.
* The CBT is forced to use despite the ESXi host settings.
* The swap file is excluded form backup.

|  |
| --- |
| Get-VBRJob -Name "Backup Job 01" | Set-VBRJobAdvancedViOptions -VMToolsQuiesce $True -EnableChangeTracking $True -UseChangeTracking $True -ExcludeSwapFile $True |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value.
2. Pipe the cmdlet output to the Set-VBRJobAdvancedViOptions cmdlet. Specify the following settings:

* Provide the $True value for the VmToolsQuiesce parameter.
* Provide the $True value for the EnableChangeTracking parameter.
* Provide the $True value for the UseChangeTracking parameter.
* Provide the $True value for the ExcludeSwapFile parameter.

Related Commands

[Get-VBRJob](get-vbrjob.md)


