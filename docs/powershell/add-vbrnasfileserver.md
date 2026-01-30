---
title: "Add-VBRNASFileServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrnasfileserver.html"
last_updated: "12/18/2023"
product_version: "13.0.1.1071"
---

# Add-VBRNASFileServer


Short Description

Adds managed Windows or Linux file serves to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRNASFileServer -Server <CHost> -CacheRepository <CBackupRepository> [-BackupIOControlLevel {Lowest | Low |Medium | High | Highest}]  [<CommonParameters>] |

Detailed Description

This cmdlet adds managed Windows or Linux file servers to the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the host where the file server is located. Veeam Backup & Replication will add the file server that is located on this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASFileServer object that contains settings of the managed Windows or Linux file servers to the Veeam Backup & Replication infrastructure.

Examples

Adding File Servers

This example shows how to add managed Windows or Linux file servers to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| $server = Get-VBRServer -Name 'Active\_Directory'  $repository = Get-VBRBackupRepository -Name 'Backup Repository 08'  Add-VBRNASFileServer -Server $server -CacheRepository $repository |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable.
3. Run the Add-VBRNASFileServer cmdlet. Set the $server variable as the Server parameter value. Set the $repository variable as the CacheRepository parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)


