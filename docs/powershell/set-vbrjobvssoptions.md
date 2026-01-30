---
title: "Set-VBRJobVssOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobvssoptions.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Set-VBRJobVssOptions


Short Description

Applies custom VSS settings to a selected job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Apply changes to the job VSS settings.

|  |
| --- |
| Set-VBRJobVssOptions -Job <CBackupJob[]> -Options <CGuestProcessingOptions>  [<CommonParameters>] |

* Specify and set the credentials you want to use for all the VMs in the job.

|  |
| --- |
| Set-VBRJobVssOptions -Job <CBackupJob[]> -Credentials <CCredentials>  [<CommonParameters>] |

Detailed Description

This cmdlet applies a set of customized VSS settings to a selected job.

To apply the set of customized settings you need to first create a CVssOptions object. This object unifies all the VSS options you want to apply to the job.

Run the [New-VBRJobVssOptions](new-vbrjobvssoptions.md) cmdlet to create the CVssOptions object.

Run the [Set-VBRJobObjectVssOptions](set-vbrjobobjectvssoptions.md) cmdlet to apply VSS settings to specific VMs in job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job you want to edit. | Accepts the CObjectInJob[] object. To get this object, run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. | True | 0 | True (ByValue, ByProperty Name) |
| Options | Specifies the set of parameters you want to apply to the job. | Accepts the CGuestProcessingOptions object. To get this object, run the [New-VBRJobVssOptions](new-vbrjobvssoptions.md) cmdlet. | True | 1 | False |
| Credentials | Specifies the credentials you want to use for authenticating with the guest VM. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Applying Custom VSS Options to Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to apply custom VSS options to the backup job named Backup Job 01.  |  | | --- | | $options = New-VBRJobVssOptions -ForJob  Get-VBRJob -Name "Backup Job 01" | Set-VBRJobVssOptions -Options $options |  Perform the following steps:   1. Run the [New-VBRJobVssOptions](new-vbrjobvssoptions.md) cmdlet. Provide the ForJob parameter. Save the result to the $options variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Set-VBRJobVssOptions cmdlet. Set the $options variable as the Options parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying Custom VSS Options to Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to apply custom VSS options to the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob  $options = New-VBRJobVssOptions  Set-VBRJobVssOptions -Job $job -Options $options |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Save the result to the $job variable. 2. Run the [New-VBRJobVssOptions](new-vbrjobvssoptions.md) cmdlet. Save the result to the $options variable. 3. Run the Set-VBRJobVssOptions cmdlet. Set the $job variable as the Job parameter value. Set the $options variable as the Options parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [New-VBRJobVssOptions](new-vbrjobvssoptions.md)
* [Get-VBRCredentials](get-vbrcredentials.md)


