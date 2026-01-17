---
title: "Get-VEHANABackup"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/get-vehanabackup.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# Get-VEHANABackup


Short Description

Returns backups created by Veeam Plug-in for SAP HANA.

Applies to

Veeam Backup & Replication

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VEHANABackup [-Name <String[]>] [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of backups created by Veeam Plug-in for SAP HANA. After you get the backups, you can use the [Start-VEHANARestoreSession](start-vehanarestoresession.md) cmdlet to start a restore session from a backup.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of backup names. The cmdlet will return SAP HANA backups with these names.  This parameter accepts wildcard characters. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see the [About CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216) section of Microsoft Docs.

Output Object

The cmdlet returns the [IVEHANABackup](vehanabackup.md)[] array that contains backups created by Veeam Plug-in for SAP HANA.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All SAP HANA Backups

|  |  |
| --- | --- |
| This command returns an array of all SAP HANA backups stored in backup repositories associated with the backup server. Save the result to the $backup variable to be able to use it with other cmdlets.  |  | | --- | | $backup = Get-VEHANABackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific SAP HANA Backups

|  |  |
| --- | --- |
| This command returns an array of SAP HANA backups with the specified names. Use the wildcard \* character to get all backups whose names begin with "SAP HANA". Save the result to the $backup variable to be able to use it with other cmdlets.  |  | | --- | | $backup = Get-VEHANABackup -Name "SAP HANA\*" | |


