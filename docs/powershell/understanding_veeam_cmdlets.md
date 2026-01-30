---
title: "Understanding Veeam Cmdlets"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/understanding_veeam_cmdlets.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Understanding Veeam Cmdlets


A cmdlet is a specialized .NET class that interacts with Microsoft .NET Framework objects. Each cmdlet acts as a single-function command that can perform multiple operations with these objects. Objects represent instances of the Veeam backup infrastructure: jobs, databases, restore sessions and so on.

Each cmdlet has parameters that pass additional object data to cmdlet. Parameters can be either required or optional. You will not be able to run a cmdlet without specifying the required parameters, while the optional parameters can be omitted. Parameters are organized into parameter sets that form a syntax of the cmdlet.

Cmdlets and their parameters are named after the Windows PowerShell naming conventions. Veeam cmdlets are developed to behave like other Microsoft Windows cmdlets.

Working with Veeam PowerShell cmdlets and scripts in many respects depends on your imagination, skills and expertise in Windows PowerShell. To learn more about Windows PowerShell, see this [Microsoft article](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-6).

|  |
| --- |
| Note |
| Veeam Support does not write scripts on demand. Custom script troubleshooting is not supported. |

Platform

Some Veeam cmdlets differ for VMware and Hyper-V platforms. A prefix indicates the platform: 'Vi' stands for VMware, and 'Hv' stands for Hyper-V. A Vi-cmdlet will not work for Hyper-V instances, and vice versa. For example, the [Add-VBRViBackupJob](add-vbrvibackupjob.md) cmdlet creates a backup job for VMware VMs, but if you need to back up Hyper-V VMs, you need to run the [Add-VBRHvBackupJob](add-vbrhvbackupjob.md) cmdlet. Some cmdlets work for both platforms, like the [Get-VBRJob](get-vbrjob.md) cmdlet. You can additionally check the platform in the Applies to section on the online help page for each cmdlet.

Input and Output

As an input, the cmdlets expect objects, and they output objects. The objects mostly represent instances of the backup infrastructure: VMs, jobs, job settings, failover plans and so on. See [Veeam PowerShell Objects](veeam_powershell_types.md) for objects properties. The objects can be part of a pipeline.

You can use the cmdlet help to understand what kind of input is needed. The cmdlets have syntax that shows the whole set of parameters available in the cmdlet and what each parameter expects as input. For example, the [Add-VBRHvProxy](add-vbrhvproxy.md) cmdlet has the following syntax:

|  |
| --- |
| Add-VBRHvProxy -Server <CHost> [-Description <String>] [-MaxTasks <Int32>]  [<CommonParameters>] |

That means that to add a new Hyper-V proxy, you need to indicate a server that will act as the proxy, the description of the new proxy and a number of tasks that the proxy can perform simultaneously.

Some cmdlets have two or more parameter sets. For example, restore cmdlets offer a 'simplified' parameter set for restoring to original location, while the parameter set for restoring to another location allows to indicate the target server and other detail and these parameters are mandatory for this set.

|  |
| --- |
| Important |
| Veeam PowerShell does not support the use of square brackets in the names of Veeam backup infrastructure components. |


