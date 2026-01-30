---
title: "New-VBRAzureBlobFolder"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrazureblobfolder.html"
last_updated: "6/17/2024"
product_version: "13.0.1.1071"
---

# New-VBRAzureBlobFolder


Short Description

Creates Microsoft Azure Blob folders.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAzureBlobFolder -Container <VBRAzureBlobContainer> -Connection <VBRAzureBlobConnection> -Name <string>  [<CommonParameters>] |

Detailed Description

This cmdlet creates Microsoft Azure Blob folders. Veeam Backup & Replication will use these folders to keep backup files there.

|  |
| --- |
| Important |
| The default Root container is not supported. For more information about this container, see [this Microsoft article](https://learn.microsoft.com/en-us/rest/api/storageservices/working-with-the-root-container). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies an Microsoft Azure Blob container. The cmdlet will create a folder in this container. | Accepts the [VBRAzureBlobContainer](vbrazureblobcontainer.md) object. To get this object, run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with Microsoft Azure Blob storage. The cmdlet will use this session to connect to Microsoft Azure object storage. | Accepts the following objects:   * VBRAzureBlobConnection * VBRAzureDataBoxConnection   To get this object, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. | True | Named | False |
| Name | Specifies a name of the Microsoft Azure Blob container. The cmdlet will create a new Microsoft Azure Blob folder in this container. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureBlobFolder object that contains Microsoft Azure Blob folders.

Examples

Adding Microsoft Azure Blob Folder

This example shows how to create a Microsoft Azure Blob folder that an Azure Blob object storage will use as a repository.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  $container = Get-VBRAzureBlobContainer -Connection $connect -Name "Container"  New-VBRAzureBlobFolder -Container $container -Connection $connect -Name "Images" |

Perform the following steps:

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Specify the Account, RegionType and the ServiceType parameter values. Save the result to the $connect variable.
3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Specify the Connection and the Name parameter values. Save the result to the $container variable.
4. Run the New-VBRAzureBlobFolder cmdlet. Set the $container variable as the Container parameter value. Set the $connect variable as the Connection parameter value. Specify the Name parameter value.

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)
* [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md)


