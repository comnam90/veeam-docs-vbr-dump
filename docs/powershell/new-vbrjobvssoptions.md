---
title: "New-VBRJobVssOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrjobvssoptions.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# New-VBRJobVssOptions


Short Description

Returns default set of VSS options for job or VM in job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Set default VSS settings for backup jobs (including Cloud Director backup jobs).

|  |
| --- |
| New-VBRJobVssOptions [-ForJob]  [<CommonParameters>] |

* Set default VSS settings for VMs in job.

|  |
| --- |
| New-VBRJobVssOptions [-ForObject]  [<CommonParameters>] |

* Set default VSS settings for replication jobs.

|  |
| --- |
| New-VBRJobVssOptions [-ForReplicaJob]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the CVssOptions object. This object contains default VSS settings for backup jobs, replication jobs or selected VMs. Use an appropriate parameter set for each case.

You can modify the settings and use this object to change the VSS settings of a job or VM. Run the [Set-VBRJobVssOptions](set-vbrjobvssoptions.md) cmdlet to apply the VSS settings to a job.

|  |
| --- |
| ![New-VBRJobVssOptions](images/icon_tip.webp) Tip: |
| Save the object to a variable when you customize settings: this variable can be used in several jobs. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ForJob | Defines that the cmdlet will return the list of the default VSS settings for backup, replication or copy job. | SwitchParameter | False | Named | False |
| ForObject | Defines that the cmdlet will return the list of the default VSS settings for VMs. | SwitchParameter | False | Named | False |
| ForReplicaJob | Defines that the cmdlet will return the list of the default VSS settings for replication job. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting CVssOptions Object for Backup Job

This example shows how to get the CVssOptions object with customized VSS settings for a backup job.

|  |
| --- |
| $o = New-VBRJobVssOptions -ForJob  $o.Enabled = $true  $o.GuestFSIndexingType = "Everyfolders"  $o.TransactionLogsTruncation = "Always" |

Perform the following steps:

1. Run the New-VBRJobVssOptions cmdlet. Provide the ForJob parameter. Save the result to the $o variable.

1. Modify the VSS settings. Specify the following settings:

* Provide the $true value for the Enabled property of the $o variable.
* Provide the Everyfolders value for the GuestFSIndexingType property of the $o variable.
* Provide the Always value for the TransactionLogsTruncation property of the $o variable.


