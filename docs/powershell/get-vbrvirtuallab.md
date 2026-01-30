---
title: "Get-VBRVirtualLab"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvirtuallab.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRVirtualLab


Short Description

Returns virtual labs with main settings.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRVirtualLab [-Id <guid[]>] [-Name <string[]>] [-Platform <VBRVirtualLabPlatform> {VMWare | HyperV | vCD}]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRVirtualLab>[] object that contains an array of virtual labs and their main settings. You can use this object with the following cmdlets:

* [Remove-VBRVirtualLab](remove-vbrvirtuallab.md) - to remove virtual labs from Veeam Backup & Replication infrastructure.
* [Add-VBRViSureBackupJob](add-vbrvisurebackupjob.md) - to create a SureBackup job.
* [Set-VBRViSureBackupJob](set-vbrvisurebackupjob.md) - to modify settings of a SureBackup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for virtual labs. The cmdlet will return an array of virtual labs with the specified ID. | Guid[] | False | Named | True (ByValue, |
| Name | Specifies an array of names for virtual labs. The cmdlet will return an array of virtual labs with the specified names. | String[] | False | Named | True (ByValue, ByProperty Name) |
| Platform | Specifies a type of server where the virtual lab is created. The cmdlet will return virtual labs created on the specified platform. You can specify either of the following virtual labs:   * VMWare * HyperV * vCD | VBRVirtualLabPlatform | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVirtualLab>[] object that contains the main settings of VMware virtual labs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Virtual Labs

|  |  |
| --- | --- |
| This command returns all virtual labs that are added to the Veeam Backup & Replication infrastructure. The cmdlet output will contain settings of virtual labs.  |  | | --- | | Get-VBRVirtualLab    IdOnHost    : 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec  Server      : Veeam.Backup.Core.Common.CHost  Platform    : VMWare  Id          : 8762b1ea-3422-4f84-8472-e596d7c8265e  Name        : Exchange Virtual Lab  Description : Created by Powershell at 2/20/2020 5:56 AM.    IdOnHost    : d36893a1-1627-4c18-919f-a1bcadf38e0e  Server      : Veeam.Backup.Core.Common.CHost  Platform    : VMWare  Id          : 36b4435b-ea6b-4fa3-a2a2-9714e1cac5a6  Name        : SQL Virtual Lab  Description : Created by Powershell at 2/20/2020 5:56 AM. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Virtual Lab by ID

|  |  |
| --- | --- |
| This command returns the 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec virtual lab. The cmdlet output will contain settings of the virtual lab.  |  | | --- | | Get-VBRVirtualLab -ID 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec    IdOnHost    : 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec  Server      : Veeam.Backup.Core.Common.CHost  Platform    : VMWare  Id          : 8762b1ea-3422-4f84-8472-e596d7c8265e  Name        : Exchange Virtual Lab  Description : Created by Powershell at 2/20/2020 5:56 AM. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Virtual Lab by Name

|  |  |
| --- | --- |
| This command returns the SQL Virtual Lab virtual lab. The cmdlet output will contain settings of the virtual lab.  |  | | --- | | Get-VBRVirtualLab -Name "SQL Virtual Lab"    IdOnHost    : 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec  Server      : Veeam.Backup.Core.Common.CHost  Platform    : VMWare  Id          : 8762b1ea-3422-4f84-8472-e596d7c8265e  Name        : Exchange Virtual Lab  Description : Created by Powershell at 2/20/2020 5:56 AM. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Getting Virtual Lab by Platform

|  |  |
| --- | --- |
| This command returns virtual labs created on the VMware.  |  | | --- | | Get-VBRVirtualLab -Platform VMWare    IdOnHost    : 6b2686ae-9e1b-4c6e-b6fb-842d7155a9ec  Server      : Veeam.Backup.Core.Common.CHost  Platform    : VMWare  Id          : 8762b1ea-3422-4f84-8472-e596d7c8265e  Name        : Exchange Virtual Lab  Description : Created by Powershell at 2/20/2020 5:56 AM. | |


