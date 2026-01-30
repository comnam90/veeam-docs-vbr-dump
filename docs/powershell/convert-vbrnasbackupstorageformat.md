---
title: "Convert-VBRNASBackupStorageFormat"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/convert-vbrnasbackupstorageformat.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Convert-VBRNASBackupStorageFormat


Short Description

Converts format of baskets used for storing backups created with file backup and file backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Convert-VBRNASBackupStorageFormat -Job <CBackupJob[]> [-RunAsync] [-BasketType {Automatic | SingleFileBasket | Classic}]  [<CommonParameters>] |

Detailed Description

The cmdlet converts format of baskets used for storing backups created with file backup and file backup copy jobs.

File share backups can be stored either in baskets containing up to 16 standard blob files each up to 64 MB in size, or in single file baskets containing one file up to 1 GB in size. To provide better performance, it is recommended to convert backups that are stored on HPE StoreOnce storage appliances and Dell Data Domain storage systems into the single file basket format.

|  |
| --- |
| Note |
| Consider the following:   * If the backups created by the backup job are stored not only in the backup repository, but also in the archive repository, all of them will be converted when running this cmdlet. * Archive backups stored on S3 repositories cannot be converted into the single file basket format. If you try to convert such backups, the cmdlet will return a warning about that. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of file backup jobs or file backup copy jobs. The cmdlet will convert backups created by these jobs into the specified format. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) or [Get-VBRUnstructuredBackupCopyJob](get-vbrunstructuredbackupcopyjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| BasketType | Specifies a basket type into which file share backups will be converted. You can specify either of the following values:   * Automatic: use this option to automatically convert backups into the recommended format based on the type of the storage specified in file backup jobs or file backup copy jobs. * SingleFileBasket: use this option to convert backups into single file baskets containing one file up to 1 GB in size. * Classic: use this option to convert backups into classic containing up to 16 standard blob files each up to 64 MB in size.   If you do not specify this parameter, the cmdlet will use the Automatic setting for conversion by default. | Accepts the VBRBasketType type. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the result of the conversion.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Converting File Share Backup into Single File Basket Format

|  |  |
| --- | --- |
| This example shows how to convert backups created by a file backup job into the single file basket format.  |  | | --- | | $job = Get-VBRUnstructuredBackupJob -Name "Daily file backup to StoreOnce"  Convert-VBRNASBackupStorageFormat -Job $job -BasketType SingleFileBasket |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Convert-VBRNASBackupStorageFormat cmdlet. Set the $job variable as the Job parameter value. Specify the SingleFileBasket value for the BasketType parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Converting File Share Backup Copy into Classic Basket Format

|  |  |
| --- | --- |
| This example shows how to convert backups created by a file backup job into the classic basket format.  |  | | --- | | $copy\_job = Get-VBRUnstructuredBackupCopyJob -Name "Daily file backup to StoreOnce"  Convert-VBRNASBackupStorageFormat -Job $copy\_job -BasketType Classic |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackupCopyJob](get-vbrunstructuredbackupcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $copy\_job variable. 2. Run the Convert-VBRNASBackupStorageFormat cmdlet. Set the $copy\_job variable as the Job parameter value. Specify the Classic value for the BasketType parameter value. |

Related Commands

* [Get-VBRUnstructuredBackupJob](get-vbrunstructuredbackupjob.md)
* [Get-VBRUnstructuredBackupCopyJob](get-vbrunstructuredbackupcopyjob.md)


