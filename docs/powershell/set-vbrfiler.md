---
title: "Set-VBRFiler"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrfiler.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Set-VBRFiler


Short Description

Modifies enterprise NAS systems added as file shares to the inventory.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify the enterprise NAS system added as a file share to the inventory without authentication.

|  |
| --- |
| Set-VBRFiler -Filer <VBRFiler> [-CacheRepository <CBackupRepository>] [-MetaMigrationType <VBRNASBackupMetaMigrationType>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-RequireAccessCredentials] [-EnableSnapDiff]  [<CommonParameters>] |

* Modify the enterprise NAS system added as a file share to the inventory with specific user name and password.

|  |
| --- |
| Set-VBRFiler -Filer <VBRFiler> -User <string> -Password <string> [-CacheRepository <CBackupRepository>] [-MetaMigrationType <VBRNASBackupMetaMigrationType>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-RequireAccessCredentials] [-EnableSnapDiff]  [<CommonParameters>] |

* Modify the enterprise NAS system added as a file share to the inventory using specific credentials.

|  |
| --- |
| Set-VBRFiler -Filer <VBRFiler> -AccessCredentials <CCredentials> [-CacheRepository <CBackupRepository>] [-MetaMigrationType <VBRNASBackupMetaMigrationType>] [-BackupIOControlLevel {Lowest | Low | Medium | High | Highest}] [-RequireAccessCredentials] [-EnableSnapDiff]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of enterprise NAS systems added to the inventory.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Filer | Specifies the enterprise NAS system. The cmdlet will modify the settings of this server. | Accepts the VBRFiler object. To get this object, run the [Add-VBRFiler](add-vbrfiler.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| CacheRepository | Specifies the cache repository. Veeam Backup & Replication will keep the .VCACHE files on this repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| MetaMigrationType | Specifies how the cmdlet will migrate metadata. You can use one of the following options:   * CheckExistence — use this option to check that metadata is available on the current cache repository. * CopyMetaFromCache — use this option to migrate metadata from source cache repository to a new cache repository. * DownloadMetaFromArchive — use this option to migrate metadata from archive repository or from replica metadata in archive repository. | VBRNASBackupMetaMigrationType | False | Named | False |
| BackupIOControlLevel | Specifies a speed that Veeam Backup & Replication will use to read data from the file server. You can specify either of the following speed:   * Lowest * Low * Medium * High * Highest | VBRNASBackupIOControlLevel | False | Named | False |
| RequireAccessCredentials | Defines that the cmdlet will check whether Veeam Backup & Replication uses authentication to access the SMB network shared folder.  If you do not provide this parameter, the cmdlet will not check credentials that are used to access the SMB network shared folder.  To remove credentials, specify the RequireAccessCredentials parameter with the :$False value.  Note: If credentials are not provided, the cmdlet will return an error. To avoid the error, you must specify credentials using either of the following parameters:   * User and Password * AccessCredentials | SwitchParameter | False | Named | False |
| EnableSnapDiff | Use this parameter for Dell PowerScale (formerly Isilon) storages only.  Defines that during the file backup jobs Veeam Backup & Replication will use the file change tracking technology provided by the NAS manufacturer. | SwitchParameter | False | Named | False |
| User | Specifies the user name. The cmdlet will apply this user name to authenticate against the enterprise NAS system. | String | True | Named | False |
| Password | Specifies the password. The cmdlet will use this password to authenticate against the enterprise NAS system. | String | True | Named | False |
| AccessCredentials | Specifies credentials that the cmdlet will use to authenticate against the enterprise NAS system. | Accepts the CCredentials object. To get this object, run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFiler object that defines the settings of the enterprise NAS system added as a file share to the inventory.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Enterprise NAS System Added as File Share Without Authentication

|  |  |
| --- | --- |
| This example shows how to modify the enterprise NAS system as a file share to the inventory without authentication.  |  | | --- | | $filer = Get-VBRFiler -Name "ontap-2"  $repository = Get-VBRBackupRepository -Name "Backup Repository 02"  Set-VBRFiler -Filer $filer -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRFiler](get-vbrfiler.md) cmdlet. Specify the Name parameter value. Save the result to the $filer variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Set-VBRFiler cmdlet. Specify the following settings:  * Set the $filer variable as the Filer parameter value. * Set the $repository variable as the CacheRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Enterprise NAS System Added as File Share with User Name and Password

|  |  |
| --- | --- |
| This example shows how to modify the enterprise NAS system added as a file share to the inventory with user name and password.  |  | | --- | | $filer = Get-VBRFiler -Name "ontap-2"  $repository = Get-VBRBackupRepository -Name "Backup Repository 02"  Set-VBRFiler -Filer $filer -User Administrator -Password AdminCredentials -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRFiler](get-vbrfiler.md) cmdlet. Specify the Name parameter value. Save the result to the $filer variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the Set-VBRFiler cmdlet. Specify the following settings:  * Set the $filer variable as the Filer parameter value.  * Specify the User parameter value. * Specify the Password parameter value.  * Set the $repository variable as the CacheRepository parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Modifying Enterprise NAS System Added as File Share with Credentials

|  |  |
| --- | --- |
| This example shows how to modify the enterprise NAS system added as a file share to the infrastructure with credentials.  |  | | --- | | $filer = Get-VBRFiler -Name "ontap-2"  $repository = Get-VBRBackupRepository -Name "Backup Repository 02"  $credentials = Get-VBRCredentials  Set-VBRFiler -Filer $filer -AccessCredentials $credentials -CacheRepository $repository |  Perform the following steps:   1. Run the [Get-VBRFiler](get-vbrfiler.md) cmdlet. Specify the Name parameter value. Save the result to the $filer variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repository variable. 3. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Save the result to the $credentials variable. 4. Run the Set-VBRFiler cmdlet. Specify the following settings:  * Set the $filer variable as the Filer parameter value.  * Set the $credentials variable as the AccessCredentials parameter value.  * Set the $repository variable as the CacheRepository parameter value. |

Related Commands

* [Get-VBRFiler](get-vbrfiler.md)

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCredentials](get-vbrcredentials.md)


