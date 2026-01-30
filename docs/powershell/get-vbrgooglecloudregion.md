---
title: "Get-VBRGoogleCloudRegion"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrgooglecloudregion.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGoogleCloudRegion


Short Description

Returns Google Cloud regions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGoogleCloudRegion -Connection <VBRGoogleCloudConnection> [-RegionId <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Google Cloud regions.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Google Cloud. The cmdlet will return an array of all Google Cloud regions from this session. | Accepts the VBRGoogleCloudConnection object. To get this object, run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RegionId | Specifies an ID of Google Cloud region. The cmdlet will return the Google Cloud region with this IDs. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRGoogleCloudRegion object that contains an array of Google Cloud regions.

Examples

Getting Google Cloud Regions

This example shows how to get Google Cloud regions.

|  |
| --- |
| $account = Get-VBRGoogleCloudAccount -Id "936edf7c-7cf3-4dbd-9895-c7485ef4bb2c"  $connection = Connect-VBRGoogleCloudService -Account $account -ServiceType CapacityTier  Get-VBRGoogleCloudRegion -Connection $connection |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the Id parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. Specify the Account and ServiceType parameter values. Save the result to the $connection variable.
3. Run the Get-VBRGoogleCloudRegion cmdlet. Set the $connection variable as the Connection parameter value.

Related Commands

* [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)
* [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md)


