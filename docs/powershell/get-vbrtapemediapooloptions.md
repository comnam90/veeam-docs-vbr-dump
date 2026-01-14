---
title: "Get-VBRTapeMediaPoolOptions (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrtapemediapooloptions.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Get-VBRTapeMediaPoolOptions (obsolete)

In this article

Short Description

Returns settings of a selected media pool.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Get-VBRTapeMediaPoolOptions -MediaPool <MediaPool> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns settings applied to a selected media pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| MediaPool | Specifies the media pool for which you want to get the settings. | Accepts the MediaPool object. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | True (by Value FromPipeline, ValueFromPipeline ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Related Commands

[Get-VBRTapeMediaPool](get-vbrtapemediapool.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
