---
title: "Set-VBRJobProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobproxy.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Set-VBRJobProxy


Short Description

Modifies settings of a backup proxy.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Assign specific backup proxies to a job.

|  |
| --- |
| Set-VBRJobProxy -Job <CBackupJob[]> -Proxy <IProxy[]> [-Target]  [<CommonParameters>] |

* Set automatic proxy selection.

|  |
| --- |
| Set-VBRJobProxy -Job <CBackupJob[]> -AutoDetect [-Target]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a backup proxy.

You can run this cmdlet with backup jobs and replica jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

|  |
| --- |
| Important |
| If you want to set a custom proxy, make sure that the proxy server is added to the backup infrastructure console, otherwise you will not be able to assign it to the job. The custom proxy server must be configured appropriately. For more information on proxy server settings, see [Adding VMware Backup Proxies](https://helpcenter.veeam.com/docs/vbr/userguide/add_vmware_proxy.html?ver=13) section in the Veeam Backup & Replication User Guide. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of jobs. The cmdlet will return proxies assigned to these jobs. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByValue, |
| Proxy | Specifies an array of proxies you want to assign to the job. | Accepts the IProxy[] object. To get this object, run the [Get-VBRViProxy](get-vbrviproxy.md) or [Get-VBRHvProxy](get-vbrhvproxy.md) cmdlet. | True | Named | False |
| AutoDetect | Defines that the automatic selection mode is enabled.  If you provide this parameter, the proxy server selection mode will be set to automatic. Otherwise, you must specify the custom proxy server.  Use the Proxy parameter to specify the custom proxy server.  Default: False. | SwitchParameter | True | Named | False |
| Target | Defines that the autodetect option will be enabled for the target proxy server.  If you provide this parameter, the automatic selection mode will be enabled for the target proxy server.  Otherwise, the automatic selection mode will be enabled for the source proxy server.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CBackupJob[] object that contains an array of jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Assigning Hyper-V Proxy to Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to assign the custom Hyper-V target proxy to the Backup Copy job. The name of the proxy is Local Backup Proxy. The Target parameter is set to enable target proxy allocation.  |  | | --- | | $job = Get-VBRJob -Name "Backup Copy"  $proxy = Get-VBRHvProxy -Name "Local Backup Proxy"  Set-VBRJobProxy -Job $job -Proxy $proxy -Target |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRHvProxy](get-vbrhvproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 3. Run the Set-VBRJobProxy cmdlet. Set the $job variable as the Job parameter value. Set the $proxy variable as the Proxy parameter value. Provide the Target parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Assigning VMware Proxies to Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to assign the custom VMware source proxy to the Backup Job 01 and Backup Job 02 backup jobs. The name of the proxy is Local Backup Proxy. The Target parameter is not set to enable the source proxy allocation.  |  | | --- | | $proxy = Get-VBRViProxy -Name "Local Backup Proxy"  Get-VBRJob -Name "Backup Job 01", "Backup Job 02" | Set-VBRJobProxy -Proxy $proxy |  Perform the following steps:   1. Run the [Get-VBRViProxy](get-vbrviproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter values. 3. Pipe the cmdlet output to the Set-VBRJobProxy cmdlet. Set the $proxy variable as the Proxy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Setting Automatic Proxy Selection to Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set the automatic proxy selection to the Backup Job 01 and Backup Job 02 backup jobs. The Target parameter is not set to enable the source proxy allocation.  |  | | --- | | Get-VBRJob -Name "Backup Job 01", "Backup Job 02" | Set-VBRJobProxy -AutoDetect |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter values. 2. Pipe the cmdlet output to the Set-VBRJobProxy cmdlet. Provide the AutoDetect parameter. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRViProxy](get-vbrviproxy.md)
* [Get-VBRHvProxy](get-vbrhvproxy.md)


