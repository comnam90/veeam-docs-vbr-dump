---
title: "Disable-VSBJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vsbjob.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Disable-VSBJob (obsolete)


Short Description

Puts a selected SureBackup job on hold.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Disable-VBRSureBackupJob](disable-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VSBJob -Job <CSbJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet puts a selected SureBackup job on hold. The job and its settings are not deleted from Veeam Backup & Replication. You can enable the job at any time by running the [Enable-VSBJob](enable-vsbjob.md) cmdlet.

Run the [Stop-VSBJob](stop-vsbjob.md) cmdlet to stop the job once without disabling it.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the SureBackup job you want to disable. | Accepts the CSbJob[] object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Related Commands

[Get-VSBJob](get-vsbjob.md)


