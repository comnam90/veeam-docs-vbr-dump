---
title: "New-VBRUnstructuredBackupRetrievalSettings"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrunstructuredbackupretrievalsettings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRUnstructuredBackupRetrievalSettings


Short Description

Defines retrieval policy settings for archive object storage repositories.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define retrieval policy settings for Amazon S3 Glacier archive repository.

|  |
| --- |
| New-VBRUnstructuredBackupRetrievalSettings -AmazonS3GlacierRetrievalPolicy {Expedited | StandardAccelerated | Standard | Bulk} [-AvailabilityPeriodDays <UInt32>] [-EnableExpirationNotification] [-ExpirationHoursThreshold <UInt32>] [<CommonParameters>] |

* Define retrieval policy settings for Microsoft Azure archive repository.

|  |
| --- |
| New-VBRUnstructuredBackupRetrievalSettings [-AvailabilityPeriodDays <UInt32>] -AzureArchiveRetrievalPolicy {StandardPriority | HighPriority} [-EnableExpirationNotification] [-ExpirationHoursThreshold <UInt32>] [<CommonParameters>] |

Detailed Description

This cmdlet defines retrieval policy settings for archive object storage repositories that are used as targets for unstructured data backup jobs.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| AmazonS3GlacierRetrievalPolicy | Defines the method of data retrieval for Amazon S3 Glacier object storage. You can retrieve data using one of the following methods:   * Expedited * StandardAccelerated * Standard * Bulk | VBRAmazonS3GlacierRetrievalPolicy | True | Named | False |
| AzureArchiveRetrievalPolicy | Defines the method of data retrieval for Azure Archive storage. You can retrieve data using one of the following methods:   * StandardPriority * HighPriority | VBRAzureArchiveRetrievalPolicy | True | Named | False |
| AvailabilityPeriodDays | Specifies a period in days during which the retrieved archive backup files will be available. | UInt32 | False | Named | False |
| EnableExpirationNotification | Defines that Veeam Backup & Replication will send the notification about the upcoming expiration of retrieved archive backup files. | SwitchParameter | False | Named | False |
| ExpirationHoursThreshold | Specifies the threshold in hours for sending the notification about the upcoming expiration of retrieved archive backup files.  Note: This parameter is required if you specify the EnableExpirationNotification parameter. | UInt32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUnstructuredBackupRetrievalSettings object that contains retrieval policy settings for archive object storage repositories.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Retrieval Policy Settings for Microsoft Azure Archive Repository

|  |  |
| --- | --- |
| This example shows how to define retrieval policy settings for a Microsoft Azure archive repository.  |  | | --- | | New-VBRUnstructuredBackupRetrievalSettings -AzureArchiveRetrievalPolicy HighPriority -AvailabilityPeriodDays 7 -EnableExpirationNotification -ExpirationHoursThreshold 24 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Retrieval Policy Settings for Amazon S3 Glacier Archive Repository

|  |  |
| --- | --- |
| This example shows how to define retrieval policy settings for a Amazon S3 Glacier archive repository.  |  | | --- | | New-VBRUnstructuredBackupRetrievalSettings -AmazonS3GlacierRetrievalPolicy HighPriority -AvailabilityPeriodDays 7 -EnableExpirationNotification -ExpirationHoursThreshold 24 | |

Page updated 2026-06-29

