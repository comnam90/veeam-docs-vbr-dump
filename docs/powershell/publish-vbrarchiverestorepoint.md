---
title: "Publish-VBRArchiveRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/publish-vbrarchiverestorepoint.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Publish-VBRArchiveRestorePoint

In this article

Short Description

Retrieves data from archive storage.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Retrieve backup files from Amazon S3 Glacier archive storage to the capacity extent.

|  |
| --- |
| Publish-VBRArchiveRestorePoint -RestorePoint <COib> -AvailabilityPeriodDays <int> [-AmazonS3GlacierRetrievalPolicy <VBRAmazonS3GlacierRetrievalPolicy>] [-EnableExpirationNotification] [-ExpirationHoursThreshold <int>] [-RunAsync]  [<CommonParameters>] |

* Retrieve backup files from Azure Archive storage to the capacity extent.

|  |
| --- |
| Publish-VBRArchiveRestorePoint -RestorePoint <COib> -AvailabilityPeriodDays <int> [-AzureArchiveRetrievalPolicy <VBRAzureArchiveRetrievalPolicy>] [-EnableExpirationNotification] [-ExpirationHoursThreshold <int>] [-RunAsync]  [<CommonParameters>] |

* Retrieve backup files from S3 compatible object storage with data archiving to the capacity extent.

|  |
| --- |
| Publish-VBRArchiveRestorePoint -RestorePoint <COib> -AvailabilityPeriodDays <UInt32> -S3GlacierCompatibleRetrievalPolicy <VBRS3GlacierCompatibleRetrievalPolicy> [-EnableExpirationNotification] [-ExpirationHoursThreshold <Int32>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet retrieves the backup files from the archive storage to the capacity extent of the scale-out backup repository. This is necessary for restore from archived backups.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point for which you want to execute publish. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | False |
| AvailabilityPeriodDays | Specifies a period (in days) during which the retrieved archive backup files will be available. | Int | True | Named | False |
| AmazonS3GlacierRetrievalPolicy | Defines the method of data retrieval for Amazon S3 Glacier object storage. You can retrieve data using one of the following methods:   * Expedited * Standard * Bulk | VBRAmazonS3GlacierRetrievalPolicy | True | Named | False |
| AzureArchiveRetrievalPolicy | Defines the method of data retrieval for Azure Archive storage. You can retrieve data using one of the following methods:   * StandardPriority * HighPriority | VBRAzureArchiveRetrievalPolicy | True | Named | False |
| S3GlacierCompatibleRetrievalPolicy | Defines the method of data retrieval for S3 compatible object storage with with data archiving. You can retrieve data using one of the following methods:   * Expedited * Standard * Bulk | VBRS3GlacierCompatibleRetrievalPolicy | True | Named | False |
| EnableExpirationNotification | Enables sending of notification about upcoming expiration of the retrieved archive backup files availability.  Default: False. | SwitchParameter | False | Named | False |
| ExpirationHoursThreshold | For the EnableExpirationNotification parameter. Specifies the moment when the user receives the notification about upcoming expiration of the retrieved archive backup files availability. | Int | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRPublishedBackupSession object.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Retrieving Backup Files from Amazon S3 Glacier Archive Extent

|  |  |
| --- | --- |
| This example shows how to retrieve backup files from the Amazon S3 Glacier archive extent of the scale-out backup repository.  |  | | --- | | $backup = Get-VBRBackup -Name "JOB\_2"  $rp = Get-VBRRestorePoint -Backup $backup  Publish-VBRArchiveRestorePoint -RestorePoint $rp[0] -AvailabilityPeriodDays 3 -AmazonS3GlacierRetrievalPolicy Standard |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $rp variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the first restore point in the array).   1. Run the Publish-VBRArchiveRestorePoint cmdlet. Specify the following settings:  * Set the $rp variable as the RestorePoint parameter value. * Specify the AvailabilityPeriodDays parameter value. * Set the Standard option for the AmazonS3GlacierRetrievalPolicy parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Retrieving Data from Amazon S3 Glacier Archive Storage for Multiple Restore Points

|  |  |
| --- | --- |
| This example shows how to retrieve several restore points from the Amazon S3 Glacier archive storage with the following settings:   * Data retrieval will take from 3-5 hours.  * The retrieved archive backup files will be available for 5 days.   |  | | --- | | Get-VBRRestorePoint  $RPIds = @('fdea6323-e018-44ef-abf3-346e0453134b', 'c57cc164-773f-494a-8fb5-aa960cba0f2d', '3898ab90-4419-4bea-b1a2-b13b93170ad3' )  foreach ($restorePointId in $RPIds)  {     $restorepoint = Get-VBRRestorePoint -Id $restorePointId     Publish-VBRArchiveRestorePoint -RestorePoint $restorepoint -AvailabilityPeriodDays 5 -AmazonS3GlacierRetrievalPolicy Standard -RunAsync  } |  Perform the following steps:   1. Get a list of all restore points. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. The cmdlet will return an array of restore points of tenant backups located in the archive tier. Select the necessary restore points from an array of restore points. 2. Define an array of restore points. Specify the necessary restore point IDs. Save the result to the $RPIds variable. 3. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 4. Run the [foreach](https://learn.microsoft.com/en-gb/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-7.4) statement.  1. Set the $restorePointId as a variable and the $RPIds as a collection. With each iteration, the foreach statement will set the $restorePointId variable to the next value in the $RPIds collection. 2. Specify the [Get-VBRRestorePoint](get-vbrrestorepoint.md) and Publish-VBRArchiveRestorePoint cmdlets. With each iteration, the foreach statement will execute these cmdlets. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)

Page updated 6/18/2024

Page content applies to build 13.0.1.1071
