---
title: "Install-VBRLicense"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/install-vbrlicense.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# Install-VBRLicense


Short Description

Installs licenses on a backup server.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Install-VBRLicense -Path <String> [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet installs licenses on a backup server.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies a path to the license file. The cmdlet will install a license from this license file. | String | True | Named | False |
| Force | Defines that the cmdlet will install Veeam Backup & Replication license without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Installing Veeam Backup & Replication License

This command installs a Veeam Backup & Replication license.

|  |
| --- |
| Install-VBRLicense -Path "C:\Users\Administrator\Downloads\veeam\_license.lic" |


