---
title: "Disconnect-VBRGoogleCloudService"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disconnect-vbrgooglecloudservice.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Disconnect-VBRGoogleCloudService

In this article

Short Description

Stops active sessions with Google Cloud object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disconnect-VBRGoogleCloudService -Connection <VBRGoogleCloudConnection>  [<CommonParameters>] |

Detailed Description

This cmdlet stops active sessions with Google Cloud object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies a session with Google Cloud object storage that you want to stop. | Accepts the VBRGoogleCloudConnection object. To create this object, run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Disconnecting Google Cloud Service

This example shows how to stops an active session with Google Cloud object storage.

|  |
| --- |
| $account = Get-VBRGoogleCloudAccount -AccessKey "ABCDEFGHIGKLMNOP"  $session = Connect-VBRGoogleCloudService -Account $account -ServiceType CapacityTier  Disconnect-VBRGoogleCloudService -Connection $session |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md) cmdlet. Specify the Account and the ServiceType parameters value. Save the result to the $session variable.
3. Run the Disconnect-VBRGoogleCloudService cmdlet. Set the $session variable as the Connection parameter value.

Related Commands

* [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)

* [Connect-VBRGoogleCloudService](connect-vbrgooglecloudservice.md)

Page updated 2/5/2024

Page content applies to build 13.0.1.1071
