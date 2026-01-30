---
title: "Rehydrate-VBRDeletedBackupFile"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/rehydrate-vbrdeletedbackupfile.html"
last_updated: "2/14/2024"
product_version: "13.0.1.1071"
---

# Rehydrate-VBRDeletedBackupFile


Short Description

Rehydrates a backup file deleted from the capacity tier and preserved by insider protection.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Rehydrate-VBRDeletedBackupFile -BackupFile <VBRDeletedDehydratedBackupFile[]> [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet rehydrates a backup file deleted from the capacity tier and preserved by insider protection.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupFile | Specifies a list of deleted backup files you want to rehydrate. | Accepts the VBRDeletedDehydratedBackupFile object. To get this object, run the [Get-VBRDeletedDehydratedBackupFile](get-vbrdeleteddehydratedbackupfile.md) cmdlet. | True | Named | True (ByValue) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

Output Object

None.

Examples

Rehydrating Backup File from Capacity Tier

This command rehydrates a backup file named Company from the capacity tier.

|  |
| --- |
| $backupfile = Get-VBRDeletedDehydratedBackupFile -Name "Company"  Rehydrate-VBRDeletedBackupFile -BackupFile $backupfile[0] -RunAsync |

Perform the following steps:

1. Run the [Get-VBRDeletedDehydratedBackupFile](get-vbrdeleteddehydratedbackupfile.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable.

The [Get-VBRDeletedDehydratedBackupFile](get-vbrdeleteddehydratedbackupfile.md) cmdlet will return an array of deleted backup files. Mind the ordinal number of the necessary backup file (in our example, it is the first backup file in the array).

1. Run the Rehydrate-VBRDeletedBackupFile cmdlet. Set the $backupfile[0] variable as the BackupFile parameter value. Provide the RunAsync parameter.

Related Commands

[Get-VBRDeletedDehydratedBackupFile](get-vbrdeleteddehydratedbackupfile.md)


