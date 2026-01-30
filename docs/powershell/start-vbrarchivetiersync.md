---
title: "Start-VBRArchiveTierSync"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrarchivetiersync.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Start-VBRArchiveTierSync


Short Description

Starts the archiving job.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRArchiveTierSync -Repository <VBRScaleOutBackupRepository> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the archiving job that moves data from the capacity tier to the archive tier.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies a scale-out backup repository. The cmdlet will return the performance extents added to this repository. | Accepts the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRArchiveTierSync object that contains details on the archiving job.

Examples

Starting Archiving Job

This example shows how to start an archiving job.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut  Start-VBRArchiveTierSync -Repository $repository |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter. Save the result to the $repository variable.
2. Run the Start-VBRArchiveTierSync cmdlet. Set the $repository variable as the Repository parameter value.

Related Commands

[Get-VBRBackupRepository](get-vbrbackuprepository.md)


