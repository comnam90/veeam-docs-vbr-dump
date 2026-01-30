---
title: "Updated Cmdlets"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/updated_cmdlets_12.2.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Updated Cmdlets


This section contains information on cmdlets updated in Veeam PowerShell v12.2.

Data Recovery

In this version, the following scenarios are supported:

* [For restore of Linux-based or Unix-based guest OS files] You can use credentials to authenticate against a backup repository where the backup from which you restore is located.
* [For restore of f Microsoft Windows guest OS files and folders] Specifies the target Veeam Agent computer to which the cmdlet will restore guest OS files.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) | New parameter added: ShareCredentials. | | [Start-VBRCDPLinuxFileRestore](start-vbrcdplinuxfilerestore.md) | New parameter added: ShareCredentials. | | [Start-VBRWindowsGuestItemRestore](start-vbrwindowsguestitemrestore.md) | New parameter added: TargetAgentMachine. | |

Veeam Agent Management

In this version, you can include to the backup scope data stored in the Library folder on the system volume of Mac computers.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBRSelectedPersonalFolders](new-vbrselectedpersonalfolders.md) | New parameter added: Library. | | [Set-VBRSelectedPersonalFolders](set-vbrselectedpersonalfolders.md) | New parameter added: Library. | |

Veeam Plug-Ins for Enterprise Applications

This section describes changes for managing application backup policies for Veeam Plug-In for Oracle RMAN.

Application Backup Policy Settings for Veeam Plug-In for Oracle RMAN

In this version, you can select one of the authentication methods to connect to Oracle RMAN hosts and databases:

* Only OS authentication.
* OS and database credentials simultaneously.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [New-VBROracleRMANProcessingOptions](new-vbroraclermanprocessingoptions.md) | New parameters added: AuthenticationMode, DBCredentials. | | [Set-VBROracleRMANProcessingOption](set-vbroraclermanprocessingoptions.md) | New parameters added: AuthenticationMode, DBCredentials. | |


