---
title: "Add-VBRCloudArchiveBackupAvailabilityPeriod"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudarchivebackupavailabilityperiod.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Add-VBRCloudArchiveBackupAvailabilityPeriod


Short Description

Extends the availability of the tenant backup files located in the archive storage.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRCloudArchiveBackupAvailabilityPeriod -RestorePoint <CCommonOib> -AvailabilityPeriodDays <uint32> [-RunAsync]  [<CommonParameters>] |

Detailed Description

Extends the availability of the tenant backup files located in the archive storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the restore point for which you want to extend the availability. | Accepts the CCommonOib object. To create this object, run the [Get-VBRCloudArchiveRestorePoint](get-vbrcloudarchiverestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| AvailabilityPeriodDays | Specifies a period in days during which the retrieved archive backup files will be available. | Uint32 | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCloudArchiveBackupAvailabilityPeriod object that contains settings of availability of the tenant backup files located in the archive storage.

Examples

Extending Availability of Tenant Backup Files Located in Archive Storage

This example shows how to extend availability of the 3e57a915-2755-4297-be14-deddb8564ca9 restore point of the ABC Company tenant.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "ABC Company"  $restorepoint = Get-VBRCloudArchiveRestorePoint -Tenant $tenant -Id "3e57a915-2755-4297-be14-deddb8564ca9"  Add-VBRCloudArchiveBackupAvailabilityPeriod -RestorePoint $restorepoint -AvailabilityPeriodDays 5 |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.

1. Run the [Get-VBRCloudArchiveRestorePoint](get-vbrcloudarchiverestorepoint.md) cmdlet. Set the $tenant variable as the Tenant parameter value. Specify the Id parameter value. Save the result to the $restorepoint variable.
2. Run the Add-VBRCloudArchiveBackupAvailabilityPeriod cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Specify the AvailabilityPeriodDays parameter value.

Related Commands

* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Get-VBRCloudArchiveRestorePoint](get-vbrcloudarchiverestorepoint.md)


