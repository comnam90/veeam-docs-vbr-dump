---
title: "New-VBROracleRMANOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbroraclermanoptions.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# New-VBROracleRMANOptions


Short Description

Creates the Oracle RMAN backup settings for application backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBROracleRMANOptions [-ParallelChannelsCount <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies to application backup policies for Veeam Plug-In for Oracle RMAN.

This cmdlet creates Oracle RMAN backup settings. You can run this cmdlet to allow Veeam Plug-In to send application backups to the target storage using several parallel data channels.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ParallelChannelsCount | Specifies the integer defining the number of data channels that can be assigned. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBROracleRMANOptions object that defines Oracle RMAN backup settings.

Examples

Creating Oracle RMAN Backup Settings for Application Backup Policies for Veeam Plug-In for Oracle RMAN

This command creates the Oracle RMAN backup settings for application backup policies for Veeam Plug-In for Oracle RMAN. The policy will send application backups to the target storage using 3 parallel data channels.

|  |
| --- |
| New-VBROracleRMANOptions -ParallelChannelsCount 3 |


