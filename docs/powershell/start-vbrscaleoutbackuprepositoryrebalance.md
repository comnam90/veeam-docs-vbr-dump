---
title: "Start-VBRScaleOutBackupRepositoryRebalance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrscaleoutbackuprepositoryrebalance.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Start-VBRScaleOutBackupRepositoryRebalance

In this article

Short Description

Starts to rebalance data of scale-out backup repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRScaleOutBackupRepositoryRebalance -Repository <VBRScaleOutBackupRepository> [-RunAsync] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts to rebalance data between extents of scale-out backup repositories.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies a scale-out backup repository which extents you want to rebalance. | Accepts the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet and provide the ScaleOut parameter. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will starts to rebalance data between extents without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting Scale-Out Repository Rebalance

This example shows how to start to rebalance data between extents of scale-out backup repositories.

|  |
| --- |
| $repository = Get-VBRBackupRepository -Name "Veeam Scale-Out Repository" -ScaleOut  Start-VBRScaleOutBackupRepositoryRebalance -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Provide the ScaleOut parameter. Save the result to the $repository variable.
2. Run the Start-VBRScaleOutBackupRepositoryRebalance cmdlet. Set the $repository variable as the Repository parameter value.

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 4/19/2024

Page content applies to build 13.0.1.1071
