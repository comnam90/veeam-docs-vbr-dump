---
title: "Get-VBRNASBackupFLRItemVersion (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasbackupflritemversion.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRNASBackupFLRItemVersion (obsolete)


Short Description

Returns versions of objects backed-up by file backup jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Get-VBRUnstructuredBackupFLRItemVersion](get-vbrunstructuredbackupflritemversion.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all versions of objects.

|  |
| --- |
| Get-VBRNASBackupFLRItemVersion -Item <VBRNASBackupFLRItem>  [<CommonParameters>] |

* Get versions of objects by the object modification date.

|  |
| --- |
| Get-VBRNASBackupFLRItemVersion -Item <VBRNASBackupFLRItem> [-ModificationDate <datetime>]  [<CommonParameters>] |

* Get versions of objects by the object version ID.

|  |
| --- |
| Get-VBRNASBackupFLRItemVersion -Item <VBRNASBackupFLRItem> [-VersionId <uint64>]  [<CommonParameters>] |

* Get the latest version of objects located in the archive repository.

|  |
| --- |
| Get-VBRNASBackupFLRItemVersion -Item <VBRNASBackupFLRItem> [-LatestArchivedVersion]  [<CommonParameters>] |

Detailed Description

This cmdlet returns versions of objects backed-up by file backup jobs.

|  |
| --- |
| Important |
| This cmdlet runs only with file-level restore sessions that are created to restore all versions of backups on file shares. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Item | Specifies an object. The cmdlet will return versions of this object. | Accepts the VBRNASBackupFLRItem object. To get this object, run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet. | True | Named | False |
| ModificationDate | Specifies the date when the object was modified. The cmdlet will return versions of objects that were modified on the specified date. | DateTime | False | Named | False |
| VersionId | Specifies a version ID of the object. The cmdlet will return objects with the specified version ID. | Uint64 | False | Named | False |
| LatestArchivedVersion | Defines that the cmdlet will return the latest version of the object located in the archive repository. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASBackupFLRItem](vbrnasbackupflritem.md) and VBRNASBackupFLRFolder objects that contain details about versions of restored guest OS files and folders that have been backed up by file backup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Versions of Object

|  |  |
| --- | --- |
| This example shows how to get all versions of an object backed-up by a file backup job.  |  | | --- | | $session = Get-VBRNASBackupFLRSession  $object = Get-VBRNASBackupFLRItem -Session $session  Get-VBRNASBackupFLRItemVersion -Item $object |  Perform the following steps:   1. Run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $object variable. 3. Run the Get-VBRNASBackupFLRItemVersion cmdlet. Set the $object variable as the Item parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Versions of Objects by Modification Date

|  |  |
| --- | --- |
| This example shows how to get versions of an object by the object modification date. Veeam Backup & Replication will return objects that have been modified on 9/9/2022.  |  | | --- | | $session = Get-VBRNASBackupFLRSession  $object = Get-VBRNASBackupFLRItem -Session $session  Get-VBRNASBackupFLRItemVersion -Item $object -ModificationDate "9/9/2022" |  Perform the following steps:   1. Run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $object variable. 3. Run the Get-VBRNASBackupFLRItemVersion cmdlet. Set the $object variable as the Item parameter value. Specify the ModificationDate parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Versions of Objects by Version ID

|  |  |
| --- | --- |
| This example shows how to get a version of an object by the object version ID. Veeam Backup & Replication will return an object with the 9 version ID.  |  | | --- | | $session = Get-VBRNASBackupFLRSession  $object = Get-VBRNASBackupFLRItem -Session $session  Get-VBRNASBackupFLRItemVersion -Item $object -VersionId 9 |  Perform the following steps:   1. Run the [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md) cmdlet. Save the result to the $session variable. 2. Run the [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md) cmdlet. Set the $session variable as the Session parameter value. Save the result to the $object variable. 3. Run the Get-VBRNASBackupFLRItemVersion cmdlet. Set the $object variable as the Item parameter value. Specify the VersionId parameter value. |

Related Commands

* [Get-VBRNASBackupFLRSession](get-vbrnasbackupflrsession.md)
* [Get-VBRNASBackupFLRItem](get-vbrnasbackupflritem.md)
* [Get-Date](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1)


