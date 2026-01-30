---
title: "Stop-VBRNASInstantRecovery"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrnasinstantrecovery.html"
last_updated: "9/4/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRNASInstantRecovery


Short Description

Stops an instant restore of backups created by the file backup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRNASInstantRecovery -InstantRecovery <VBRNASInstantRecovery> [-Force] [-RunAsync]  [<CommonParameters>] |

Detailed Description

The cmdlet stops an instant restore of backups created by the file backup job. The process comprises the following steps:

1. Removing the shared folder
2. Stopping the agents
3. Updating information in the database

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| InstantRecovery | Specifies an array of instant restore sessions. The cmdlet will stop the instant recovery for each of the specified restore points. | Accepts the [VBRNASInstantRecovery](vbrnasinstantrecovery.md) object. To get this object, run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. | True | 1 | False |
| Force | Defines that the cmdlet will immediately start the dismount procedure.  If the parameter is not specified, the cmdlet will ask for the confirmation to start the dismount procedure for the instant restore session. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Instant Restore Session for File Backup

This example shows how to stop the instant restore session for file backup.

|  |
| --- |
| $nasInstantRecovery = Get-VBRNASInstantRecovery -NASBackupName "Daily SMB1 Backup" -NASServerName "ontap-2"  Stop-VBRNASInstantRecovery -InstantRecovery $nasInstantRecovery |

Perform the following steps:

1. Run the [Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md) cmdlet. Specify the NASBackupName and NASServerName parameter values. Save the result to the $nasInstantRecovery variable.
2. Run the Stop-VBRNASInstantRecovery cmdlet. Set the $nasInstantRecovery variable as the InstantRecovery parameter value.

Related Commands

[Get-VBRNASInstantRecovery](get-vbrnasinstantrecovery.md)


