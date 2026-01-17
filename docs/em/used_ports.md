---
title: "Ports"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/used_ports.html"
last_updated: "12/22/2025"
product_version: "13.0.1.1071"
---


In this article

This section covers typical Veeam Backup Enterprise Manager connections and default ports required for communication between Enterprise Manager components.

|  |
| --- |
| Note |
| For more information on ports specific for Veeam Backup & Replication infrastructure components, see the [Ports](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13) section of the Veeam Backup & Replication User Guide. |

Veeam Backup Enterprise Manager on Linux (Veeam Software Appliance)

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Software Appliance | Linux-based backup server | TCP | 443 | Default port required for initial connection to a backup server and to its Identity Service.  This is also the default port used by the Veeam Guest Catalog service for catalog replication. |
| 2500 to 2600 | Ports used by the Veeam Guest Catalog service for replicating catalog data. |
| Microsoft Windows-based backup server | TCP | 9405 | Default certificate port used by Enterprise Manager for collecting data from backup servers with version 12 installed. |
| 9392 | Default port required for initial connection to a backup server. |
| 443 | Default port used by the Veeam Guest Catalog service for catalog replication.  This is also the default certificate port used by Enterprise Manager for collecting data from backup servers with version 13 installed. |
| 2500 to 2600 | Ports used by the Veeam Guest Catalog service for replicating catalog data. |
| 49152 to 65535 | Dynamic RPC port range. For more information, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/929851/the-default-dynamic-port-range-for-tcp-ip-has-changed-in-windows-vista). |
| PostgreSQL hosting the Enterprise Manager configuration database | TCP | 5432 | Default port used for communication with PostgreSQL hosting the Enterprise Manager configuration database. |
| VMware vCenter Server | TCP | 443 | Default port used for connection to a vCenter Server and deploying the Veeam Plug-in for vSphere Client. |
| DNS server with forward/reverse name resolution of all backup servers | UDP | 53 | Port used for communication with the DNS Server. |
| Active Directory domain controller | TCP, UDP | 389 | Port used by Enterprise Manager service to communicate with Active Directory through the LDAP protocol. |
| TCP | 636 | Port used by the Enterprise Manager service to communicate with Active Directory through the LDAPS (LDAP over TLS/SSL) protocol. |
| TCP | 3268 | Port used by the Enterprise Manager service to communicate with LDAP Global Catalog. |
| TCP | 3269 | Port used by the Enterprise Manager service to communicate with LDAP Global Catalog through TLS/SSL. |
| TCP | 49152 to 65535 | Ports used by the Enterprise Manager service to communicate with Active Directory. These ports are also used during restore through Veeam Self-Service File Restore Portal. This is a default dynamic port range. For more information, see [Microsoft Support KB 832017](https://support.microsoft.com/en-us/help/832017/service-overview-and-network-port-requirements-for-windows#method1). |
| Veeam Update Repository | TCP | 443 | Port used by Veeam Software Appliance to connect to the Veeam Update Repository, a public Veeam-maintained repository that provides product, operating system, and security updates. For more information, see [How Updates Work](update_appliance_hiw.md). |
| Veeam Update Repository | TCP | 80 | Port used by Veeam Software Appliance to connect to a local mirror of the Veeam Update Repository. For more information, see [Configuring Updates](update_appliance_configure_updates.md). |
| Veeam License Update Server (vbr.butler.veeam.com, autolk.veeam.com) | TCP | 443 | Default port used to automatically update license from the Veeam License Update Server through HTTPS. |
| 80 | Required for certificate validation when Enterprise Manager connects to Veeam License Update Server to check if the new license is available and download it.  Certificate verification endpoints:   * \*.ss2.us * \*.amazontrust.com   Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. The actual list of addresses can be found in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Veeam Backup Enterprise Manager web application (Nginx) | Veeam Backup Enterprise Manager Service | TCP | 9394 | Default internal port used by Nginx to communicate with Veeam Backup Enterprise Manager through gRPC. |
| Browser | Veeam Backup Enterprise Manager web application (Nginx) | TCP | 443 | Default ports used to communicate with the Enterprise Manager website and Identity Service through HTTPS.  When you work with Veeam Self-Service Backup Portal (accessed by the portal URL or from the native VMware Cloud Director environment) and vSphere Self-Service Backup Portal, your browser also communicates with the Veeam Backup Enterprise Manager website through this port. |
| Veeam Backup Enterprise Manager REST API client and VMware vSphere Client plug-in | Veeam Backup Enterprise Manager REST API | TCP | 9398 | Default port used to communicate with Veeam Backup Enterprise Manager REST API through HTTPS. |
| Veeam ONE Server (optional) | Veeam Backup Enterprise Manager Service | TCP | 50001 | If you add the Enterprise Manager server to the Veeam ONE monitoring scope, this port is used for data collection through gRPC. |

Veeam Backup Enterprise Manager on Windows

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup Enterprise Manager | Linux-based backup server | TCP | 443 | Default port required for initial connection to a backup server and to its Identity Service.  This is also the default port used by the Veeam Guest Catalog service for catalog replication.  You can customize the port when you add a backup server. For more information, see [Adding Backup Servers](adding_backup_server.md). |
| 2500 to 2600 | Ports used by the Veeam Guest Catalog service for replicating catalog data. |
| Microsoft Windows-based backup server | TCP | 9405 | Default certificate port used by Enterprise Manager for collecting data from backup servers with version 12 installed. |
| 9392 | Default port required for initial connection to a backup server. |
| 443 | Default port used by the Veeam Guest Catalog service for catalog replication.  This is also the default certificate port used by Enterprise Manager for collecting data from backup servers with version 13 installed. |
| 2500 to 2600 | Ports used by the Veeam Guest Catalog service for replicating catalog data. |
| 49152 to 65535 | Dynamic RPC port range. For more information, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/929851/the-default-dynamic-port-range-for-tcp-ip-has-changed-in-windows-vista). |
| PostgreSQL hosting the Enterprise Manager configuration database | TCP | 5432 | Default port used for communication with PostgreSQL hosting the Enterprise Manager configuration database. |
| Microsoft SQL Server hosting the Enterprise Manager configuration database | TCP | 1433 | Default port used for communication with Microsoft SQL Server hosting the Enterprise Manager configuration database.  Additional ports may be needed depending on your configuration. For more information, see the Microsoft SQL Docs [Configure the Windows Firewall to Allow SQL Server Access](https://docs.microsoft.com/en-us/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access?view=sql-server-2014#BKMK_ssde) article. |
| VMware vCenter Server | TCP | 443 | Default port used for connection to a vCenter Server and deploying the Veeam Plug-in for vSphere Client. Can be customized during Enterprise Manager installation. For more information, see [Specify Service Ports](em_setup_port_configuration.md). |
| DNS server with forward/reverse name resolution of all backup servers | UDP | 53 | Port used for communication with your DNS Server. |
| Active Directory domain controller | TCP, UDP | 389 | Port used by the Enterprise Manager service to communicate with Active Directory through the LDAP protocol. |
| TCP | 636 | Port used by the Enterprise Manager service to communicate with Active Directory through the LDAPS (LDAP over TLS/SSL) protocol. |
| TCP | 3268 | Port used by the Enterprise Manager service to communicate with LDAP Global Catalog. |
| TCP | 3269 | Port used by the Enterprise Manager service to communicate with LDAP Global Catalog through TLS/SSL. |
| TCP | 49152 to 65535 | Ports used by the Enterprise Manager service to communicate with Active Directory. These ports are also used during restore through Veeam Self-Service File Restore Portal. This is a default dynamic port range. For more information, see [Microsoft Support KB 832017](https://support.microsoft.com/en-us/help/832017/service-overview-and-network-port-requirements-for-windows#method1). |
| Veeam License Update Server (vbr.butler.veeam.com, autolk.veeam.com) | TCP | 443 | Default port used to automatically update license from the Veeam License Update Server through HTTPS. |
| 80 | Required for certificate validation when Enterprise Manager connects to Veeam License Update Server to check if the new license is available and download it.  Certificate verification endpoints:   * \*.ss2.us * \*.amazontrust.com   Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. The actual list of addresses can be found in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Veeam Backup Enterprise Manager website (IIS extension) | Veeam Backup Enterprise Manager service | TCP | 9394 | Default port used by IIS extension to communicate with Veeam Backup Enterprise Manager. Can be customized during Veeam Backup Enterprise Manager installation. For more information, see [Specify Service Ports](em_setup_port_configuration.md). |
| Browser | Veeam Backup Enterprise Manager website (IIS extension) | TCP | 9080 | Default ports used to communicate with the website through HTTP. Can be customized during Veeam Backup Enterprise Manager installation. For more information, see [Specify Service Ports](em_setup_port_configuration.md).  When you work with Veeam Self-Service Backup Portal (accessed by the portal URL or from the native VMware Cloud Director environment) and vSphere Self-Service Backup Portal, your browser also communicates with the Veeam Backup Enterprise Manager website through this port. |
| TCP | 9443 | Default ports used to communicate with the website through HTTPS. Can be customized during Veeam Backup Enterprise Manager installation. For more information, see [Specify Service Ports](em_setup_port_configuration.md).  When you work with Veeam Self-Service Backup Portal (accessed by the portal URL or from the native VMware Cloud Director environment) and vSphere Self-Service Backup Portal, your browser also communicates with the Veeam Backup Enterprise Manager website through this port. |
| Veeam Backup Enterprise Manager REST API client and VMware vSphere Client plug-in | Veeam Backup Enterprise Manager REST API | TCP | 9399 | Default port used to communicate with Veeam Backup Enterprise Manager REST API through HTTP. Can be customized during Veeam Backup Enterprise Manager installation. For more information, see [Specify Service Ports](em_setup_port_configuration.md). |
| TCP | 9398 | Default port used to communicate with Veeam Backup Enterprise Manager REST API through HTTPS. Can be customized during Veeam Backup Enterprise Manager installation. For more information, see [Specify Service Ports](em_setup_port_configuration.md). |
| Veeam ONE Server (optional) | Veeam Backup Enterprise Manager server | TCP | Dynamically assigned ports | If you add the Enterprise Manager server to the Veeam ONE monitoring scope, this port is used for data collection through gRPC. |

|  |
| --- |
| Note |
| Consider the following:   * For communication between Enterprise Manager and backup servers, Kerberos authentication is used by default. * During installation, Enterprise Manager automatically creates firewall rules for default ports to allow communication for the application components. * For more information on Enterprise Manager network connectivity, refer to the [Enterprise Manager](http://bp.veeam.expert/networking/veeam_backup_enterprise_manager.html) article of the Veeam Backup and Replication Best Practices documentation. |

Data Recovery Operations

Guest OS File Restore (Windows)

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup Enterprise Manager server | Mount server associated with backup repository | TCP | 2500 to 6000 | Ports used for file download. |

Guest OS File Restore (non-Windows)

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup Enterprise Manager server | Mount server (helper host or helper appliance) | TCP | 2500 to 6000 | Ports used for file download. For more information on the mount server, see [Preparing for File Search and Restore (non-Windows machines)](em_preparing_for_linux_guest_file.md). |

|  |
| --- |
| Note |
| Consider the following:   * For more information on the list of ports used by the mount server associated with the backup repository during file-level restore, see the [Mount Server Connections](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13#mount) section of the Veeam Backup & Replication User Guide. * For more information on the list of ports used by the components involved in [1-Click Restore to Original Location](https://helpcenter.veeam.com/docs/vbr/userguide/full_recovery.html?ver=13), see the [Ports](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13) section of the Veeam Backup & Replication User Guide. |

Microsoft SQL Server Database Restore

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Machine running mount service1 | Target machine with Microsoft SQL Server | TCP, UDP | 135, 445 | Ports used to deploy the runtime coordination process on the target machine. |
| TCP | 49152 to 65535 (for Microsoft Windows Server 2008 or later) | Dynamic RPC range used by the runtime coordination process that is deployed on the target machine.  For more information, see [this Microsoft article](http://support.microsoft.com/kb/929851/en-us). |
| TCP | 6160 | Port used to communicate with Veeam Installer Service. |
| TCP | 1433, 1434 | Ports used to communicate with the Microsoft SQL Server installed on the target machine during application-item restore.  For more information, see [this Microsoft article](http://msdn.microsoft.com/en-us/library/cc646023.aspx#BKMK_ssde). |
| UDP | 1434 | Port used by the Microsoft SQL Server Browser service.  For more information, see [this Microsoft article](https://technet.microsoft.com/en-us/library/ms181087%28v%3Dsql.130%29.aspx). |
| TCP | 1025 to 1034 | Default RPC range for the Veeam SQL Restore Service runtime component installed on a target or staging Microsoft SQL Server machine to support restore. Each runtime component uses the next available port in the range, and only during application item restore.  For more information on the Veeam SQL Restore Service runtime component, see the [How Data Recovery Works](https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_service.html?ver=13) section of the Veeam Explorers User Guide.  You must manually open this port range in Microsoft Windows Firewall. |
| Target machine with Microsoft SQL Server | Machine running mount service1 | TCP | 3260 to 3270 | Port range opened by Veeam Backup & Replication to manage iSCSI traffic during restore to the target machine.  This port range is opened only during application item restore.  For more information, see the [How Mounting Works](https://helpcenter.veeam.com/docs/vbr/userguide/vesql_mount_operations.html?ver=13) section of the Veeam Explorers User Guide. |
| Backup repository | TCP | 2500 to 3300 | Port range used by the Veeam Agent persistent component deployed on the target or staging server.  This port range is only used during transaction log restore.  For more information on the components used during restore, see the [How Data Recovery Works](https://helpcenter.veeam.com/docs/vbr/userguide/vesql_restore_service.html?ver=13) section of the Veeam Explorers User Guide. |

1 Mount server associated with the repository (if restoring from backup), or a backup server (if restoring from replica).

Oracle Database Restore (1-Click)

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Target machine with Oracle | Machine running mount service1 | TCP | 3260 to 3270 | Ports used by Veeam Backup and Replication for iSCSI traffic. Ports are open only during the application item restore session. |

1 Mount server associated with the repository (if restoring from backup), or a backup server (if restoring from replica).

|  |
| --- |
| Note |
| For more information on 1-Click Database Restore to the original Oracle server machine (remote machine), see [1-Click Restore to Original Location](restore_oracle_1click_restore.md). |

Oracle Database Restore (Custom Settings)

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Machine running mount service1 | Target Windows machine with Oracle | TCP | 49152 to 65535 | Recommended dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft article](https://support.microsoft.com/en-us/kb/832017). |
| TCP | 1025 to 1034 | Default range of ports for the runtime component installed on the target or staging Oracle server to support restore operations. Each runtime component uses the next available port in the range, and only during application item restore.  You must manually open this port range in Microsoft Windows Firewall. |
| TCP | 6160, 11731 | Ports used by the Veeam Installer Service for connections to the target Windows machine with Oracle. |
| Target Linux machine with Oracle | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 5000 | Default port range for data transmission. |

1 Mount server associated with the repository (if restoring from backup), or a backup server (if restoring from replica).

|  |
| --- |
| Note |
| For more information on the process of database restore with custom settings, see [Restore with Custom Settings](restore_oracle_custom_settings.md). |

Page updated 12/22/2025

Page content applies to build 13.0.1.1071
