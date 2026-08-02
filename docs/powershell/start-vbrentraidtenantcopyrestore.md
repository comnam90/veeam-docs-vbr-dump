---
title: "Start-VBREntraIDTenantCopyRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrentraidtenantcopyrestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Start-VBREntraIDTenantCopyRestore


Short Description

Starts a restore session from a backup copy of a Microsoft Entra ID tenant.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBREntraIDTenantCopyRestore -RestorePoint <VBRNASBackupRestorePoint> [-Reason <String>] [-RetrievalSettings <VBRUnstructuredBackupColdStorageRetrievalSettings>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet starts a restore session for an Entra ID tenant using a backup copy.

If the application used for adding the tenant does not have the required roles, use the [Request-VBREntraIDLogin](request-vbrentraidlogin.md) cmdlet to get access to Entra ID. For more information on the required permissions, see the [Permissions](https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_permissions.html?ver=13) section in the User Guide for Microsoft Entra ID.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| RestorePoint | Specifies a restore point. The cmdlet will start restore to recover backup files to the specified restore point. | Accepts the VBRNASBackupRestorePoint object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Reason | Specifies the reason of the restore operation. | String | False | Named | False |
| RetrievalSettings | Specifies the retrieval policy settings. The cmdlet will use these settings to retrieve data from archive repositories. | Accepts the VBRUnstructuredBackupColdStorageRetrievalSettings object. To create this object, run the [New-VBRUnstructuredBackupColdStorageRetrievalSettings](new-vbrunstructuredbackupretrievalsettings.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will modify settings of managed file shares without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBREntraIDTenantRestoreSession](vbrentraidtenantrestoresession.md) object that contains properties of the tenant restore session.

Examples

Starting Entra ID Tenant Restore Session from Backup Copy

This example shows how to start a tenant restore session from the Tenant backup backup copy located on the \\WinSRV2049\Documents file share.

|  |
| --- |
| $backup = Get-VBRUnstructuredBackup -Name "Tenant Backup"  $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  $restorePoint = Get-VBRUnstructuredBackupRestorePoint -Server $server -Backup $backup  $retrieval = New-VBRUnstructuredBackupColdStorageRetrievalSettings -AmazonS3GlacierRetrievalPolicy HighPriority -AvailabilityPeriodDays 7 -EnableExpirationNotification -ExpirationHoursThreshold 24  $tenantRestoreSession = Start-VBREntraIDTenantCopyRestore -RestorePoint $restorePoint -Reason "users restore" -RetrievalSettings $retrieval |

Perform the following steps:

1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
3. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $server variable as the Server parameter value and the $backup variable as the Backup parameter value. Save the result to the $restorePoint variable.
4. Run the [New-VBRUnstructuredBackupColdStorageRetrievalSettings](new-vbrunstructuredbackupretrievalsettings.md) cmdlet. Specify the AmazonS3GlacierRetrievalPolicy, AvailabilityPeriodDays and ExpirationHoursThreshold parameter values. Save the result to the $retrieval variable.
5. Run the Start-VBREntraIDTenantCopyRestore cmdlet. Set the $restorePoint variable as the RestorePoint parameter value and the $retrieval variable as the RetrievalSettings parameter value. Specify the Reason parameter value. Save the result to the $tenantRestoreSession variable.

Related Commands

* [Start-VBREntraIDTenantRestore](start-vbrentraidtenantrestore.md)
* [New-VBRUnstructuredBackupColdStorageRetrievalSettings](new-vbrunstructuredbackupretrievalsettings.md)

Page updated 2026-06-29

