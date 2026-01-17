---
title: "New and Updated Cmdlets"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new_updated_cmdlets.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# New and Updated Cmdlets


This section contains information on new and updated Veeam Explorers PowerShell cmdlets in Veeam Backup & Replication 12.1.

Veeam Explorer for Oracle

In this version, the Server parameter was added to the [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md) cmdlet. Use this parameter instead of the Sever parameter, which will become obsolete in a future version.

Veeam Explorer for PostgreSQL

In this version, new cmdlets were added to the Veeam Explorer for PostgreSQL PowerShell module, which allow you to perform instant recovery and export operations.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VEPSQLDatabase](get-vepsqldatabase.md) | Returns backed-up PostgreSQL databases. | | [Get-VEPSQLDatabaseExport](get-vepsqldatabaseexport.md) | Returns PostgreSQL databases with ongoing export sessions. | | [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md) | Returns PostgreSQL instances that are published within an instant recovery session. | | [Get-VEPSQLPublishedDatabase](get-vepsqlpublisheddatabase.md) | Returns published PostgreSQL databases. | | [New-VEPSQLIRSwitchOverOptions](new-vepsqlirswitchoveroptions.md) | Defines the switchover option that you can apply to the instant recovery session of a PostgreSQL instance. | | [Restart-VEPSQLDatabaseExport](restart-vepsqldatabaseexport.md) | Restarts a failed export process for a backed-up PostgreSQL database. | | [Restart-VEPSQLInstanceInstantRecovery](restart-vepsqlinstanceinstantrecovery.md) | Restarts a failed instant recovery process for a PostgreSQL instance. | | [Set-VEPSQLInstanceInstantRecovery](set-vepsqlinstanceinstantrecovery.md) | Modifies switchover settings for a specified PostgreSQL instance. | | [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md) | Starts an export process for a backed-up or a published PostgreSQL database. | | [Start-VEPSQLInstanceInstantRecovery](start-vepsqlinstanceinstantrecovery.md) | Performs instant recovery of backed-up PostgreSQL instances. | | [Stop-VEPSQLDatabaseExport](stop-vepsqldatabaseexport.md) | Starts an export process for a backed-up or a published PostgreSQL database. | | [Stop-VEPSQLInstanceInstantRecovery](stop-vepsqlinstanceinstantrecovery.md) | Stops an active instant recovery session for a PostgreSQL instance. | | [Switch-VEPSQLInstanceInstantRecovery](switch-vepsqlinstanceinstantrecovery.md) | Performs switchover of a PostgreSQL instance published within an instant recovery session. | |

Veeam Explorer for SAP HANA

In Veeam Backup & Replication 12.1, the Veeam Explorer for SAP HANA PowerShell module was added, which allows you to restore your SAP HANA data from backups created with Veeam Backup & Replication and a standalone Veeam Plug-in for SAP HANA. For a list of the new cmdlets, see [Veeam Explorer for SAP HANA](veeam_explorer_for_sap_hana.md).

Veeam Explorer for Microsoft Exchange

In this version, new cmdlets were added to the Veeam Explorer for Microsoft Exchange PowerShell module.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VEXMailSettings](get-vexmailsettings.md) | Returns Veeam Explorer for Microsoft Exchange email settings. | | [Set-VEXMailSettings](set-vexmailsettings.md) | Modifies Veeam Explorer for Microsoft Exchange email settings. | |

Veeam Explorer for Microsoft SharePoint

In this version, new cmdlets were added to the Veeam Explorer for Microsoft SharePoint PowerShell module and one cmdlet was updated.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VESPMailSettings](get-vespmailsettings.md) | Returns Veeam Explorer for Microsoft SharePoint email settings. | | [Set-VESPMailSettings](set-vespmailsettings.md) | Modifies Veeam Explorer for Microsoft SharePoint email settings. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VBRSharePointItemRestoreSession](start-vbrsharepointitemrestoresession.md) | Parameter removed: SiteCollection | |

Veeam Explorer for Microsoft OneDrive for Business

In this version, new cmdlets were added for Veeam Explorer for Microsoft OneDrive for Business.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VEODMailSettings](get-veodmailsettings.md) | Returns Veeam Explorer for Microsoft OneDrive for Business email settings. | | [Set-VEODMailSettings](set-veodmailsettings.md) | Modifies Veeam Explorer for Microsoft OneDrive for Business email settings. | |

Veeam Explorer for Microsoft Teams

In this version, new cmdlets were added to the Veeam Explorer for Microsoft Teams PowerShell module.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VETMailSettings](get-vetmailsettings.md) | Returns Veeam Explorer for Microsoft Teams email settings. | | [Set-VETMailSettings](set-vetmailsettings.md) | Modifies Veeam Explorer for Microsoft Teams email settings. | |


