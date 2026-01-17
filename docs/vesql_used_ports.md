---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vesql_used_ports.html"
last_updated: "1/15/2026"
product_version: "13.0.1.1071"
---

# Ports


The following table lists network ports that must be opened to manage traffic during recovery from image-level backups of Microsoft SQL Server data.

For information on the ports that must be opened when creating image-level backups of Microsoft SQL Server machines, see the Guest Processing Components and Log Shipping Components subsections of the [Ports](used_ports.md) section.

For information on the ports that must be opened when working with backups created with Veeam Plug-In for Microsoft SQL Server, see the [Ports](ports_mssql.md) section for standalone plug-ins or the [Ports](plan_and_manage_used_ports.md) section for managed plug-ins.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Backup server, Veeam Backup & Replication console, mount server associated with the backup repository (only for Instant Recovery or restore from Enterprise Manager) | Target machine with Microsoft SQL Server, staging server | TCP, UDP | 135, 445 | Ports used to deploy the runtime coordination process on the target machine. |
| TCP | 6173 | Port used by the runtime coordination process that is deployed on the target machine. |
| TCP | 6160 | Port used to communicate with Veeam Installer Service. |
| TCP | 1433, 1434 | Ports used to communicate with the Microsoft SQL Server installed on the target machine during application-item restore.  For more information, see [this Microsoft article](http://msdn.microsoft.com/en-us/library/cc646023.aspx#BKMK_ssde). |
| UDP | 1434 | Port used by the Microsoft SQL Server Browser service.  For more information, see [this Microsoft article](https://technet.microsoft.com/en-us/library/ms181087%28v%3Dsql.130%29.aspx). |
| TCP | 1026 to 1034 | Default RPC range for the Veeam SQL Restore Service runtime components installed on a target or staging Microsoft SQL Server machine. Each runtime component uses the next available port in the range, and only during application item restore.  For more information on the Veeam SQL Restore Service non-persistent runtime component, see [Deploying Persistent and Non-Persistent Components](vesql_restore_service.md).  Note: You must manually open this port range in Microsoft Windows Firewall. |
| TCP | 1025 | Port used by the Veeam SQL Agent Service persistent component installed on the target or staging Microsoft SQL Server machine. The port is used only during application item restore.  For more information on the Veeam SQL Agent Service persistent component, see [Deploying Persistent and Non-Persistent Components](vesql_restore_service.md).  Note: You must manually open this port in Microsoft Windows Firewall. |
| Backup server | Mount server associated with the backup repository | TCP | 6170 | Port used for communication with Veeam Mount Service. |
| Target machine with Microsoft SQL Server, staging server | Mount server associated with the backup repository | TCP | 3260 to 3270 | Port range opened by Veeam Backup & Replication to manage iSCSI traffic during restore to the target machine.  This port range is opened only during application item restore.  For more information, see [How Mounting Works](vesql_mount_operations.md). |
| Backup repository | TCP | 6162 or 2500 to 3300 | These ports are used by the Veeam Agent persistent component deployed on the target or staging server and only during transaction log restore.  Port 6162 is used to connect to the Veeam Data Mover Service (for Windows-based backup servers) or Veeam Transport Service (for Linux-based backup servers).  The 2500 to 3300 port range is the default port range for data transfer over the network.  For more information on the components used during data recovery, see [Deploying Persistent and Non-Persistent Components](vesql_restore_service.md). |


