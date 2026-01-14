---
title: "Get-VBRServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrserver.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Get-VBRServer

In this article

Short Description

Returns hosts connected to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRServer [-Name <String[]>] [-Type <VBRHostType>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns hosts connected to the backup infrastructure. You can get the following servers:

* BackupServer
* VC
* ESXi
* VcdSystem
* Scvmm
* HvServer
* HvCluster
* SmbCluster
* SmbServer
* Windows
* Linux
* Cloud
* Local
* SanHost
* Object storage repositories
* Object storage servers
* Microsoft Entra ID tenant

You can get the list of all hosts or narrow down the output to servers of specific type, or search for instances directly by name.

To get VMware objects run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet.

To get Hyper-V objects run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the host type. The cmdlet will return hosts of this type:   * ESX * VC * Linux * Local * Windows * ESXi * HvServer * HvCluster * Scvmm * SanHost * SmbServer * SmbCluster * VcdSystem * Cloud * AzureWinServer * VmSnapshotStorageHost * ConfigurationService * ExternalInfrastructureProxy * NdmpServer * ExternalInfrastructureServer * CifsShare * NfsShare * SanCifsServer * SanNfsServer * CifsServer * NfsServer * CifsServerShare * NfsServerShare * S3CompatibleServer * S3CompatibleBucket * AmazonS3Server * AmazonS3Bucket * AzureBlobServer * AzureBlobContainer * GoogleStorageServer * GoogleStorageBucket * AzureDataLakeServer * AzureDataLakeContainer * AzureEntraIdTenant | VBRHostType | False | Named | False |
| Name | Specifies the array of host names. The cmdlet will return hosts with these names. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHost object that contains settings of hosts connected to Veeam Backup & Replication.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for Server by Name

|  |  |
| --- | --- |
| This command looks for the server named Active\_Directory.  |  | | --- | | Get-VBRServer -Name "Active\_Directory" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for VM Registered on Hyper-V Server

|  |  |
| --- | --- |
| This command looks for the VM named Hv\_DNS registered on a Hyper-V server.  |  | | --- | | Get-VBRServer -Type "HvServer" -Name "Hv\_DNS" | |

Page updated 11/14/2025

Page content applies to build 13.0.1.1071
