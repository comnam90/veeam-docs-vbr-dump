---
title: "Publish-VBRCloudArchiveRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/publish-vbrcloudarchiverestorepoint.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Publish-VBRCloudArchiveRestorePoint


Short Description

Retrieves tenant data from archive storage.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Retrieve tenant data from Amazon S3 Glacier archive storage.

|  |
| --- |
| Publish-VBRCloudArchiveRestorePoint -RestorePoint <CCommonOib> -AvailabilityPeriodDays <uint32> -AmazonS3GlacierRetrievalPolicy {Expedited | Standard | Bulk} [-EnableExpirationNotification] [-ExpirationHoursThreshold <int>] [-RunAsync]  [<CommonParameters>] |

* Retrieve tenant data from Azure Archive storage.

|  |
| --- |
| Publish-VBRCloudArchiveRestorePoint -RestorePoint <CCommonOib> -AvailabilityPeriodDays <uint32> -AzureArchiveRetrievalPolicy {StandardPriority | HighPriority} [-EnableExpirationNotification] [-ExpirationHoursThreshold <int>] [-RunAsync]  [<CommonParameters>] |

* Retrieve tenant data from S3 compatible object storage with data archiving.

|  |
| --- |
| Publish-VBRCloudArchiveRestorePoint -RestorePoint <CCommonOib> -AvailabilityPeriodDays <UInt32> -S3GlacierCompatibleRetrievalPolicy <VBRS3GlacierCompatibleRetrievalPolicy> [-EnableExpirationNotification] [-ExpirationHoursThreshold <Int32>] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet retrieves tenant data from archive storage and places them in the capacity tier of scale-out backup repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of tenant backups which you want to retrieve. | Accepts the CCommonOib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| AvailabilityPeriodDays | Specifies a period in days during which the retrieved archive backup files will be available. | Uint32 | True | Named | False |
| AmazonS3GlacierRetrievalPolicy | Defines the method of data retrieval for Amazon S3 Glacier object storage. You can retrieve data using one of the following method:   * Expedited: Use this method to retrieve archived data within 1-5 minutes. Note that this is the most expensive method. * Standard: Use this method to retrieve archived data within 3-5 hours. * Bulk: Use this method to retrieve archived data within 5-12 hours. | VBRAmazonS3GlacierRetrievalPolicy | True | Named | False |
| AzureArchiveRetrievalPolicy | Defines the method of data retrieval for Azure Archive storage. You can retrieve data using one of the following method:   * StandardPriority: Use this method to retrieve archived data within 15 hours. * HighPriority: Use this method to retrieve archived data within an hour. Note that this is the most expensive method. | VBRAzureArchiveRestrievalPolicy | True | Named | False |
| S3GlacierCompatibleRetrievalPolicy | Defines the method of data retrieval for S3 compatible object storage with data archiving. You can retrieve data using one of the following method:   * Expedited: Use this method to retrieve archived data within 1-5 minutes. Note that this is the most expensive method. * Standard: Use this method to retrieve archived data within 3-5 hours. * Bulk: Use this method to retrieve archived data within 5-12 hours. | VBRS3GlacierCompatibleRetrievalPolicy | True | Named | False |
| EnableExpirationNotification | Enables sending of notification about upcoming expiration of the retrieved archive backup files availability.  Default: False. | SwitchParameter | False | Named | False |
| ExpirationHoursThreshold | For the EnableExpirationNotification parameter. Specifies the moment when the user receives the notification about upcoming expiration of the retrieved archive backup files availability. | Int | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCloudArchiveRestorePoint object that contains information on tenant data retieved from archive storage and places them in the capacity extents of scale-out backup repository.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Retrieving Tenant Data from Amazon S3 Glacier Archive Storage

