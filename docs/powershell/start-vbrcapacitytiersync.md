---
title: "Start-VBRCapacityTierSync"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcapacitytiersync.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Start-VBRCapacityTierSync


Short Description

Starts to offload data stored on the performance tier to capacity tier.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRCapacityTierSync -Repository <VBRScaleOutBackupRepository> [-ApproximateOffloadSizeGB <Int64>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts to offload data stored on the performance tier to capacity tier.

|  |
| --- |
| Important |
| Consider the following:   * You cannot offload data from the performance extents are set to the Maintenance mode to capacity tier. * Run the [Disable-VBRCapacityExtentMaintenanceMode](disable-vbrcapacityextentmaintenancemode.md) cmdlet to disable the Maintenance mode for the necessary performance extent. * If you provide the ApproximateOffloadSizeGB parameter, the cmdlet will move backups to capacity tier and delete them from performance tier. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies a scale-out backup repository. The cmdlet will return the performance extents added to this repository. | Accepts the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) object. to get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| ApproximateOffloadSizeGB | Specifies an approximate size of data that you want to offload to the capacity tier.  Note: If you provide this parameter, the cmdlet will move backups to capacity tier and delete them from performance tier. | Int64 | False | Named | True (ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Offloading Data From Performance Tier to Capacity Tier

|  |  |
| --- | --- |
| This example shows how to start offload data from the performance tier to the capacity tier. We recommend using this script if you have several scale-out repositories and would like to synchronize data on a specific repository.  |  | | --- | | $repository = Get-VBRBackupRepository -ScaleOut  Start-VBRCapacityTierSync -Repository $repository[1] |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the ScaleOut parameter. Save the result to the $repository variable.   The Get-VBRBackupRepository cmdlet will return an array of scale-out repositories. Mind the ordinal number of the necessary repository (in our example, it is the second scale-out repository in the array).   1. Run the Start-VBRCapacityTierSync cmdlet. Set the $repository variable as the Repository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Offloading Data From Performance Tier to Capacity Tier [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to sync data stored on the performance tier with the data on capacity tier. We recommend using this script if you do not want to specify an ordinal number of a scale-out repository.  |  | | --- | | Get-VBRBackupRepository -ScaleOut | ForEach-Object {Start-VBRCapacityTierSync -Repository $\_ -RunAsync} |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the ScaleOut parameter. 2. Pipe the cmdlet output to the [ForEach-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.3) cmdlet:  * Run the Start-VBRCapacityTierSync cmdlet. * Set the $\_ value for the Repository parameter. Provide the RunAsync parameter. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [ForEach-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.3)


