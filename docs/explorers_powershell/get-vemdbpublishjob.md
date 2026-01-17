---
title: "Get-VEMDBPublishJob"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vemdbpublishjob.html"
last_updated: "7/11/2025"
product_version: "13.0.1.1071"
---


In this article

Short Description

Returns active publishing sessions for backed-up MongoDB instances.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a publish job with the specified job ID.

|  |
| --- |
| Get-VEMDBPublishJob [-JobId <Guid>] [<CommonParameters>] |

* Get a publish job with the specified source instance.

|  |
| --- |
| Get-VEMDBPublishJob -SourceInstance <String[]> [<CommonParameters>] |

* Get a publish job with the specified target instance.

|  |
| --- |
| Get-VEMDBPublishJob -TargetInstance <String[]> [<CommonParameters>] |

Detailed Description

This cmdlet returns information about the publishing process for backed-up MongoDB instances.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| JobId | Specifies the publishing job ID. The cmdlet returns publishing jobs with the specified ID. | GUID | False | Named | True (ByValue) |
| SourceInstance | Specifies names of source MongoDB instances, in the <server>:<port> format (for example, mongodb01:27017). The cmdlet will return publishing jobs performed for the specified instances.  This parameter accepts wildcard characters. | String[] | True | Named | False |
| TargetInstance | Specifies names of published MongoDB instances, in the <server>:<port> format (for example, mongodb01:27017). The cmdlet will return the publishing jobs performed for the specified instances.  This parameter accepts wildcard characters. | String[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [VEMDBInstancePublish](vemdbinstancepublish.md)[] array that contains information about the publishing process of MongoDB instances.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Publish Jobs

|  |  |
| --- | --- |
| This command returns a list of all published MongoDB instances. Save the result to the $publish variable to be able to use it with other cmdlets.  |  | | --- | | $publish = Get-VEMDBPublishJob | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Publishing Jobs that Use Specific Source MongoDB Instance

|  |  |
| --- | --- |
| This command returns an array of MongoDB publishing jobs that use mongodb01:27017 as a source instance. Save the result to the $publish variable to be able to use it with other cmdlets.  |  | | --- | | $publish = Get-VEMDBPublishJob -SourceInstance "mongodb01:27017" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Publishing Jobs with Target MongoDB Instances that Begin with Certain String

|  |  |
| --- | --- |
| This command returns an array of MongoDB publishing jobs that have published instances whose names begin with "mongo". Save the result to the $publish variable to be able to use it with other cmdlets.  |  | | --- | | $publish = Get-VEMDBPublishJob -TargetInstance "mongo\*" | |

Page updated 7/11/2025

Page content applies to build 13.0.1.1071
