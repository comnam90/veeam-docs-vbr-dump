---
title: "Get-VBRGlobalNotificationOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrglobalnotificationoptions.html"
last_updated: "1/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRGlobalNotificationOptions

In this article

Short Description

Returns global notification settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRGlobalNotificationOptions  [<CommonParameters>] |

Detailed Description

This cmdlet returns the global notification settings on the following events:

* Low disk space
* Support contract expiration
* New product versions, available updates and patches

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRGlobalNotificationOptions](vbrglobalnotificationoptions.md)

Examples

Getting Global Notification Settings

This command returns global notification settings. The cmdlet output will contain information on these settings.

|  |
| --- |
| Get-VBRGlobalNotificationOptions  StorageSpaceThresholdEnabled   : True  StorageSpaceThreshold          : 10  DatastoreSpaceThresholdEnabled : True  DatastoreSpaceThreshold        : 10  SkipVMSpaceThresholdEnabled    : True  SkipVMSpaceThreshold           : 5  NotifyOnSupportExpiration      : True  NotifyOnUpdates                : True |

Page updated 1/29/2024

Page content applies to build 13.0.1.1071
