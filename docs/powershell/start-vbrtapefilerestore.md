---
title: "Start-VBRTapeFileRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrtapefilerestore.html"
last_updated: "3/25/2024"
product_version: "13.0.1.1071"
---

# Start-VBRTapeFileRestore


Short Description

Starts the restore of files and folders from tape.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore files and folders from tape to the original location.

|  |
| --- |
| Start-VBRTapeFileRestore [-CatalogItem <VBRTapeCatalogItem[]>] [-CatalogItemVersion <VBRTapeCatalogItemVersion[]>] [-ItemRestorePolicy <VBRTapeCatalogItemRestorePolicy>] [-EnableItemSecurityRestore] [-RunAsync]  [<CommonParameters>] |

* Restore files and folders from tape to the a new location.

|  |
| --- |
| Start-VBRTapeFileRestore [-CatalogItem <VBRTapeCatalogItem[]>] [-CatalogItemVersion <VBRTapeCatalogItemVersion[]>] -Server <CHost> -Path <String> [-PreserveFolderHierarchy] [-ItemRestorePolicy <VBRTapeCatalogItemRestorePolicy>] [-EnableItemSecurityRestore] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the restore of files and folders backed-up by tape jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CatalogItem | Specifies an array of files or folders to restore. | Accepts the VBRTapeCatalogItem[] object. To get this object, run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| CatalogItemVersion | Specifies an array of versions of files or folders to restore.  If this parameter is not specified, the cmdlet will restore the latest version of files or folders. | Accepts the VBRTapeCatalogItemVersion[] object. To get this object, run the [Find-VBRTapeCatalogItemVersion](find-vbrtapecatalogitemversion.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| Server | Specifies the server to restore data to. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Path | Specifies the path to the folder on the destination server to restore data to. | String | True | Named | False |
| PreserveFolderHierarchy | If you provide this parameter, the cmdlet will preserve the folder hierarchy of restored data.  Otherwise, files will be restored to the specified target folder without keeping the folder structure.  Note: Do not use this parameter when restoring NDMP volumes. | SwitchParameter | False | Named | False |
| ItemRestorePolicy | Specifies overwrite options to use in case the file already exists in the target folder:   * LeaveExisting: use this option not to overwrite the existing file with the restored one. * OverwriteOlder: use this option to overwrite the existing file only if it is older than the restored file. * AlwaysOverwrite: use this option to overwrite the existing file with the restored file in all cases. | VBRTapeCatalogItemRestorePolicy | False | Named | False |
| EnableItemSecurityRestore | Enables the Restore file and folder security option: use it if you want the restored files to keep their original ownership and security permissions. Otherwise, Veeam Backup & Replication will change security settings: the user account under which the Veeam Backup Service runs will be set as the owner of the restored objects, while access permissions will be inherited from the target folder to which the objects are restored. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring to Original Location Items Backed-Up by Tape Jobs

|  |  |
| --- | --- |
| This example shows how to start the restore to original location files and folders backed-up by tape jobs.  |  | | --- | | $item = Find-VBRTapeCatalogItem  Start-VBRTapeFileRestore -CatalogItem $item[3] |  Perform the following steps:   1. Run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. Save the result to the $item variable. 2. Run the Start-VBRTapeFileRestore cmdlet. Set the $item[3] variable as the CatalogItem parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring to Another Location Items Backed-Up by Tape Jobs

|  |  |
| --- | --- |
| This example shows how to start the restore to another location files and folders backed-up by tape jobs.  |  | | --- | | $host = Get-VBRServer -Name target.tech.local  $item = Find-VBRTapeCatalogItem  Start-VBRTapeFileRestore -Server $host -Path "C:\Backup restore\Fileserv05" -CatalogItem $item[3] |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable. 2. Run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. Save the result to the $item variable. 3. Run the Start-VBRTapeFileRestore cmdlet. Set the $host variable as the Server parameter value. Specify the Path parameter value. Set the $item[3] variable as the CatalogItem parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md)


