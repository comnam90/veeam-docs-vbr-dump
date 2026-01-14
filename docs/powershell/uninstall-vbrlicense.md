---
title: "Uninstall-VBRLicense"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrlicense.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Uninstall-VBRLicense

In this article

Short Description

Removes a license from a backup server.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Uninstall-VBRLicense [-Instance] [-Socket] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a license from a backup server.

|  |
| --- |
| ![Uninstall-VBRLicense](images/icon_note.webp) Note: |
| By default, details about both per-instance and per-socket objects are removed. To remove details about either per-instance or per-socket objects, you must specify the necessary parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Instance | Defines that the cmdlet will remove details about per-instance objects from the license scope.  Default: False. | SwitchParameter | False | Named | False |
| Socket | Defines that the cmdlet will remove details about per-socket objects from the license scope.  Default: False. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing License from Backup Server

This command removes a license from a backup server. The details about both per-instance and per-socket objects are removed.

|  |
| --- |
| Uninstall-VBRLicense |

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
