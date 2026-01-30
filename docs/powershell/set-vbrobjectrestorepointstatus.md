---
title: "Set-VBRObjectRestorePointStatus"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrobjectrestorepointstatus.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# Set-VBRObjectRestorePointStatus


Short Description

Modifies the malware status of restore points.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRObjectRestorePointStatus -RestorePoint <VBRObjectRestorePoint> -Status {Clean | Suspicious | Infected}  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the malware status of restore points.

|  |
| --- |
| Important |
| The cmdlet does not return an output. To get details on the updated malware status of restore points, run the [Get-VBRObjectRestorePoint](get-vbrobjectrestorepoint.md) cmdlet. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies restore points which malware status you want to modiffy. | Accepts the VBRObjectRestorePoint object. To get this object, run the [Get-VBRObjectRestorePoint](get-vbrobjectrestorepoint.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| Status | Specifies one of the following malware status:   * Clean * Suspicious * Infected | VBRActivitySeverity | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Modifying Malware Status of Restore Points

This example shows how to set the Clean status for restore points.

|  |
| --- |
| $rp = Get-VBRObjectRestorePoint -Id "2ee79fec-9aa8-4058-a147-ff6b76ef2924"  Set-VBRObjectRestorePointStatus -RestorePoint $rp[0] -Status Clean |

Perform the following steps:

1. Run the [Get-VBRObjectRestorePoint](get-vbrobjectrestorepoint.md) cmdlet. Specify the Id parameter value. Save the result to the $rp variable.

The Get-VBRObjectRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the first restore session in the array).

1. Run the Set-VBRObjectRestorePointStatus cmdlet. Set the $rp variable as the RestorePoint parameter value. Set the Clean option for the Status parameter.

Related Commands

[Get-VBRObjectRestorePoint](get-vbrobjectrestorepoint.md)


