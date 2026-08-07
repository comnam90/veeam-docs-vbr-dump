---
title: "Validate-VBRDiscoveredComputerRecoveryMedia"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/validate-vbrdiscoveredcomputerrecoverymedia.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Validate-VBRDiscoveredComputerRecoveryMedia


Short Description

Verifies that Veeam Recovery Media is valid.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Validate-VBRDiscoveredComputerRecoveryMedia -Hash <String> [<CommonParameters>] |

Detailed Description

This cmdlet verifies that Veeam Recovery Media was created by Veeam Backup & Replication and can be trusted. To verify a recovery media file, calculate its hash and pass it to the cmdlet. If a record with this hash exists, the cmdlet returns audit information about the media.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Hash | Specifies the hash calculated over the Veeam Recovery Media file that you want to verify. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRRecoveryMediaAudit](vbrrecoverymediaaudit.md) object that contains audit information about the Veeam Recovery Media.

Examples

Verifying Veeam Recovery Media

This command verifies the Veeam Recovery Media with the specified hash.

|  |
| --- |
| Validate-VBRDiscoveredComputerRecoveryMedia -Hash "2C26B46B68FFC68FF99B453C1D30413D" |

Related Commands

[Add-VBRDiscoveredComputerRecoveryMedia](add-vbrdiscoveredcomputerrecoverymedia.md)

Page updated 2026-06-04

