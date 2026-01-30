---
title: "Get-VBRNASInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrnasinstantrecovery.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNASInstantRecovery


Short Description

Returns active instant restore sessions started to recover backups created by file backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all instant restore sessions started to recover backups created by file backup jobs.

|  |
| --- |
| Get-VBRNASInstantRecovery [-All]  [<CommonParameters>] |

* Get instant restore sessions started to recover backups created by file backup jobs. In this case, the cmdlet will return sessions with specified IDs.

|  |
| --- |
| Get-VBRNASInstantRecovery -Id <guid[]>  [<CommonParameters>] |

* Get instant restore sessions started to recover backups created by file backup jobs. In this case, the cmdlet will return sessions with specified parameters.

|  |
| --- |
| Get-VBRNASInstantRecovery -NASBackupName <string> -NASServerName <string>  [<CommonParameters>] |

* Get instant restore sessions by their names.

|  |
| --- |
| Get-VBRNASInstantRecovery -SessionName <string[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns active instant restore sessions started to recover backups created by file backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| All | Defines that the cmdlet will return all active instant restore sessions started to recover backups created by file backup jobs. | SwitchParameter | False | Named | False |
| Id | Specifies the array of instant restore session IDs. The cmdlet will return the instant restore sessions with these IDs. | Guid[] | True | Named | True (ByPropertyName) |
| NASBackupName | Specifies a name of the file share backup for which the instant restore session was started. The cmdlet will return the instant restore session started to recover backups created by the file backup job with this name. | String | True | Named | True (ByPropertyName) |
| NASServerName | Specifies a name of the host with the repository and mount service where the SMB share is published. The cmdlet will return the instant restore session using this host. | String | True | Named | True (ByPropertyName) |
| SessionName | Specifies the array of instant restore session names. The cmdlet will return active instant restore sessions with these names. | String[] | True | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRNASInstantRecovery](vbrnasinstantrecovery.md)[] object that defines the file share backup recovery session settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Instant Restore Sessions for File Backups

|  |  |
| --- | --- |
| This command returns all instant restore sessions for file backups.  |  | | --- | | Get-VBRNASInstantRecovery | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Instant Restore Sessions for File Backups by Session IDs

|  |  |
| --- | --- |
| This command returns instant restore sessions for file backups by restore session IDs.  |  | | --- | | Get-VBRNASInstantRecovery -Id ("49664A5F-9C55-4A1F-8E6A-1CD5705A684B", "42696B53-6FEC-4148-9354-AA9E4B52DED9") | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Instant Restore Sessions for File Backups by Parameters

|  |  |
| --- | --- |
| This command returns instant restore sessions for file backups with certain parameters.  |  | | --- | | Get-VBRNASInstantRecovery -NASBackupName "Daily SMB1 Backup" -NASServerName "ontap-2" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Instant Restore Sessions for File Backups by Session Names

|  |  |
| --- | --- |
| This command returns instant restore sessions for file backups with certain parameters.  |  | | --- | | Get-VBRNASInstantRecovery -SessionName ("\\Server\Share", "\\OtherServer\OtherShare") | |


