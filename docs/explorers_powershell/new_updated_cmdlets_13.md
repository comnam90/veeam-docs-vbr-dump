---
title: "new_updated_cmdlets_13"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/new_updated_cmdlets_13.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---


In this article

This section contains information on new and updated Veeam Explorers PowerShell cmdlets in Veeam Backup & Replication 13.

Veeam Explorer for Oracle

In this version, the deprecated ServerName parameter of the [Get-VEORPublishedDatabase](get-veorpublisheddatabase.md) cmdlet has been removed. Use the Backup parameter instead.

The Backup parameter of the [Start-VEORRMANRestoreSession](start-veorrmanrestoresession.md) cmdlet became required.

Veeam Explorer for PostgreSQL

In this version, the LinuxTargetHost parameter of the [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md) cmdlet became optional. Using [Start-VEPSQLDatabaseExport](start-vepsqldatabaseexport.md) to export data to the local host where the Veeam Backup & Replication console is installed is not supported — Veeam Backup & Replication 13 only supports Linux-based backup servers.

Veeam Explorer for SAP HANA

In this version, the RestoreSession parameter of the [Stop-VEHANARestoreSession](stop-vehanarestoresession.md) cmdlet has become deprecated. Use the Session parameter instead.

Veeam Explorer for MongoDB

In Veeam Backup & Replication 13, new cmdlets were added to the Veeam Explorer for MongoDB PowerShell module, which allow you to perform publishing operations and restore instances to a point-in-time state.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Start-VEMDBDataRestore](start-vemdbdatarestore.md) | Restores MongoDB collections or the entire MongoDB instance. Use this cmdlet instead of the deprecated Start-VEMDBRestoreJob cmdlet. | | [Get-VEMDBDataRestore](get-vemdbdatarestore.md) | Returns active MongoDB restore jobs. Use this cmdlet instead of the deprecated Get-VEMDBRestoreJob cmdlet. | | [Stop-VEMDBDataRestore](stop-vemdbdatarestore.md) | Stops the restore process for backed-up MongoDB data. Use this cmdlet instead of the deprecated Stop-VEMDBRestoreJob cmdlet. | | [Get-VEMDBPublishedCollection](get-vemdbpublishedcollection.md) | Returns published MongoDB collections. | | [Get-VEMDBPublishJob](get-vemdbpublishjob.md) | Returns active publishing sessions for backed-up MongoDB instances. | | [Get-VEMDBRestoreInterval](get-vemdbrestoreinterval.md) | Returns details on the available restore period for a backed-up MongoDB instance. | | [Start-VEMDBPublishJob](start-vemdbpublishjob.md) | Publishes a backed-up MongoDB instance. | | [Stop-VEMDBPublishJob](stop-vemdbpublishjob.md) | Unpublishes a MongoDB instance from the target server. | |

In this version, additional parameters were added to the [Start-VEMDBDataRestore](start-vemdbdatarestore.md) cmdlet that allow you to restore instances to a point-in-time state and authenticate to MongoDB deployments using X.509 authentication.

* UseSystemCertificateAuthority
* CertificateAuthorityPemFilePath
* UseX509Authentication
* ClientCertificateAndKeyPemFilePath
* ClientKeyPassword
* ToPointInTimeUTC

The PublishedCollection parameter was added to the [New-VEMDBCollectionRestoreOptions](new-vemdbcollectionrestoreoptions.md) cmdlet. Use this parameter to specify restore options for published collections.

Veeam Explorer for Microsoft Exchange

In this version, new cmdlets were added to the Veeam Explorer for Microsoft Exchange PowerShell module, which allow you to get, enable and disable the secure LDAP mode for Veeam Explorer for Microsoft Exchange.

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)New Cmdlets

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| | Cmdlet | Operation | | --- | --- | | [Get-VEXUseSecureLdap](get-vexusesecureldap.md) | Returns the state of the secure LDAP mode for Veeam Explorer for Microsoft Exchange. | | [Enable-VEXUseSecureLdap](enable-vexusesecureldap.md) | Enables the secure LDAP mode for Veeam Explorer for Microsoft Exchange. | | [Disable-VEXUseSecureLdap](disable-vexusesecureldap.md) | Disables the secure LDAP mode for Veeam Explorer for Microsoft Exchange. | |

Page updated 7/29/2025

Page content applies to build 13.0.1.1071
