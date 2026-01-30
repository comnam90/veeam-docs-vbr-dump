---
title: "Stop-VBRCloudTapeRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrcloudtaperestore.html"
last_updated: "4/12/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRCloudTapeRestore


Short Description

This cmdlet stops the restore session of the tenant data from tape.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

|  |
| --- |
| Stop-VBRCloudTapeRestore -Session <VBRBackupSession>  [<CommonParameters>] |

Detailed Description

This cmdlet stops the restore session of the tenant data from tape.

Run the [Start-VBRCloudTapeRestore](start-vbrcloudtaperestore.md) cmdlet to start the restore session.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Session | Specifies the tape restore session that you want to stop. | Accepts the [VBRBackupSession](vbrbackupsession.md) object. To get this object, run the [Get-VBRCloudTapeRestoreSession](get-vbrcloudtaperestoresession.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Starting and Stopping Restore Session for Tenant Backups

This example shows how to start a restore session of the tenant backups and then to stop the running session of backups restore from the tape.

|  |
| --- |
| $repository = Get-VBRCloudTapeBackupTenantRepository  Start-VBRCloudTapeRestore -BackupObject $repository -PointInTime "11/26/23" -RunAsync  CreationTime : 11/26/2023 5:47:38 PM  EndTime      : 1/1/1900 12:00:00 AM  JobId        : 3d6c6bc4-fca3-4815-854a-3e5095a2f452  Result       : None  State        : Starting  Id           : aae753f4-bcbf-427b-9cb8-bc9ee92acb6b  $session = Get-VBRCloudTapeRestoreSession -Id aae753f4-bcbf-427b-9cb8-bc9ee92acb6b  Stop-VBRCloudTapeRestore -Session $session |

Perform the following steps:

1. Run the [Get-VBRCloudTapeBackupTenantRepository](get-vbrcloudtapebackuptenantrepository.md) cmdlet. Save the result to the $repository variable.
2. Run the [Start-VBRCloudTapeRestore](start-vbrcloudtaperestore.md) cmdlet. Set the $repository variable as the BackupObject parameter value. Specify the PointInTime parameter value. Provide the RunAsync parameter.
3. Run the [Get-VBRCloudTapeRestoreSession](get-vbrcloudtaperestoresession.md) cmdlet. Specify the Id parameter value. Save the result to the $session variable.
4. Run the Set-VBRNDMPServer cmdlet. Set the $session variable as the Session parameter value.

Related Commands

* [Get-VBRCloudTapeBackupTenantRepository](get-vbrcloudtapebackuptenantrepository.md)
* [Start-VBRCloudTapeRestore](start-vbrcloudtaperestore.md)
* [Get-VBRCloudTapeRestoreSession](get-vbrcloudtaperestoresession.md)


