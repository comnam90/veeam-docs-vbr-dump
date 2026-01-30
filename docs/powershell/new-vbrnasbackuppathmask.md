---
title: "New-VBRNASBackupPathMask"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrnasbackuppathmask.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# New-VBRNASBackupPathMask


Short Description

Defines an exclusion mask for path for a file backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Exclude the whole file share.

|  |
| --- |
| New-VBRNASBackupPathMask [-ForAllShares]  [<CommonParameters>] |

* Exclude certain folder.

|  |
| --- |
| New-VBRNASBackupPathMask -Path <string> [-ForAllShares]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRNASBackupPathMask object. This object defines an exclusion path for mask for a file backup job. You can exclude either a specific folder or the whole file share.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Path | Specifies a path to the folder that you want to exclude. | String | True | Named | True (ByValue, ByPropertyName) |
| ForAllShares | Defines that the cmdlet will exclude multiple paths under file shares.  Note: You can exclude multiples paths for only for root file shares. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRNASBackupPathMask object that defines an exclusion path for mask for a file backup job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Exclusion Paths for File Backup Job

|  |  |
| --- | --- |
| This command defines the \\EV-NIMBLE\SMB\_Share\New Inc-Exc exclusion path.  |  | | --- | | $exclusionMask = New-VBRNASBackupPathMask -Path "\\EV-NIMBLE\SMB\_Share\New Inc-Exc" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Exclusion Paths for Multiple File Shares

|  |  |
| --- | --- |
| This command defines that the New Inc-Exc folder will be excluded from all file shares.  |  | | --- | | $exclusionMask = New-VBRNASBackupPathMask -Path "New Inc-Exc" -ForAllShares | |


