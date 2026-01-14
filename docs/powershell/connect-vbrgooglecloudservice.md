---
title: "Connect-VBRGoogleCloudService"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrgooglecloudservice.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Connect-VBRGoogleCloudService

In this article

Short Description

Connects to Google Cloud object storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VBRGoogleCloudService -Account <VBRGoogleCloudAccount> -ServiceType <VBRGoogleCloudServiceType> [-GatewayServer <CHost[]>] [-ConnectionType <VBRRepositoryConnectionType>]  [<CommonParameters>] |

Detailed Description

This cmdlet connects to Google Cloud object storage. You can use these settings to add Google Cloud object storage into your backup infrastructure an object storage repository.

Run the [Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md) cmdlet to add Google Cloud as an object storage repository.

|  |
| --- |
| Note |
| Consider the following:   * It is recommended to disconnect from the Google Cloud object storage at the end of the PowerShell session. Otherwise, the information that you get within the session will not be refreshed when you connect again, and outdated data will be used then. Run the [Disconnect-VBRGoogleCloudService](disconnect-vbrgooglecloudservice.md) cmdlet to stop the session.  * To get an active session, save the result that you get after you run the Connect-VBRGoogleCloudService cmdlet to a variable. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies a Google Cloud credentials record. Veeam Backup & Replication will use this credentials record to connect to Google Cloud object storage. | Accepts the VBRGoogleCloudAccount object. To create this object, run the [Add-VBRGoogleCloudAccount](add-vbrgooglecloudaccount.md) cmdlet. | True | Named | False |
| ServiceType | Specifies the type of the backup repository. The cmdlet will add the object storage as the specified type of the backup repository to the backup infrastructure.   * ExternalRepository: Use this option to add object storage as an external backup repository. * CapacityTier: Use this option to add object storage as a capacity extent or an object storage repository. * ArchiveTier: Use this option to add object storage as an archive extent. | VBRGoogleCloudServiceType | True | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Connecting to Google Cloud Service

This example shows how to connect to Google Cloud object storage.

|  |
| --- |
| $account = Get-VBRGoogleCloudAccount -AccessKey "ABCDEFGHIGKLMNOP"  Connect-VBRGoogleCloudService -Account $account -ServiceType ExternalRepository |

Perform the following steps:

1. Run the [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md) cmdlet. Specify the AccessKey parameter value. Save the result to the $account variable.
2. Run the Connect-VBRGoogleCloudService cmdlet. Set the $account variable as the Account parameter value. Set the ExternalRepository value for the ServiceType parameter value.

Related Commands

* [Get-VBRGoogleCloudAccount](get-vbrgooglecloudaccount.md)
* [Add-VBRGoogleCloudRepository](add-vbrgooglecloudrepository.md)

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
