---
title: "New-VBRManuallyDeployedContainer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmanuallydeployedcontainer.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRManuallyDeployedContainer


Short Description

Defines a scope of Veeam Agent setup files.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRManuallyDeployedContainer -Path <String> [-WindowsPackage] [-MacPackage] [-LinuxPackage <VBRProtectionGroupLinuxPackage[]>] [-UnixPackage <VBRProtectionGroupUnixPackage[]>] [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRManuallyDeployedContainer](vbrmanuallydeployedcontainer.md) object. This object defines a scope of Veeam Agent setup files that will be exported to computers in a protection group for pre-installed Veeam Agents after you create the protection group. To learn more about the protection group for pre-installed Veeam Agents, see the [Protection Group Types](https://helpcenter.veeam.com/docs/backup/agents/protection_groups_types.html?ver=120) section in the Veeam Agent Management Guide.

|  |
| --- |
| Note |
| Keep in mind that the cmdlet does not define a scope of computers you can add to a protection group for pre-installed Veeam Agents. To learn how to add computers to a protection group for pre-installed Veeam Agents, see the [Deploying Veeam Agents Using Generated Setup Files](https://helpcenter.veeam.com/docs/vbr/userguide/agents_deploy_with_generated_file.html?ver=13) section in the Veeam Agent Management Guide. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies a path to the folder to which Veeam Backup & Replication will export Veeam Agent setup files. | String | True | Named | True (ByValue, ByPropertyName) |
| WindowsPackage | Defines that the cmdlet will export Veeam Agent for Microsoft Windows setup files.  Default: False. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |
| MacPackage | Defines that the cmdlet will export Veeam Agent for macOS setup files.  Default: False. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |
| LinuxPackage | Specifies an array of Linux-based setup files. | Accepts the [VBRProtectionGroupLinuxPackage](vbrprotectiongrouplinuxpackage.md)[] object. To create this object, run the [Get-VBRProtectionGroupLinuxPackage](get-vbrprotectiongrouplinuxpackage.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| UnixPackage | Specifies an array of Unix-based setup files. | Accepts the [VBRProtectionGroupUnixPackage](vbrprotectiongroupunixpackage.md)[] object. To create this object, run the [Get-VBRProtectionGroupUnixPackage](get-vbrprotectiongroupunixpackage.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRManuallyDeployedContainer](vbrmanuallydeployedcontainer.md) object that defines a scope of Veeam Agent setup files that you want to export to computers.

Examples

Defining Scope of Veeam Agent Microsoft Windows Setup Files

This command will export Veeam Agent for Microsoft Windows setup files to the C:\container folder path after you create a protection group for pre-installed Veeam Agents.

|  |
| --- |
| New-VBRManuallyDeployedContainer -Path "C:\container" -WindowsPackage |


