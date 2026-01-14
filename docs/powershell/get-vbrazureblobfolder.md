---
title: "Get-VBRAzureBlobFolder"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureblobfolder.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureBlobFolder

In this article

Short Description

Returns Microsoft Azure Blob folders.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureBlobFolder -Container <VBRAzureBlobContainer[]> -Connection <VBRAzureBlobConnection> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Microsoft Azure Blob folders. You can get the array of all folders from your Microsoft Azure Blob storage or the array of the folders from the particular container.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies an array of Microsoft Azure Blob containers. The cmdlet will return the folders from these containers. | Accepts the VBRBlobContainer[] object. To get this object, run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. | True | Named | True (ByValue) |
| Connection | Specifies an active session with Microsoft Azure Blob storage. | Accepts the following objects:   * VBRAzureBlobConnection * VBRAzureDataBoxConnection   To get these objects, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. | True | Named | False |
| Name | Specifies an array of names for Microsoft Azure Blob folders that you want to get. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureBlobFolder object that contains Microsoft Azure Blob folders.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Folders from Microsoft Azure Blob Storage

|  |  |
| --- | --- |
| This example shows how to get all folders from Microsoft Azure Blob storage.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  $container = Get-VBRAzureBlobContainer -Connection $connect  Get-VBRAzureBlobFolder -Container $Container -Connection $connect |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and the ServiceType parameter values. Save the result to the $connect variable. 3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Set the $connect variable as the Connection parameter value. Save the result to the $container variable. 4. Run the Get-VBRAzureBlobFolder cmdlet. Set the $container variable as the Container parameter value. Set the $connect variable as the Connection parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Folders from Specific Microsoft Azure Blob Container

|  |  |
| --- | --- |
| This example shows how to get all folders from a specific Microsoft Azure Blob container.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  $container = Get-VBRAzureBlobContainer -Connection $connect -Name "Container"  Get-VBRAzureBlobFolder -Container $Container -Connection $connect |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and the ServiceType parameter values. Save the result to the $connect variable. 3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Set the $connect variable as the Connection parameter value. Specify the Name parameter value. Save the result to the $container variable. 4. Run the Get-VBRAzureBlobFolder cmdlet. Set the $container variable as the Container parameter value. Set the $connect variable as the Connection parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Specific Folder from Microsoft Azure Blob Storage

|  |  |
| --- | --- |
| This example shows how to get a specific folder from Microsoft Azure Blob storage.  |  | | --- | | $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  $container = Get-VBRAzureBlobContainer -Connection $connect  Get-VBRAzureBlobFolder -Container $container -Connection $connect -Name "New Folder" |  Perform the following steps:   1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable. 2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and the ServiceType parameter values. Save the result to the $connect variable. 3. Run the [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md) cmdlet. Set the $connect variable as the Connection parameter value. Save the result to the $container variable. 4. Run the Get-VBRAzureBlobFolder cmdlet. Set the $container variable as the Container parameter value. Set the $connect variable as the Connection parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)
* [Get-VBRAzureBlobContainer](get-vbrazureblobcontainer.md)

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