|  |  |
| --- | --- |
| This example shows how to retrieve the ABC Company tenant data from Amazon S3 Glacier archive storage with the following settings:   * Data retrieval will take from 3-5 hours. * The retrieved archive backup files will be available for 14 days.   |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  $restorepoint = Get-VBRCloudArchiveRestorePoint -Tenant $tenant -Id "3e57a915-2755-4297-be14-deddb8564ca9"  Publish-VBRCloudArchiveRestorePoint -RestorePoint $restorepoint -AvailabilityPeriodDays 14 -AmazonS3GlacierRetrievalPolicy Standard -RunAsync |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.  1. Run the [Get-VBRCloudArchiveRestorePoint](get-vbrcloudarchiverestorepoint.md) cmdlet. Set the $tenant variable as the Tenant parameter value. Specify the Id parameter value. Save the result to the $restorepoint variable. 2. Run the Publish-VBRCloudArchiveRestorePoint cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the AvailabilityPeriodDays parameter value. * Specify the AmazonS3GlacierRetrievalPolicy parameter value. * Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Retrieving Tenant Data from Azure Archive Storage

|  |  |
| --- | --- |
| This example shows how to retrieve the ABC Company tenant data from Azure Archive storage with the following settings:   * Data retrieval will take about an hour. * The retrieved archive backup files will be available for 7 days.   |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  $restorepoint = Get-VBRCloudArchiveRestorePoint -Tenant $tenant -Id "3e57a915-2755-4297-be14-deddb8564ca9"  Publish-VBRCloudArchiveRestorePoint -RestorePoint $restorepoint -AvailabilityPeriodDays 7 -AzureArchiveRetrievalPolicy StandardPriority -RunAsync |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.  1. Run the [Get-VBRCloudArchiveRestorePoint](get-vbrcloudarchiverestorepoint.md) cmdlet. Set the $tenant variable as the Tenant parameter value. Specify the Id parameter value. Save the result to the $restorepoint variable. 2. Run the Publish-VBRCloudArchiveRestorePoint cmdlet. Specify the following settings:  * Set the $restorepoint variable as the RestorePoint parameter value. * Specify the AvailabilityPeriodDays parameter value. * Specify the AzureArchiveRetrievalPolicy parameter value. * Provide the RunAsync parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Retrieving Tenant Data from Amazon S3 Glacier Archive Storage for Multiple Restore Points

|  |  |
| --- | --- |
| This example shows how to retrieve several restore points of the XYZ Company tenant data from the Amazon S3 Glacier archive storage with the following settings:   * Data retrieval will take from 3-5 hours.  * The retrieved archive backup files will be available for 5 days.   |  | | --- | | Get-VBRCloudArchiveRestorePoint  $RPIds = @('2312a0c3-8e9d-48fe-b48e-5a081f1ca525', '9b6bd9c3-f29e-4323-ad85-cbbf9bec2642')  $tenant = Get-VBRCloudTenant -Name "XYZ Company"  foreach ($restorePointId in $RPIds)  {     $restorepoint = Get-VBRCloudArchiveRestorePoint -Tenant $tenant -Id $RPIds     Publish-VBRCloudArchiveRestorePoint -RestorePoint $restorepoint -AvailabilityPeriodDays 5 -AmazonS3GlacierRetrievalPolicy Standard -RunAsync  } |  Perform the following steps:   1. Get a list of all restore points. Run the [Get-VBRCloudArchiveRestorePoint](get-vbrcloudarchiverestorepoint.md) cmdlet. The cmdlet will return an array of restore points of tenant backups located in the archive tier. Select the necessary restore points from an array of restore points. 2. Define the array of restore points. Specify the necessary restore point IDs. Save the result to the $restorePointIds variable. 3. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 4. Run the [foreach](https://learn.microsoft.com/en-gb/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-7.4) loop.  1. Set the $restorePointId as a variable and the $RPIds as a collection. With each iteration, the foreach statement will set the $restorePointId variable to the next value in the $RPIds collection. 2. Specify the [Get-VBRCloudArchiveRestorePoint](get-vbrcloudarchiverestorepoint.md) and Publish-VBRCloudArchiveRestorePoint cmdlets. With each iteration, the foreach statement will execute these cmdlets. |

Related Commands

* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Get-VBRCloudArchiveRestorePoint](get-vbrcloudarchiverestorepoint.md)


