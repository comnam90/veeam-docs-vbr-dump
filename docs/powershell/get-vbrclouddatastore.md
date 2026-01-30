---
title: "Get-VBRCloudDatastore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrclouddatastore.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudDatastore


Short Description

Returns datastores or disk volumes allocated to you under your cloud resources.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get datastores or volumes by name.

|  |
| --- |
| Get-VBRCloudDatastore [-Name <string[]>]  [<CommonParameters>] |

* Get datastores or volumes of a selected cloud service provider.

|  |
| --- |
| Get-VBRCloudDatastore [-CloudServer <VBRCloudServer[]>] [-Name <string[]>]  [<CommonParameters>] |

* Get datastores or volumes by ID.

|  |
| --- |
| Get-VBRCloudDatastore [-Id <guid[]>] [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns datastores (for VMware) or volumes (for Hyper-V) in your cloud resources.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name of the datastore or volume you want to get. | String[] | False | Named | False |
| CloudServer | Specifies the cloud service provider. The cmdlet will return the datastores or volumes provided by this cloud service provider. | Accepts the [VBRCloudServer[]](vbrcloudserver.md) object. To get this object, run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. | False | Named | True (ByValue, |
| Id | Specifies the ID of the datastore or volume you want to get. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudDatastore](vbrclouddatastore.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Cloud Datastore by Name

|  |  |
| --- | --- |
| This command returns the Cloud Replicas cloud datastore.  |  | | --- | | Get-VBRCloudDatastore -Name "Cloud Replicas" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Cloud Datastores of Selected Cloud Server

|  |  |
| --- | --- |
| This example shows how to return cloud datastores located on the cloud server named "Hyper-V Silver".  |  | | --- | | $cloudServer = Get-VBRCloudServer -Name "Hyper-V Silver"  Get-VBRCloudDatastore -CloudServer $cloudServer |  Perform the following steps:   1. Run the [Get-VBRCloudServer](get-vbrcloudserver.md) cmdlet. Specify the Name parameter value. Save the result to the $cloudServer variable. 2. Run the Get-VBRCloudDatastore cmdlet. Set the $cloudServer variable as the CloudServer parameter value. |

Related Commands

[Get-VBRCloudServer](get-vbrcloudserver.md)


