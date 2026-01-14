---
title: "Get-VBRAzureBlobContainer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureblobcontainer.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureBlobContainer

In this article

Short Description

Returns Azure Blob containers.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureBlobContainer -Connection <VBRAzureBlobConnection> [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of Microsoft Azure Blob containers.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Microsoft Azure Blob storage. The cmdlet will return an array of the containers added to this object storage. | Accepts the following objects:   * VBRAzureBlobConnection * VBRAzureDataBoxConnection   To get this object, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. | True | Named | False |
| Name | Specifies an array of names of the Microsoft Azure Blob container that you want to get. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRAzureBlobContainer object that contains Microsoft Azure Blob containers.

Examples

Getting All Microsoft Azure Blob Containers

This example shows how to get all containers added to Microsoft Azure Blob storage. The cmdlet will return an array of containers added to the Global region type.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount -Name "Azure Blob"  $connect = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType ExternalRepository  Get-VBRAzureBlobContainer -Connection $connect |

Perform the following steps:

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Specify the Account, RegionType and the ServiceType parameter values. Save the result to the $connect variable.
3. Run the Get-VBRAzureBlobContainer cmdlet. Set the $connect variable as the Connection parameter value.

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
