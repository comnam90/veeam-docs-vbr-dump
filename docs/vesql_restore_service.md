---
title: "Deploying Persistent and Non-Persistent Components"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_service.html"
last_updated: "11/5/2025"
product_version: "13.0.1.1071"
---

# Deploying Persistent and Non-Persistent Components


To perform data recovery operations, Veeam Explorer for Microsoft SQL Server uses persistent agent or non-persistent runtime components — they check the valid rights assignments required for database recovery, get information about the databases, and later perform required file operations including database and transaction logs copy. Persistent components remain on the machine until they are manually deleted, while non-persistent components are automatically stopped and removed from the machine after the data recovery session completes.

These components are deployed on the staging server (in case of data export, data recovery to a specific transaction and restore of database schema and data) or on the target server (all remaining operations).

Veeam Explorer for Microsoft SQL Server uses the following components:

* Veeam SQL Agent Service — persistent component deployed by the Veeam Installer Service.
* Veeam Agent — persistent component deployed by the Veeam Installer Service. This component is deployed only if transaction logs are used.

* Veeam SQL Restore Service — non-persistent component deployed through the administrative share.

Persistent components are deployed in a more secure way and handle traffic through a narrower port range. The deployment workflow depends on whether you use the default or the enhanced security mode.

Default Mode

By default, Veeam Explorer for Microsoft SQL Server deploys runtime or persistent components on the staging or target server during data recovery. The default data recovery process works as follows:

* If the Veeam Installer Service on the target or staging server is available, Veeam Explorer for Microsoft SQL Server uses it to deploy persistent agents. For more information on this service, see [Veeam Installer Service](installer_service.md).

The Veeam Installer Service checks whether the necessary persistent components are installed, namely the Veeam SQL Agent Service for database recovery, and the Veeam Agent component if transaction logs are used. If the persistent components are installed, Veeam Explorer for Microsoft SQL Server proceeds with the recovery operation. If they are not installed, the Veeam Installer Service first installs the necessary components and Veeam Explorer for Microsoft SQL Server proceeds with the recovery operation.

* If the Veeam Installer Service on the target or staging server is not available, Veeam Explorer for Microsoft SQL Server attempts to deploy runtime components through the administrative share (for example, \\myserver\ADMIN$). It first checks if the administrative share is available on the target machine or the staging server. The user must have at least Read and Write permissions; Full Control is recommended. Depending on the availability of the administrative share, the workflow is as follows:

* If the administrative share is available, the Veeam SQL Restore Service runtime component is deployed and registered as a service on the target server and, if necessary, on the staging server.
* If the administrative share is not available, the restore operation fails.

Enhanced Security Mode

Veeam Explorer for Microsoft SQL Server also has an enhanced security mode, which allows you to only use persistent components during data recovery. To enable this functionality, go to %ProgramData%\Veeam\Backup\SQLExplorer on the machine where Veeam Explorer for Microsoft SQL Server is running. If a configuration file named Config.xml does not exist in this directory, create this file. In the configuration file, enter the following XML code:

|  |
| --- |
| <Veeam>     <SqlExplorer>         <Agent EnableEnhancedSecurity="True"/>     </SqlExplorer>  </Veeam> |

To finish the configuration, save the Config.xml file and restart Veeam Explorer for Microsoft SQL Server.

With this setting enabled, data recovery works as follows:

* If the Veeam Installer Service on the target or staging server is available, Veeam Explorer for Microsoft SQL Server uses it to deploy persistent agents. The service checks whether the necessary persistent components are installed, namely the Veeam SQL Agent Service for database recovery, and the Veeam Agent component if transaction logs are used. If the persistent components are installed, Veeam Explorer for Microsoft SQL Server proceeds with the recovery operation. If they are not installed, the Veeam Installer Service first installs the necessary components and Veeam Explorer for Microsoft SQL Server proceeds with the recovery operation.
* If the Veeam Installer Service on the target or staging server is not available, the restore operation fails. You can run the restore operation again once the Veeam Installer Service is available.

Considerations

Consider the following:

* All activities of the components are recorded in log files stored in the following locations:

* For persistent components, in the C:\ProgramData\Veeam\Backup\VESQL Restore Service\Logs folder of the staging or target server.
* For non-persistent components, in the Veeam.SQL.Service\_<timestamp> folder, located in the %WINDIR%\Temp directory of the staging or target server.

* To see the ports the persistent and non-persistent components use during data recovery operations, see [Ports](vesql_used_ports.md).
* All persistent and runtime components deployed by Veeam Explorer for Microsoft SQL Server require the Local System account.
* No components are deployed when restoring to a server where the Veeam Backup & Replication console is installed.

Related Topics

* [Ports](vesql_used_ports.md)
* [How Restore Works](vesql_how_restore_works.md)
* [How Publishing Works](vesql_how_publishing_works.md)
* [How Instant Recovery Works](vesql_instant_hiw.md)
* [How Export Works](vesql_how_export_works.md)


