---
title: "Remove-VBRvCDReplica"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrvcdreplica.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRvCDReplica


Short Description

Removes Cloud Director replicas.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Removes Cloud Director replicas from the backup infrastructure.

|  |
| --- |
| Remove-VBRvCDReplica -Replica <VBRvCDReplica> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Removes Cloud Director replicas from disk.

|  |
| --- |
| Remove-VBRvCDReplica -Replica <VBRvCDReplica> -FromDisk [-RunAsync] [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Cloud Director replicas.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Replica | Specifies a Cloud Director replica that you want to remove. | Accepts the VBRvCDReplica object. To get this object, run the [Get-VBRvCDReplica](get-vbrvcdreplica.md) cmdlet. | True | Named | False |
| FromDisk | Defines that the cmdlet will remove a Cloud Director replica from a disk. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will remove  a Cloud Director without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Cloud Director Replica

This cmdlet removes a Cloud Director replica from the backup infrastructure.

|  |
| --- |
| $replica = Get-VBRvCDReplica -Id "2a7c321c-c8cf-4aec-9332-93882e69c667"  Remove-VBRvCDReplica -Replica $replica |

Perform the following steps:

1. Run the [Get-VBRvCDReplica](get-vbrvcdreplica.md) cmdlet. Specify the Id parameter value. Save the result to the $replica variable.
2. Run the Remove-VBRvCDReplica cmdlet. Set the $replica variable as the Replica parameter value.

Related Commands

[Get-VBRvCDReplica](get-vbrvcdreplica.md)


