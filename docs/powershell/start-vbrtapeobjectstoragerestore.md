---
title: "Start-VBRTapeObjectStorageRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrtapeobjectstoragerestore.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Start-VBRTapeObjectStorageRestore


Short Description

Starts the restore of objects from tape.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Restore objects from tape to the original location.

|  |
| --- |
| Start-VBRTapeObjectStorageRestore [-CatalogItem <VBRTapeCatalogItem[]>] [-CatalogItemVersion <VBRTapeCatalogItemVersion[]>] [-ItemRestorePolicy {LeaveExisting | OverwriteOlder | AlwaysOverwrite}] [-EnableItemSecurityRestore] [-RunAsync]  [<CommonParameters>] |

* Restore objects from tape to the a new location.

|  |
| --- |
| Start-VBRTapeObjectStorageRestore -Server <CHost> -Path <string> [-CatalogItem <VBRTapeCatalogItem[]>] [-CatalogItemVersion <VBRTapeCatalogItemVersion[]>] [-PreserveFolderHierarchy] [-ItemRestorePolicy {LeaveExisting | OverwriteOlder | AlwaysOverwrite}] [-EnableItemSecurityRestore] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the restore of objects backed-up by tape jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CatalogItem | Specifies an array of objects to restore. | Accepts the VBRTapeCatalogItem[] object. To get this object, run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| CatalogItemVersion | Specifies an array of objects to restore.  If this parameter is not specified, the cmdlet will restore the latest version of objects. | Accepts the VBRTapeCatalogItemVersion[] object. To get this object, run the [Find-VBRTapeCatalogItemVersion](find-vbrtapecatalogitemversion.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| Server | Specifies the server to restore data to. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Path | Specifies the path to the folder on the destination server to restore data to. | String | True | Named | False |
| PreserveFolderHierarchy | If you provide this parameter, the cmdlet will preserve the folder hierarchy of restored data.  Otherwise, objects will be restored to the specified target folder without keeping the folder structure. | SwitchParameter | False | Named | False |
| ItemRestorePolicy | Specifies overwrite options to use in case the object already exists in the target folder:   * LeaveExisting: use this option not to overwrite the existing object with the restored one. * OverwriteOlder: use this option to overwrite the existing object only if it is older than the restored object. * AlwaysOverwrite: use this option to overwrite the existing object with the restored object in all cases. | VBRTapeCatalogItemRestorePolicy | False | Named | False |
| EnableItemSecurityRestore | Enables the option for the restored objects to keep their original ownership and security permissions. Otherwise, Veeam Backup & Replication will change security settings: the user account under which the Veeam Backup Service runs will be set as the owner of the restored objects, while access permissions will be inherited from the target folder to which the objects are restored. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Restoring Objects from Tape to Original Location

|  |  |
| --- | --- |
| This example shows how to start the restore to original location objects backed-up by tape jobs.  |  | | --- | | $item = Find-VBRTapeCatalogItem  Start-VBRTapeObjectStorageRestore -CatalogItem $item[3] |  Perform the following steps:   1. Run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. Save the result to the $item variable.   The Find-VBRTapeCatalogItem cmdlet will return an array of objects to restore. Mind the ordinal number of the necessary object (in our example, it is the fourth restore point in the array).   1. Run the Start-VBRTapeObjectStorageRestore cmdlet. Set the $item[3] variable as the CatalogItem parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Restoring Objects from Tape to Another Location

|  |  |
| --- | --- |
| This example shows how to start the restore to another location objects backed-up by tape jobs.  |  | | --- | | $host = Get-VBRServer -Name target.tech.local  $item = Find-VBRTapeCatalogItem  Start-VBRTapeObjectStorageRestore -Server $host -Path "C:\Backup restore\Azure Blob Container" -CatalogItem $item[3] |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable. 2. Run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. Save the result to the $item variable.   The Find-VBRTapeCatalogItem cmdlet will return an array of objects to restore. Mind the ordinal number of the necessary object (in our example, it is the fourth restore point in the array).   1. Run the Start-VBRTapeObjectStorageRestore cmdlet. Set the $host variable as the Server parameter value. Specify the Path parameter value. Set the $item[3] variable as the CatalogItem parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Restoring Objects from Tape to Another Object Storage Location

|  |  |
| --- | --- |
| This example shows how to start the restore of the ABC Bucket item to the SDK Container within Microsoft Azure Blob Storage.  |  | | --- | | $azure = Get-VBRServer -Name "Azure Blob Storage"  $item = Find-VBRTapeCatalogItem -Name "ABC Bucket"  Start-VBRTapeObjectStorageRestore -Server $azure -Path "<ObjectStorageHostPath><Region>Azure Global (Standard)</Region><Container>SDK Container</Container><RelativePath></RelativePath><Delimiter>/</Delimiter><IsObject>False</IsObject></ObjectStorageHostPath>" -CatalogItem $item |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $azure variable. 2. Run the [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) cmdlet. Specify the Name parameter value. Save the result to the $item variable. 3. Run the Start-VBRTapeObjectStorageRestore cmdlet. Specify the following settings:  * Set the $azure variable as the Server parameter value. * Specify the Path parameter value.  * Set the $item variable as the CatalogItem parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Restoring Objects from Tape to Another Object Storage Location (XML)

|  |  |
| --- | --- |
| If you restore to another storage or container, you must provide the path to this new location in the XML format. The format must have the following tags:  |  | | --- | | <ObjectStorageHostPath>   <Region>Reqion\_name</Region>   <Container>Container\_name</Container>   <RelativePath>Prefix</RelativePath>   <Delimiter>/</Delimiter>   <IsObject>False</IsObject>  </ObjectStorageHostPath> |  The path contains the following tags and parameters:   * <Region> — specifies a name of a region for the object storage. Note: If you do not have a name of a region, specify the asterisk sign \*. * <Container> — specifies the name of the container or bucket  to which you want to restore the object storage data. * <RelativePath> — specifies the prefix for the restored objects. Note: Do not specify this tag when restoring objects to the root container or bucket. * <Delimiter> — the value always must be /. * <IsObject> — the value always must be False. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md)


