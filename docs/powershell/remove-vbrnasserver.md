---
title: "Remove-VBRNASServer (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrnasserver.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRNASServer (obsolete)


Short Description

Removes file shares that are added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Remove-VBRUnstructuredServer](remove-vbrunstructuredserver.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRNASServer -Server <VBRNASServer[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes file shares that are added to the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an array of file shares. The cmdlet will remove these file shares from the Veeam Backup & Replication infrastructure. | Accepts the VBRNASServer[] object. To get this object, run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing all File Shares

|  |  |
| --- | --- |
| This example shows how to remove all file shares that are added to the Veeam Backup & Replication infrastructure.  |  | | --- | | $fileshare = Get-VBRNASServer  Remove-VBRNASServer -Server $fileshare |  Perform the following steps:   1. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Save the result to the $fileshare variable. 2. Run the Remove-VBRNASServer cmdlet. Set the $fileshare variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Specific File Share

|  |  |
| --- | --- |
| This example shows how to remove the \\WinSRV2049\Documents file share that is added to the Veeam Backup & Replication infrastructure. The cmdlet will display a prompt that asks if the user is sure that he wants to continue.  |  | | --- | | $fileshare = Get-VBRNASServer -Name "\\WinSRV2049\Documents"  Remove-VBRNASServer -Server $fileshare -Confirm |  Perform the following steps:   1. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Save the result to the $fileshare variable. 2. Run the Remove-VBRNASServer cmdlet. Set the $fileshare variable as the Server parameter value. Provide the Confirm parameter. |

Related Commands

[Get-VBRNASServer](get-vbrnasserver.md)


