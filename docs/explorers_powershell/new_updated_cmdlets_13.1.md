---
title: "New and Updated Cmdlets"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new_updated_cmdlets_13.1.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New and Updated Cmdlets


This section contains information on new and updated Veeam Explorers PowerShell cmdlets in Veeam Backup & Replication 13.1.

Veeam Explorer for Microsoft Active Directory

In Veeam Backup & Replication 13.1, new cmdlets were added to the Veeam Explorer for Microsoft Active Directory PowerShell module. These cmdlets use the Veeam Explorers Recovery Service to orchestrate recovery operations for backed-up Microsoft Active Directory databases. This job-based workflow (Start/Get/Stop) replaces the previous synchronous restore-session cmdlets, which are now deprecated. For more information, see [Deprecated Cmdlets](deprecated_cmdlets_13.1.md).

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Start-VEADItemExport](start-veaditemexport.md) | Exports backed-up Active Directory objects and containers. | | [Get-VEADItemExport](get-veaditemexport.md) | Returns information about the export process for Active Directory objects and containers. | | [Stop-VEADItemExport](stop-veaditemexport.md) | Stops the export process for an Active Directory object or container. | | [Start-VEADItemRestore](start-veaditemrestore.md) | Restores backed-up Active Directory objects and containers. | | [Get-VEADItemRestore](get-veaditemrestore.md) | Returns information about the restore process for Active Directory objects and containers. | | [Stop-VEADItemRestore](stop-veaditemrestore.md) | Stops the restore process for an Active Directory object or container. | | [Start-VEADRestoreSessionJob](start-veadrestoresessionjob.md) | Starts a restore session to explore backed-up Microsoft Active Directory databases and to perform operations with these databases. | | [Get-VEADRestoreSessionJob](get-veadrestoresessionjob.md) | Returns active restore sessions started to perform operations with backed-up Microsoft Active Directory databases. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Get-VEADADContainer](get-veadadcontainer.md) | Parameter added: Session | |

Veeam Explorer for PostgreSQL

In Veeam Backup & Replication 13.1, new cmdlets were added to the Veeam Explorer for PostgreSQL PowerShell module, and existing cmdlets were updated with new parameters. These changes include database-level restore for Linux-based PostgreSQL machines and the ability to restore, instantly recover and publish instances to Windows-based target servers.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Start-VEPSQLDatabaseRestore](start-vepsqldatabaserestore.md) | Restores a backed-up PostgreSQL database. | | [Get-VEPSQLDatabaseRestore](get-vepsqldatabaserestore.md) | Returns information about the restore process for backed-up PostgreSQL database. | | [Stop-VEPSQLDatabaseRestore](stop-vepsqldatabaserestore.md) | Stops a restore job for a backed-up PostgreSQL database. | | [New-VEPSQLInstanceCredentials](new-vepsqlinstancecredentials.md) | Creates a PostgreSQL credential object to authenticate to a PostgreSQL database. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md) | Parameters added: WindowsStagingCredentials, WindowsTargetHost. The LinuxTargetHost parameter is now required. | | [Start-VEPSQLInstanceInstantRecovery](start-vepsqlinstanceinstantrecovery.md) | Parameter added: WindowsCredentials | | [Start-VEPSQLInstancePublish](start-vepsqlinstancepublish.md) | Parameter added: WindowsCredentials. The LinuxCredentials parameter is now optional. | | [Start-VEPSQLInstanceRestore](start-vepsqlinstancerestore.md) | Parameter added: WindowsCredentials. The LinuxCredentials parameter is now required. | |

Veeam Explorer for Microsoft SQL Server

In Veeam Backup & Replication 13.1, new cmdlets were added to the Veeam Explorer for Microsoft SQL Server PowerShell module. These cmdlets use the Veeam Explorers Recovery Service to orchestrate recovery operations, replacing the previous synchronous cmdlets that are now deprecated. For more information, see [Deprecated Cmdlets](deprecated_cmdlets_13.1.md). New cmdlets also add support for restoring Microsoft SQL Server databases running on Amazon RDS.

Existing cmdlets were also updated to support Group Managed Service Account (gMSA) authentication.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| New Cmdlets  | Cmdlet | Operation | | [Start-VESQLDatabaseExport](start-vesqldatabaseexport.md) | Exports a backed-up Microsoft SQL Server database. | | [Get-VESQLDatabaseExport](get-vesqldatabaseexport.md) | Returns Microsoft SQL Server databases with ongoing export jobs. | | [Stop-VESQLDatabaseExport](stop-vesqldatabaseexport.md) | Stops an active export job for a Microsoft SQL Server database. | | [Start-VESQLDatabasePublish](start-vesqldatabasepublish.md) | Publishes a backed-up Microsoft SQL Server database. | | [Get-VESQLDatabasePublish](get-vesqldatabasepublish.md) | Returns active publishing jobs for backed-up Microsoft SQL Server databases. | | [Stop-VESQLDatabasePublish](stop-vesqldatabasepublish.md) | Unpublishes a Microsoft SQL Server database from the target server. | | [Start-VESQLDatabaseRestore](start-vesqldatabaserestore.md) | Restores a backed-up Microsoft SQL Server database. | | [Get-VESQLDatabaseRestore](get-vesqldatabaserestore.md) | Returns active restore jobs for Microsoft SQL Server databases. | | [Stop-VESQLDatabaseRestore](stop-vesqldatabaserestore.md) | Stops a restore job for a Microsoft SQL Server database. | | [Start-VESQLPublishedDatabaseExport](start-vesqlpublisheddatabaseexport.md) | Exports a published Microsoft SQL Server database. | | [Start-VESQLRDSRestoreSession](start-vesqlrdsrestoresession.md) | Starts a restore session to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS. | | [Get-VESQLRDSRestoreSession](get-vesqlrdsrestoresession.md) | Returns active restore sessions started to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS. | | [Stop-VESQLRDSRestoreSession](stop-vesqlrdsrestoresession.md) | Stops an active restore session started to explore and restore backed-up Microsoft SQL Server databases running on Amazon RDS. | | [Get-VESQLRDSDatabase](get-vesqlrdsdatabase.md) | Returns backed-up Microsoft SQL Server databases running on Amazon RDS. | | [Get-VESQLRDSDatabaseFile](get-vesqlrdsdatabasefile.md) | Returns database files for a backed-up Microsoft SQL Server database running on Amazon RDS. | | [Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md) | Returns restore points for a backed-up Microsoft SQL Server database running on Amazon RDS. | | [Start-VESQLRDSDatabaseRestore](start-vesqlrdsdatabaserestore.md) | Restores a backed-up Microsoft SQL Server database running on Amazon RDS to an on-premise Microsoft SQL Server machine. | | [Get-VESQLRDSDatabaseRestore](get-vesqlrdsdatabaserestore.md) | Returns active restore jobs for backed-up Microsoft SQL Server databases running on Amazon RDS. | | [Stop-VESQLRDSDatabaseRestore](stop-vesqlrdsdatabaserestore.md) | Stops a restore job for a backed-up Microsoft SQL Server database running on Amazon RDS. | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Updated Cmdlets

|  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- |
| Updated Cmdlets  | Cmdlet | Operation | | [Restore-VESQLIRDatabase](restore-vesqlirdatabase.md) | Parameter added: GMSAAccount. The SqlCredentials parameter is now required. | | [Start-VESQLPluginDatabaseRestore](start-vesqlplugindatabaserestore.md) | Parameter added: GMSAAccount. The SqlCredentials parameter is now required, and the QuickRecovery parameter is now optional. | |

Page updated 2026-07-28

