---
title: "Set-VBRTapeMediaPoolOptions (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrtapemediapooloptions.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Set-VBRTapeMediaPoolOptions (obsolete)


Short Description

Modifies media pool options.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but it is recommended to perform the tape restore operation with Veeam Backup & Replication UI for full functionality. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRTapeMediaPoolOptions -MediaPool <CTapeMediaPool> -Options <PSMediaPoolOptions>  [<CommonParameters>] |

Detailed Description

Modifies media pool options.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| MediaPool | Specifies the media pool that you want to modify. | Accepts the CTapeMediaPool object. To create this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Options | Specifies the media pool options. The cmdlet will modify these options. | Accepts the PSMediaPoolOptions object. To create this object, run the  cmdlet. | True | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Related Commands

[Get-VBRTapeMediaPool](get-vbrtapemediapool.md)


