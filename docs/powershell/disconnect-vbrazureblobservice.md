---
title: "Disconnect-VBRAzureBlobService"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disconnect-vbrazureblobservice.html"
last_updated: "4/17/2024"
product_version: "13.0.1.1071"
---

# Disconnect-VBRAzureBlobService

In this article

Short Description

Stops active sessions with Microsoft Azure Blob storage.

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disconnect-VBRAzureBlobService -Connection <VBRAzureBlobConnection>  [<CommonParameters>] |

Detailed Description

This cmdlet stops active sessions with Microsoft Azure Blob storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Connection | Specifies an active session with Microsoft Azure Blob storage. The cmdlet will stop the session with this object storage. | Accepts the following objects:   * VBRAzureBlobConnection * VBRAzureDataBoxConnection   To get these objects, run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. | True | Named | True (ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Active Session with Microsoft Azure Blob Storage

This example shows how to stop an active session with Microsoft Azure Blob storage.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount -Name "Microsoft Azure Blob"  $session = Connect-VBRAzureBlobService -Account $account -RegionType Global -ServiceType CapacityTier  Disconnect-VBRAzureBlobService -Connection $session |

Perform the following steps:

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Run the [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md) cmdlet. Set the $account variable as the Account parameter value. Specify the RegionType and ServiceType parameter values. Save the result to the $session variable.
3. Run the Disconnect-VBRAzureBlobService cmdlet. Set the $session variable as the Connection parameter value.

Related Commands

* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)
* [Connect-VBRAzureBlobService](connect-vbrazureblobservice.md)

Page updated 4/17/2024

Page content applies to build 13.0.1.1071
