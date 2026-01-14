---
title: "New-VSBJobOptions (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vsbjoboptions.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# New-VSBJobOptions (obsolete)

In this article

Short Description

Sets SureBackup job options.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VSBJobOptions [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet lets you edit job settings of SureBackup jobs.

This cmdlet returns the CDRJobOptions object containing the default settings of the SureBackup job you want to edit. You can customize any setting that you want to apply. This object is then used in the [Set-VSBJobOptions](set-vsbjoboptions.md) cmdlet.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Setting SureBackup Job Options

This command creates a CDRJobOptions object with the following settings:

* The EmailNotification is enabled
* The EmailNotificationAddresses is set to mailto@veeam.com
* The RunningVmsNumber is set to 6
* The other settings are left by default

|  |
| --- |
| $sureoptions = New-VSBJobOptions  $sureoptions.EmailNotification = $true  $sureoptions.EmailNotificationAddresses = "mailto@veeam.com"  $sureoptions.RunningVmsNumber = 6  $sureoptions  RunManually                : True |

Page updated 6/3/2024

Page content applies to build 13.0.1.1071
