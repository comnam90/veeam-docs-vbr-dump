---
title: "Connect-VBRAzureDataBoxService"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/connect-vbrazuredataboxservice.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Connect-VBRAzureDataBoxService

In this article

Short Description

Connects to Azure Data Box storage.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Connect-VBRAzureDataBoxService -Account <VBRAzureBlobAccount> -ServicePoint <string> [-GatewayServer <CHost>] [-ConnectionType <VBRRepositoryConnectionType>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet connects to Azure Data Box storage.

|  |
| --- |
| Important |
| This cmdlet connects only the Azure Data Box storage that can be used as a capacity extent of the scale-out backup repository. |

|  |
| --- |
| Note |
| Consider the following:   * It is recommended to disconnect the Microsoft Azure Blob session at the end. Otherwise, the information that you get within the session will not be refreshed when you connect again, and outdated data will be used then. Run the [Disconnect-VBRAzureBlobService](disconnect-vbrazureblobservice.md) cmdlet to stop the session. * To get the current session, save the result that you get after you run the Connect-VBRAzureDataBoxService cmdlet to a variable. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies an Microsoft Azure Blob credentials record. The cmdlet will use this credentials record to connect to Azure Data Box storage. | Accepts the VBRAzureBlobAccount object. To get this object, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. | True | Named | True (ByValue) |
| ServicePoint | Specifies the endpoint. The cmdlet will use this endpoint to connect to Azure Data Box object storage. | String | True | Named | False |
| GatewayServer | Specifies an array of gateway servers that you want to use to transfer data from processed VM to object storage repositories. | Accepts the CHost[] object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| ConnectionType | Specifies how Veeam Backup & Replication will access the object storage repository:   * Direct: Use this option if you want Veeam Backup & Replication to use a proxy server to transfer data from the processed VM to object storage repositories. * Gateway: Use this option if you want Veeam Backup & Replication to use a gateway server to transfer data from processed VM to object storage repositories.   Default: Direct. | VBRRepositoryConnectionType |  |  |  |
| Force | Defines that the cmdlet will skip the certificate check.  If you do not provide this parameter, Veeam Backup & Replication will check that the Azure Data Box certificate is valid. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRAzureDataBoxService object that contains connection settings to Azure Data Box storage.

Examples

Connecting to Azure Data Box Storage

This example shows how to connect to Azure Data Box storage.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  Connect-VBRAzureDataBoxService -Account $connect -ServicePoint "ZTX15910049.microsoftdatabox.com" |

Perform the following steps:

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and the ServiceType parameter values. Save the result to the $connect variable.
3. Run the Connect-VBRAzureDataBoxService cmdlet. Set the $connect variable as the Account parameter value. Specify the ServicePoint parameter value.

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
