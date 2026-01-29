---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html"
last_updated: "1/28/2026"
product_version: "13.0.1.1071"
---

# Ports


On backup infrastructure components, Veeam Backup & Replication automatically creates firewall rules for the required ports on Windows-based machines. If you are using a third-party firewall, these rules must be created manually. These rules allow components to communicate with each other. You can find the full list of the ports in this section.

|  |
| --- |
| Important |
| Some Linux distributions also require firewall and security rules to be created manually. For details, see [this Veeam KB article](https://www.veeam.com/kb2986). |

If you use an HTTP/HTTPS proxy server to access the Internet, make sure that WinHTTP settings are properly configured on Microsoft Windows machines with Veeam backup infrastructure components. For information on how to configure WinHTTP settings, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/configure-proxy-internet).

|  |
| --- |
| Note |
| Tenants cannot access Veeam Cloud Connect infrastructure components through HTTP/HTTPS proxy servers. For information on supported protocols for Veeam Cloud Connect, see the [Ports](https://helpcenter.veeam.com/docs/vbr/cloud/ports.html?ver=13) section in the Veeam Cloud Connect Guide. |

Backup Server

The following tables describe network ports that must be opened to ensure proper communication of the backup server with backup infrastructure components:

* [Incoming Connections](#backup_server_in)
* [Outgoing Connections](#backup_server_out)

Incoming Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Management client PC (remote access) | Backup server | TCP | 22 | Default port used to connect to the Linux-based backup server through SSH. |
| TCP | 443 | Default ports used to connect to the Veeam Backup & Replication web UI. |
| Remote Veeam Backup & Replication console | TCP | 443 | Port used to communicate with the backup server. |
| Backup proxy | TCP | 2500 to 3300 | Default range of ports used for malware detection metadata transfer. |
| Backup repository (Linux) | TCP | 2500 to 3300 | Default range of ports used as transmission channels for copy backup operations if the backup server is used as the target backup repository. These ports are also required for file copy operations between the Linux backup repository and the backup server.  For every TCP connection that a job uses, one port from this range is assigned. |
| Tape server | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Mount server | TCP | 9401 | Port used for communication with the Veeam Backup Service.  Also required to perform Copy to and Mount to console operations during Windows file-level recovery. |
| TCP | 443 | Port used for communication with the backup server during file-level recovery. |
| REST client | TCP | 9419 | Default ports for communication with REST API service. |
| Management client PC (remote access) | TCP | 10443 | Default port used by the Linux-based backup server to connect to the Host Management console. |
| CDP components | TCP | 33034 | [CDP only] Port used by the following CDP components to communicate with Veeam CDP Coordinator Service:   * CDP proxy (source and target) * ESXi host (source and target) * vCenter Server (source and target)   For more information, see [Continuous Data Protection (CDP) for VMware vSphere](cdp_replication.md). |
| ESXi host | TCP | 33035 | [CDP only] Port used to install I/O filter components on the source and target ESXi hosts. For more information, see [Continuous Data Protection (CDP) for VMware vSphere](cdp_replication.md). |
| vCenter Server | TCP | 33035 | [CDP only] Port used to install I/O filter components on the source and target vCenter servers. For more information, see [Continuous Data Protection (CDP) for VMware vSphere](cdp_replication.md). |
| SCVMM | TCP | 443 | Port used for Veeam PowerShell Management Service authorization on the SCVMM server. |
| Management client PC (remote access) | TCP | 3389 | Default port used by Remote Desktop Services to connect to the Windows-based backup server. If you use third-party solutions to connect to the backup server, other ports may need to be open. |

Outgoing Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Communication with Virtualization Servers | | | | |
| Backup server | vCenter Server | TCP | 443 | Port used for connections to vCenter Server.  Note: The backup server should have a direct connection to vCenter Server. HTTP/HTTPS proxy servers are not supported.  If you use VMware Cloud Director, make sure you open port 443 on underlying vCenter Servers. |
| ESXi server | TCP | 443 | Port used for connections to ESXi host.  This port is not required for VMware Cloud on AWS. |
| TCP | 902 | Port used for data transfer to ESXi host. It is also used during guest OS file recovery if you recover files from replicas.  This port is not required for VMware Cloud on AWS. |
| VMware Cloud Director | TCP | 443 | Port used for connections to VMware Cloud Director.  Note: The backup server should have a direct connection to VMware Cloud Director. HTTP/HTTPS proxy servers are not supported. |
| SCVMM | TCP | 8732 | Port used to communicate with the VMM server. |
| TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Port used by Veeam Installer Service. |
| TCP | 6162 | Port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| Microsoft Hyper-V server | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6163 | Default port used to communicate with Veeam Hyper-V Integration Service. |
| TCP | 2179 | Port used to connect to VMs using the Virtual Machine Connection during [Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md) and [Recovery Verification for Microsoft Hyper-V](recovery_verification_overview_hv.md). |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for jobs and for collecting log files. For every TCP connection that a job uses, one port from this range is assigned. |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Communication with Configuration Databases | | | | |
| Backup server | PostgreSQL configuration database | TCP | 5432 | Port used for communication with PostgreSQL configuration database. Also required for the High Availability clusters. |
| Primary backup server with PostgreSQL configuration database | Standby backup server with PostgreSQL configuration database | TCP | 8008 | Port used by PostgreSQL database service to manage the High Availability clusters. |
| TCP | 8500 | Port used by PostgreSQL database service to manage the High Availability clusters. |
| Backup server | Microsoft SQL Server hosting the Veeam Backup & Replication configuration database | TCP | 1433 | Port used for communication with Microsoft SQL Server on which the Veeam Backup & Replication configuration database is deployed (if you use a Microsoft SQL Server default instance).  Additional ports may need to be open depending on your configuration. For more information, see [Microsoft Docs](https://msdn.microsoft.com/en-us/library/cc646023%28v%3Dsql.120%29.aspx#BKMK_ssde). |
| Communication with Mail Servers | | | | |
| Backup server | SMTP server | TCP | 25 | Port used by the SMTP server. |
| TCP | 587 | Port used by the SMTP server if SSL is enabled. |
| Gmail REST API  (gmail.googleapis.com) | TCP | 443 | Port used to communicate with Google Mail services. |
| Microsoft Graph REST API  (graph.microsoft.com, login.microsoftonline.com) | TCP | 443 | Port used to communicate with Microsoft Exchange Online organizations. |
| Other Communications | | | | |
| Backup server | Veeam Update Repository  (repository.veeam.com) | TCP | 443 | Port used by backup servers deployed from the Veeam Software Appliance ISO. It is used to connect to the Veeam Update Repository. The repository is Veeam-maintained and provides product, operating system, and security updates. For more information, see [How Updates Work](update_appliance_hiw.md). |
| Veeam Update Repository (local mirror)  (<localmirrorrepository.domain>) | TCP | 443 or 80 | Port used by backup servers deployed from the Veeam Software Appliance ISO. It is used to connect to a local mirror of the Veeam Update Repository. For more information, see [Configuring Updates](update_appliance_configure_updates.md).  Consider that the address must be replaced with the actual URL of your mirror repository. |
| Veeam License Update Server  (vbr.butler.veeam.com, autolk.veeam.com) | TCP | 443 | Default port used to automatically update license from the Veeam License Update Server over HTTPS. Veeam Threat Hunter and Veeam Data Cloud Vault also require this communication to work properly. |
| Veeam License Update Server  (\*.ss2.us, \*.amazontrust.com) | TCP | 80 | Port used for certificate validation when Veeam Backup & Replication connects to Veeam License Update Server to check if the new license is available and download it. Veeam Threat Hunter also requires this communication to work properly.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Certificate Revocation Lists | TCP | 80 or 443 | Port used for access to the Certificate Revocation Lists (CRL) of the Certificate Authority (CA) that issued the certificate for each backup infrastructure component.  Note: The specific CRL endpoint that must be connected to depends on the CA that issued the certificate.  You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| DNS server | UDP | 53 | Port used for communication with the DNS server. It is required for forward/reverse name resolution of all backup and infrastructure servers including Active Directory domain controllers. |
| KMS server | TCP | 5696 | Default port used for communication with the Key Management System server. |
| Syslog server | TCP, UDP | 514 | Default port used to communicate with the syslog server. |
| TLS | 6514 | Default port used to communicate with the syslog server over TLS. |
| Veeam ONE Server | TCP | 2741 | Default port used for communication with Veeam ONE internal Web API.  Required for the Analytics view. For more information, see [Configuring Analytics View](configure_analytics.md). |
| 2805 | Port used for communication between Veeam Analytics Service and Veeam ONE Monitoring service. This is required for Veeam ONE data collection. |
| Veeam ONE Web Services | TCP | 1239 | Default port used by Veeam ONE Web Services.  Required for the Analytics view. For more information, see [Configuring Analytics View](configure_analytics.md). |
| Microsoft SMB3 server (Hyper-V storage) | TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6163 | Default port used by the Hyper-V Integration Service. |
| Veeam Update Notification Server  (dev.veeam.com, vbrad.butler.veeam.com, vbrce.butler.veeam.com) | TCP | 443 | Default port used to download information about available updates from the Veeam Update Notification Server over HTTPS. |
| NTP server | UDP | 123 | Port used by backup servers deployed from the Veeam Software Appliance ISO for synchronization with NTP time servers. |
| NTS server | UDP | 123 | Ports used by backup servers deployed from the Veeam Software Appliance ISO for synchronization with NTS time servers. |
| TCP | 4460 |
| Active Directory Domain Controllers | TCP | 636, 3268, 3269 | Ports used for communications over LDAP and LDAPS protocols. |
| UDP, TCP | 389 |
| UDP, TCP | 445, 139 | Ports used for communications over SMB protocol. |
| UDP, TCP | 88 | Port used for Kerberos authentication. |

Backup & Replication Console

The following table describes network ports that must be opened to ensure proper communication with the Veeam Backup & Replication console.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication console | Mount server | TCP | 6162, 2500 to 3300 | [Remote console only] Ports used as data transmission channels for guest OS file-level restore. For every TCP connection that a job uses, one port from this range is assigned.  These ports are used if the mount server is not located on the console.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Veeam AI Assistant  (rest-ai.veeam.com) | TCP | 443 | Default port for communication with the Veeam AI Assistant service. |
| Backup server | TCP | 9420 | [For console version 12.3.2 P1 (build 12.3.2.4165)] Port used by the Veeam Backup & Replication console to communicate with the backup server for console automatic update. |

Veeam Infrastructure Appliance

The following table describes network ports that must be opened to ensure proper communication between Veeam Infrastructure Appliances and other backup components. You must open additional ports based on the role you have assigned to the Veeam Infrastructure Appliance. For more information, see the relevant section for the role on this page.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Infrastructure Appliance | Veeam Update Repository  (repository.veeam.com) | TCP | 443 | Port used by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO. It is used to connect to the Veeam Update Repository. The repository is Veeam-maintained and provides product, operating system, and security updates. For more information, see [How Updates Work](update_appliance_hiw.md). |
| Veeam Update Repository (local mirror)  (<localmirrorrepository.domain>) | TCP | 443 or 80 | Port used by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO. It is used to connect to a local mirror of the Veeam Update Repository. For more information, see [Configuring Updates](update_appliance_configure_updates.md).  Consider that the address must be replaced with the actual URL of your mirror repository. |
| Backup server | TCP | 443 | Port used by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO to authenticate incoming connections from Veeam Backup & Replication. |
| NTP server | UDP | 123 | Port used by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO for synchronization with NTP time servers. |
| NTS server | UDP | 123 | Port used by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO for synchronization with NTS time servers. |
| TCP | 4460 |
| DNS server | UDP | 53 | Port used for communication with the DNS server. It is required for forward/reverse name resolution of all backup and infrastructure servers including Active Directory domain controllers. |
| Active Directory Domain Controllers | TCP | 636, 3268, 3269 | Ports used for communications over LDAP and LDAPS protocols. |
| UDP, TCP | 389 |
| UDP, TCP | 445, 139 | Ports used for communications over SMB protocol. |
| UDP, TCP | 88 | Port used for Kerberos authentication. |
| Backup server | Veeam Infrastructure Appliance | TCP | 443 | Port used by Veeam Backup & Replication to synchronize Veeam Updater settings on backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO. |
| Management client PC (remote access) | TCP | 10443 | Port used by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO. Required to connect to the Host Management console. |

Backup Proxy

The following table describes network ports that must be opened to ensure proper communication of backup proxies with other backup components. For more information about ports that must be opened between the backup proxy and specific backup repository, see [Backup Repositories](#backup_repos).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Communication with Backup Server | | | | |
| Backup server | Backup proxy (Microsoft Windows) | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| Backup proxy (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 6160 | Default port used by Veeam Installer Service for Linux. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  You can specify a different port while adding the Linux server to the Veeam Backup & Replication infrastructure. Note that you can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on this Linux server. For more information, see [Specify Credentials and SSH Settings](linux_server_ssh.md). |
| Backup proxy | TCP | 2500 to 3300 | Default range of ports used as data transmission channels and for collecting log files. For every TCP connection that a job uses, one port from this range is assigned. |
| TCP | 6210 | Default port used by the Veeam Backup VSS Integration Service for taking a VSS snapshot during the SMB file share backup. |
| Communication with Virtualization Servers | | | | |
| Backup proxy | vCenter Server | TCP | 443 | Default VMware web service port that can be customized in vCenter settings. |
| ESXi server | TCP | 902 | Default VMware port used for data transfer.  This port is not required for VMware Cloud on AWS. |
| TCP | 443 | Default VMware web service port that can be customized in ESXi host settings. Not required if vCenter connection is used.  This port is not required for VMware Cloud on AWS. |
| Other Communications | | | | |
| Backup proxy | Gateway server | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Backup proxy | TCP | 2500 to 3300 | Default range of ports used as transmission channels for replication jobs. For every TCP connection that a job uses, one port from this range is assigned. |
| Backup repository | TCP | 6162 | Port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |

Off-Host Backup Proxy

The following table describes network ports that must be opened to ensure proper communication of off-host backup proxies with other backup components. For more information about ports that must be opened between the off-host backup proxy and specific backup repository, see [Backup Repositories](#backup_repos).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Communication with Backup Server | | | | |
| Backup server | Hyper-V server/Off-host backup proxy | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6163 | Default port used by the Hyper-V Integration Service. |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Off-host file proxy | TCP | 6210 | Default port used by the Veeam Backup VSS Integration Service for taking a VSS snapshot during the SMB file share backup. |
| Other Communications | | | | |
| Hyper-V server/Off-host backup proxy | Gateway server | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Hyper-V server | TCP | 2500 to 3300 | Default range of ports used as transmission channels for replication jobs. For every TCP connection that a job uses, one port from this range is assigned. |
| Microsoft SMB3 server | Hyper-V server/Off-host backup proxy | TCP | 2500 to 3300 | Ports used to retrieve CBT information from a Microsoft SMB3 server managing shares that host VM disks. |

Gateway Server

The following table describes network ports that must be opened to ensure proper communication with gateway servers. For more information about ports that must be opened between the gateway server and specific backup repository, see [Backup Repositories](#backup_repos).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Gateway server (Microsoft Windows) | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6190 | Port used for communication with the guest interaction proxy. |
| Gateway server (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 6160 | Default port used by Veeam Installer Service for Linux. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  You can specify a different port while adding the Linux server to the Veeam Backup & Replication infrastructure. Note that you can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on this Linux server. For more information, see [Specify Credentials and SSH Settings](linux_server_ssh.md). |
| TCP | 6190 | Port used for communication with the guest interaction proxy. |
| Backup proxy or Hyper-V server/Off-host backup proxy | Gateway server | TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| Guest interaction proxy | TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| Log shipping server | TCP | 2500 to 3300 | Default range of ports used as transmission channels and for log file collection. For every TCP connection that a job uses, one port from this range is assigned. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| VM Guest OS | TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 2500-3300 | Default range of ports used as transmission channels and for log file collection. For every TCP connection that a job uses, one port from this range is assigned. |

Backup Repositories

* [Microsoft Windows/Linux-Based Backup Repository](#repo)
* [NFS Backup Repository](#nfs_repository)
* [SMB Backup Repository](#smb_repository)

* [Dell Data Domain System](#emc)
* [ExaGrid](#exagrid)
* [HPE StoreOnce](#storeonce)
* [Quantum DXi](#quantum)
* [Fujitsu ETERNUS CS800](#fujitsu_eternus)
* [Infinidat InfiniGuard](#infinidat_infiniguard)
* [Veeam Data Cloud Vault](#VDCvault)
* [Object Storage Repository](#osrc)
* [External Repository](#external_repo)
* [Archive Object Storage Repository](#archive_tier)

Microsoft Windows/Linux-Based Backup Repository

The following table describes network ports that must be opened to ensure proper communication with Microsoft Windows/Linux-based backup repositories.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Backup repository (Microsoft Windows) | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| Backup repository (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 6160 | Default port used by Veeam Installer Service for Linux. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  You can specify a different port while adding the Linux server to the Veeam Backup & Replication infrastructure. Note that you can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on this Linux server. For more information, see [Specify Credentials and SSH Settings](linux_server_ssh.md). |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels and for collecting log files. For every TCP connection that a job uses, one port from this range is assigned. |
| Backup proxy or Hyper-V server/Off-host backup proxy | Backup repository | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Source backup repository | Target backup repository | TCP | 2500 to 3300 | Default range of ports used as transmission channels for backup copy jobs and copy backup operations. For every TCP connection that a job uses, one port from this range is assigned.  If the backup copy job utilizes WAN accelerators, make sure that [ports specific for WAN accelerators](used_ports.md#wan) are opened. |

NFS Backup Repository

The following table describes network ports that must be opened to ensure proper communication with NFS shares added as backup repositories.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Gateway server or backup proxy | NFS backup repository | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service.  Also used as a transmission channel from the gateway server to the target NFS backup repository if a gateway server is specified explicitly in NFS backup repository settings. |
| Gateway server or backup proxy | NFS backup repository | TCP, UDP | mountd\_port | Dynamic port used for mountd service. Can be assigned statically. |
| TCP, UDP | statd\_port | Dynamic port used for statd service. Can be assigned statically. |
| TCP, UDP | lockd\_port | Dynamic port used for lockd service. Can be assigned statically. |

SMB Backup Repository

The following table describes network ports that must be opened to ensure proper communication with SMB (CIFS) shares added as backup repositories.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Gateway server or backup proxy | SMB (CIFS) backup repository (Microsoft Windows) | TCP | 445 | Port used as a transmission channel from the gateway server to the target SMB (CIFS) backup repository if a gateway server is specified explicitly in SMB (CIFS) backup repository settings. |
| Active Directory Domain Controllers | TCP | 389 | Port used for communications over LDAP and LDAPS protocols. |
| TCP | 88 | Port used for Kerberos authentication. |

Dell Data Domain System

For more information, see [Dell Documents](https://www.dell.com/support/kbdoc/en-us/000126375/powerprotect-and-data-domain-core-documents).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server or gateway server | Dell Data Domain | TCP | 111 | Port used to assign a random port for the mountd service used by NFS and DDBOOST. Mountd service port can be statically assigned. |
| TCP | 2049 | Main port used by NFS. Can be modified using the ‘nfs set server-port’ command. Command requires SE mode. |
| TCP | 2052 | Main port used by NFS MOUNTD. Can be modified using the 'nfs set mountd-port' command in SE mode. |

ExaGrid

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | ExaGrid | TCP | 22 | Default command port used for communication with ExaGrid and initial installation of Veeam components. |
| TCP | 6160 | Default port used by Veeam Installer Service for components management and upgrade. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Backup proxy | ExaGrid | TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |

HPE StoreOnce

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server or gateway server | HPE StoreOnce | TCP | 9387 | Default command port used for communication with HPE StoreOnce. |
| TCP | 9388 | Default data port used for communication with HPE StoreOnce. |

Quantum DXi

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Quantum DXi | TCP | 22 | Default command port used for communication with Quantum DXi and initial installation of Veeam components. |
| TCP | 6160 | Default port used by Veeam Installer Service for components management and upgrade. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Backup proxy | Quantum DXi | TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |

Fujitsu ETERNUS CS800

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Fujitsu ETERNUS CS800 | TCP | 22 | Default command port used for communication with Fujitsu ETERNUS CS800 and initial installation of Veeam components. |
| TCP | 6160 | Default port used by Veeam Installer Service for components management and upgrade. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Backup proxy | Fujitsu ETERNUS CS800 | TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |

Infinidat InfiniGuard

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Infinidat InfiniGuard | TCP | 22 | Default command port used for communication with Infinidat InfiniGuard and initial installation of Veeam components. |
| TCP | 6160 | Default port used by Veeam Installer Service for components management and upgrade. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Backup proxy | Infinidat InfiniGuard | TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |

Veeam Data Cloud Vault

The following table describes network ports and endpoints that must be opened to ensure proper communication with Veeam Data Cloud Vault. Note that a connection between the backup server and Veeam License Update Server is also required. For more information, see [Backup Server](#backup).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Veeam Data Cloud Vault  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used to communicate with the Microsoft Azure object storage.  Consider that the <storage-account> part of the address must be replaced with the ID of your storage vault. You can find the storage vault ID in the Storage Vaults > Vault ID section in Veeam Data Cloud Vault. For more information, see the [Managing Storage Vaults](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#viewing-storage-vault-details) section in the Veeam Data Cloud User Guide. |
| Veeam Data Cloud Vault | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Microsoft Entra ID  (login.microsoftonline.com, login.windows.net) | TCP | 443 | Port used for Entra ID authentication. |
| Backup proxy (direct connection)/Gateway server/Instant Recovery to Azure helper appliance | Veeam Data Cloud Vault  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used to communicate with the Microsoft Azure object storage.  Consider that the <storage-account> part of the address must be replaced with the ID of your storage vault. You can find the storage vault ID in the Storage Vaults > Vault ID section in Veeam Data Cloud Vault. For more information, see the [Managing Storage Vaults](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#viewing-storage-vault-details) section in the Veeam Data Cloud User Guide. |
| Veeam Data Cloud Vault | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| On-premises backup repository/ Gateway server for on-premises backup repository | Backup proxy (direct connection)/ Gateway server for Veeam Data Cloud Vault | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |

Object Storage Repository

The following table describes network ports and endpoints that must be opened to ensure proper communication with object storage repositories. For more information, see [Object Storage Repository](object_storage_repository.md).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Gateway server | Backup proxy (direct connection)/Gateway server or backup server | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Backup server | Smart Object Storage API (SOSAPI) compatible S3 object storage | TCP | 443 | Port used by Veeam Backup & Replication for auxiliary communications with object storage repositories that support Smart Object Storage API (SOSAPI). |
| Backup proxy (direct connection)/Gateway server or backup server/Instant Recovery to Azure helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with the Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Amazon S3 object storage  (\*.amazontrust.com) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | Port used to communicate with the Microsoft Azure object storage.  The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Microsoft Azure object storage | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Google Cloud storage  (storage.googleapis.com) | TCP | 443 | Port used to communicate with Google Cloud storage.  All cloud endpoints are specified in [this Google article](https://cloud.google.com/storage/docs/request-endpoints). |
| Google Cloud storage  (ocsp.pki.goog, pki.goog, crl.pki.goog) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| IBM Cloud object storage | TCP | Depends on device configuration | Port used to communicate with IBM Cloud object storage. |
| S3 compatible object storage | TCP | Depends on device configuration | Port used to communicate with S3 compatible object storage. |

External Repository

The following table describes network ports and endpoints that must be opened to ensure proper communication with external repositories. For more information, see [External Repository](external_repository.md).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Gateway server | Backup proxy (direct connection)/Gateway server or backup server | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Gateway server/backup server/Instant Recovery to Azure helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Amazon S3 object storage  (\*.amazontrust.com) | TCP | 80 | Port used to verify certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | Port used to communicate with Microsoft Azure object storage.  The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Microsoft Azure object storage | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Google Cloud storage  (storage.googleapis.com) | TCP | 443 | Port used to communicate with Google Cloud storage.  All cloud endpoints are specified in [this Google article](https://cloud.google.com/storage/docs/request-endpoints). |
| Google Cloud storage  (ocsp.pki.goog, pki.goog, crl.pki.goog) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |

Archive Object Storage Repository

The following table describes network ports and endpoints that must be opened to ensure proper communication with object storage repositories used as a part of Archive Tier. For more information, see [Archive Tier](archive_tier.md).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Gateway server or backup server | Amazon EC2 helper appliance | TCP | 443 | Port used by default to communicate with the Amazon EC2 helper appliance through public/private IPv4 addresses of EC2 appliances.  If you use Amazon S3 Glacier object storage, the gateway server should have direct connection to AWS service endpoints. HTTP/HTTPS proxy servers are not supported.  If there is no gateway server selected, the backup server will be used as a gateway server. |
| TCP | 22 | Default SSH port used as a control channel. |
| Microsoft Azure proxy appliance | TCP | 443 | Port used by default to communicate with the Microsoft Azure helper appliance through public/private IPv4 addresses of Azure appliances.  If there is no gateway server selected, the backup server will be used as a gateway server. |
| TCP | 22 | Default SSH port used as a control channel. |
| Amazon EC2 helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with the Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Amazon S3 object storage  (\*.amazontrust.com) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Microsoft Azure proxy appliance | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | Port used to communicate with the Microsoft Azure object storage.  The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Microsoft Azure object storage | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |

Storage Systems

* [Dell Unity XT, Unity Storage](#dell_unity)

* [Dell PowerScale (formerly Isilon) Storage](#dell_isilon)

* [HPE 3PAR StoreServ Storage](#3par)
* [HPE Alletra Storage MP B10000, Alletra 9000, Primera Storage](#hpe_primera)
* [HPE Alletra 5000, Alletra 6000, Nimble Storage](#nimble)
* [Lenovo ThinkSystem DM/DG Series Storage](#lenovo_thinksystem)
* [NetApp ONTAP Storage](#netapp)
* [Nutanix Files Storage](#nutanix_files_storage)
* [Universal Storage API Integrated System](#usais)

Dell Unity XT, Unity Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell Unity XT/Unity storage system | TCP | 443 | Default port used for communication with Dell Unity XT/Unity over HTTPS and sending REST API calls. |
| Backup proxy | Dell Unity XT/Unity storage system | TCP | 3260 | Default iSCSI target port. |
| TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |

Dell PowerScale (Formerly Isilon) Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell PowerScale storage system | TCP | 8080 | Default port used for communication with Dell PowerScale over HTTPS and sending REST API calls. |
| Backup proxy | Dell PowerScale storage system | TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |

HPE 3PAR StoreServ Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | HPE 3PAR StoreServ storage system | TCP | 8008 | Default port used for communication with HPE 3PAR StoreServ over HTTP. |
| TCP | 8080 | Default port used for communication with HPE 3PAR StoreServ over HTTPS. |
| TCP | 22 | Default command port used for communication with HPE 3PAR StoreServ over SSH. |
| Backup proxy | HPE 3PAR StoreServ storage system | TCP | 3260 | Default iSCSI target port. |

HPE Alletra Storage MP B10000, Alletra 9000, Primera Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | HPE Alletra Storage MP B10000/Alletra 9000/Primera storage system | TCP | 443 | Default port used for communication with HPE Alletra Storage MP B10000/Alletra 9000/Primera over HTTPS. |
| TCP | 22 | Default command port used for communication with HPE Alletra Storage MP B10000/Alletra 9000/Primera over SSH. |
| Backup proxy | HPE Alletra Storage MP B10000/Alletra 9000/Primera storage system | TCP | 3260 | Default iSCSI target port. |
| HPE Alletra Storage MP B10000/Alletra 9000 | TCP | 4420, 8009 | Default NVMe-oF ports. |

HPE Alletra 5000, Alletra 6000, Nimble Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | HPE Alletra 5000/Alletra 6000/Nimble storage system | TCP | 5392 | Default command port used for communication with HPE Alletra 5000/Alletra 6000/Nimble. |
| Backup proxy | HPE Alletra 5000/Alletra 6000/Nimble storage system | TCP | 3260 | Default iSCSI target port. |

Lenovo ThinkSystem DM/DG Series Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Lenovo ThinkSystem DM/DG Series storage system | TCP | 80 | Default command port used for communication with Lenovo ThinkSystem DM/DG Series over HTTP. |
| TCP | 443 | Default command port used for communication with Lenovo ThinkSystem DM/DG Series over HTTPS. |
| Backup proxy | Lenovo ThinkSystem DM/DG Series storage system | TCP, UDP | 111, 2049, 635 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |
| TCP | 3260 | Default iSCSI target port. |

NetApp ONTAP Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | NetApp ONTAP storage system | TCP | 80 | Default command port used for communication with NetApp ONTAP over HTTP. |
| TCP | 443 | Default command port used for communication with NetApp ONTAP over HTTPS. |
| Backup proxy | NetApp ONTAP storage system | TCP, UDP | 111, 2049, 635 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |
| TCP | 3260 | Default iSCSI target port. |

Nutanix Files Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Nutanix Files storage system | TCP | 9440 | Default port used for communication with Nutanix Files and sending REST API calls. |
| Backup proxy | Nutanix Files storage system | TCP, UDP | 111, 2049, 20048 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |

Universal Storage API Integrated System

The following tables describe network ports that must be opened to ensure proper communication with Universal Storage API integrated systems:

* [DataCore SANsymphony](#DataCore)
* [Dell SC Series](#DellEMC)
* [Dell PowerMax](#dell_powermax)
* [Dell PowerStore](#dell_powerstore)
* [Fujitsu ETERNUS DX/AF](#fujitsu)

* [Hitachi VSP/VSP One Block](#vsp)
* [IBM FlashSystem (formerly Spectrum Virtualize) Storage](#ibm)

* [INFINIDAT InfiniBox](#infinidat)

* [NEC Storage M Series](#necm)
* [NetApp SolidFire/HCI](#solidfire)
* [Pure Storage FlashArray](#pure)
* [Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)](#WesternDigital)

DataCore SANsymphony

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | DataCore SANsymphony storage system | TCP | 443 | Default command port used for communication with DataCore SANsymphony over HTTPS. |
| Backup proxy | DataCore SANsymphony storage system | TCP | 3260 | Default iSCSI target port. |

Dell SC Series

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell SC Series storage system | TCP | 3033 | Default command port used for communication with Dell SC Series over HTTPS. |
| Backup proxy | Dell SC Series storage system | TCP | 3260 | Default iSCSI target port. |

Dell PowerMax

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell PowerMax storage system | TCP | 8443 | Default command port used for communication with Dell PowerMax over HTTPS. |
| Backup proxy | Dell PowerMax storage system | TCP | 3260 | Default iSCSI target port. |

Dell PowerStore

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Dell PowerStore storage system | TCP | 443 | Default command port used for communication with Dell PowerStore over HTTPS. |
| Backup proxy | Dell PowerStore storage system | TCP | 3260 | Default iSCSI target port. |

Fujitsu ETERNUS DX/AF

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Fujitsu ETERNUS DX/AF storage system | TCP | 22 | Default command port used for communication with Fujitsu ETERNUS DX/AF over SSH. |
| Backup proxy | Fujitsu ETERNUS DX/AF storage system | TCP | 3260 | Default iSCSI target port. |

Hitachi VSP/VSP One Block

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Hitachi VSP/VSP One Block storage system | TCP | 443 | Default command port used for communication with Hitachi VSP/VSP One Block over HTTPS. |
| Backup proxy | Hitachi VSP/VSP One Block storage system | TCP | 3260 | Default iSCSI target port. |

IBM FlashSystem (formerly Spectrum Virtualize) Storage

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | IBM FlashSystem storage system | TCP | 22 | Default command port used for communication with IBM FlashSystem over SSH. |
| Backup proxy | IBM FlashSystem storage system | TCP | 3260 | Default iSCSI target port. |

INFINIDAT InfiniBox

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | INFINIDAT InfiniBox storage system | TCP | 443 | Default command port used for communication with INFINIDAT InfiniBox over HTTPS. |
| Backup proxy | INFINIDAT InfiniBox storage system | TCP | 3260 | Default iSCSI target port. |

NEC Storage M Series

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | NEC Storage M Series storage system | TCP | 22 | Default command port used for communication with NEC Storage M Series over SSH. |
| Backup proxy | NEC Storage M Series storage system | TCP | 3260 | Default iSCSI target port. |

NetApp SolidFire/HCI

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | NetApp SolidFire/HCI storage system | TCP | 443 | Default command port used for communication with NetApp SolidFire/HCI over HTTPS. |
| Backup proxy | NetApp SolidFire/HCI storage system | TCP | 3260 | Default iSCSI target port. |

Pure Storage FlashArray

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Pure Storage FlashArray system | TCP | 443 | Default command port used for communication with Pure Storage FlashArray over HTTPS. |
| Backup proxy | Pure Storage FlashArray system | TCP | 3260 | Default iSCSI target port. |
| Pure Storage FlashArray system | TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |

Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Tintri IntelliFlash system | TCP | 443 | Default command port used for communication with Tintri IntelliFlash over HTTPS. |
| Backup proxy | Tintri IntelliFlash system | TCP | 3260 | Default iSCSI target port. |
| Tintri IntelliFlash system | TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |

Unstructured Data Backup Components

The following tables describe network ports that must be opened to ensure proper communication between unstructured data backup components.

* [File Share Connections](#nas_shares_connections)
* [Cache Repository Connections](#cache_repository_connections)
* [Archive Repository Connections](#archive_repository_connections)
* [NDMP Server Connections](#ndmp)

File Share Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| File server (Windows or Linux), Backup proxy | Backup server | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Backup server | File server (Windows or Linux), Backup proxy | TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6210 | Default port used by the Veeam Backup VSS Integration Service for taking a VSS snapshot during the SMB file share backup (if Veeam Backup & Replication is installed on the Microsoft Windows machine). For more information, see [Microsoft Windows Services](services_and_components.md#win_services). |
| TCP | 6162 | Default port used by Veeam Transport Service. |
| Backup proxy | NAS filer (NetApp Data ONTAP or Lenovo ThinkSystem DM/DG Series storage system) | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Standard SMB port. |
| TCP, UDP | 635 | The default port used by the NetApp Data ONTAP storage controller. |
| TCP | 80, 443 | Ports used by NetApp SnapDiff when changed file tracking (CFT) is enabled. |
| NAS filer (Dell PowerScale (formerly Isilon) or Nutanix Files storage system) | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Standard SMB port. |
| TCP | 20048 | Port used for the NFS mountd access and service request monitoring. |
| Active Directory Domain Controllers | TCP | 389 | Port used for communications over LDAP and LDAPS protocols. |
| TCP | 88 | Port used for Kerberos authentication. |
| File server (Windows or Linux), backup proxy or tape server | NFS share | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service. |
| SMB share | TCP | 445 | Standard SMB port. |
| Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Amazon S3 object storage  (\*.amazontrust.com) | TCP | 80 | Port used to verify certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | Port used to communicate with Microsoft Azure object storage.  The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Microsoft Azure object storage | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| S3 compatible object storage | TCP | Depends on device configuration | Port used to communicate with S3 compatible object storage. |
| Active Directory Domain Controllers | TCP | 389 | Port used for communications over LDAP and LDAPS protocols. |
| TCP | 88 | Port used for Kerberos authentication. |
| Mount server | SMB share | TCP | 137-139, 443, 445, 6170 | Ports used during Instant File Share Recovery. |

Cache Repository Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| File server (Windows or Linux), Backup proxy | Cache repository | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| TCP | 6160 | Default ports used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service. |
| Backup server | Old cache repository, new cache repository | TCP | 2500 to 3300, 6160, 6162 | Default range of ports used for metadata migration during cache repository change. For more information, see [Changing Cache Repository](unstructured_data_backup_in_object_storage.md#change_cache_repo). |
| Cache repository | File server (Windows or Linux), Backup proxy | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| Primary or secondary backup repository | TCP | 2500 to 3300 | Default range of ports used as transmission channels for file share backup restore jobs. For every TCP connection that a job uses, one port from this range is assigned. |

Archive Repository Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Primary backup repository | Archive repository | TCP | 2500 to 3300 | Default range of ports used as transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |

NDMP Server Connections

The following table describes network ports that must be opened to ensure proper communication with NDMP servers.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Gateway server | NDMP server | NDMP | 10000 | Default port used to manage the NMDP server.  Note: The port range used for data transfer depends on your NDMP server configuration. For more information, contact your hardware vendor. |

Tape Server

The following table describes network ports that must be opened to ensure proper communication with tape servers.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Tape server | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 2500 to 3300 | Default range of ports used as data transmission channels and for collecting log files. For every TCP connection that a job uses, one port from this range is assigned. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6166 | Controlling port for RPC calls. |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Tape server | Backup repository or gateway server | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is assigned. |
| NFS share | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service. |
| SMB share | TCP | 445 | Standard SMB port. |

WAN Accelerator

The following table describes network ports that must be opened to ensure proper communication between WAN accelerators used in backup copy jobs and replication jobs.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | WAN accelerator | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6164 | Controlling port for RPC calls. |
| WAN accelerator (target) | Backup repository (target) | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is selected dynamically. |
| WAN accelerator (source) | Backup repository (source) | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is selected dynamically. |
| WAN accelerator (source and target) | WAN accelerator (source and target) | TCP | 6164 | Controlling port for RPC calls. |
| TCP | 6165 | Default port used for data transfer between WAN accelerators. Ensure this port is open in firewall between sites where WAN accelerators are deployed. |
| Backup server | WAN accelerator  (target) | TCP | 6220 | Port used for traffic control (throttling) for tenants that use WAN accelerators.  This port is required only in the Veeam Cloud Connect infrastructure. |

Guest Processing Components

The following table describes the network ports that must be opened to ensure proper communication between the backup server and the VMs that will be added to Managed Servers as Guest Interaction Proxy (Log Shipping Server).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Guest interaction proxy | TCP | 445, 135 | Ports used for adding Windows VMs to managed servers using local administrator credentials. Note: Kerberos domain account with administrator privileges should be used. |
| TCP | 6160 | Port used for adding both Windows and Linux VMs to managed servers using a certificate-based authentication. Note: Deployment kit should be pre-installed on VMs. |
| TCP | 22 | Port used for adding Linux VMs to managed servers using SSH credentials. |

Connections with Non-Persistent Runtime Components

The following tables describe network ports that must be opened to ensure proper communication of the backup server and backup infrastructure components with the non-persistent runtime components deployed inside the VM guest OS for application-aware processing and indexing.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Guest interaction proxy | TCP | 6190 | Port used for communication with the guest interaction proxy. |
| Guest interaction proxy | ESXi server | TCP | 443 | Default port used for connections to ESXi host.  [For VMware vSphere earlier than 6.5] Not required if vCenter connection is used. In VMware vSphere versions 6.5 and later, port 443 is required by vCenter Web Services. |

Network ports described in the following table are NOT required in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | VM guest OS (Microsoft Windows) | TCP | 445, 135 | Port used to deploy the runtime coordination process on the VM guest OS. |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. |
| TCP | 6173 | Port used by the runtime process deployed inside the VM for guest OS interaction. |
| VM guest OS (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. |

Connections with Persistent Agent Components

The following table describes network ports that must be opened to ensure proper communication of the backup server with the persistent agent components deployed inside the VM guest OS for application-aware processing and indexing.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | VM guest OS (Linux) | TCP | 6160 | Default port used by Veeam Installer Service for Linux. |
| TCP | 6162 | Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| VM guest OS (Windows) | TCP | 6160, 11731 | Default port and failover port used by Veeam Installer Service. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing and file system indexing. |

Log Shipping Components

The following tables describe network ports that must be opened to ensure proper communication between log shipping components.

* [Log Shipping Server Connections](#log_shipping_server_connections)
* [MS SQL Guest OS Connections](#sql_guest_os_connections)
* [Oracle Guest OS Connections](#oracle_guest_os_connections)
* [PostgreSQL Guest OS Connections](#postgresql_guest_os_connections)

Log Shipping Server Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Log shipping server | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| Hyper-V host | Log shipping server (backup server) | TCP | 6162 or 2500 to 3300 | Port or range of ports used for communication with the Hyper-V host and for transfer log backups.  These ports are required only if the log shipping server transfers data over PowerShell Direct. In this case, the backup server performs the role of the log shipping server.  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Log shipping server | Backup repository or gateway server | TCP | 6162 or 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Log shipping server (backup server) | Hyper-V host | TCP | 6162 or 2500 to 3300 | Port or range of ports used for communication with the Hyper-V host and for transfer log backups.  These ports are required only if the log shipping server transfers data over PowerShell Direct. In this case, the backup server performs the role of the log shipping server.  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Log shipping server | ESXi host | TCP | 443 | Default port used for communication with a log shipping server and transfer log backups over vSphere API. |

MS SQL Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | MS SQL VM guest OS | TCP | 445, 135, 137, 139 | [Non-persistent runtime components only] Ports used for deploying Veeam Backup & Replication components including Veeam Log Shipper runtime component.  These ports are not required:   * When working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. * If the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.   Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing. |
| TCP | 6160, 11731 | [Persistent agent components only] Default port and failover port used by Veeam Installer Service. |
| TCP | 6167 | Port used by the Veeam Log Shipping Service for preparing the database and taking logs. |
| MS SQL VM guest OS | Backup repository | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the MS SQL server has a direct connection to the backup repository. |
| MS SQL VM guest OS | Log shipping server | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a log shipping server and transfer log backups. |

Oracle Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | Oracle VM guest OS (Microsoft Windows) | TCP | 445, 135 | [Non-persistent runtime components only] Ports used for deploying Veeam Backup & Replication components including Veeam Log Shipper runtime component.  These ports are not required:   * When working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. * If the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.   Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing |
| TCP | 6160, 11731 | [Persistent agent components only] Default port and failover port used by Veeam Installer Service. |
| TCP | 6167 | Port used by the Veeam Log Shipping Service for preparing the database and taking logs. |
| Oracle VM guest OS (Linux) | TCP | 22 | [Non-persistent runtime components only] Default SSH port used as a control channel.  This port is NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6162 | [Persistent agent components only] Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| Oracle VM guest OS | Backup repository | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the Oracle server has a direct connection to the backup repository. |
| Oracle VM guest OS | Log shipping server | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a log shipping server and transfer log backups. |

PostgreSQL Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Guest interaction proxy | PostgreSQL VM guest OS | TCP | 22 | [Non-persistent runtime components only] Default SSH port used as a control channel.  This port is NOT required when working in networkless mode over vSphere Web Services. |
| TCP | 6162 | [Persistent agent components only] Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  This port is NOT required when working in networkless mode over vSphere Web Services. |
| PostgreSQL VM guest OS | Backup repository | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the PostgreSQL server has a direct connection to the backup repository. |
| PostgreSQL VM guest OS | Log shipping server | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a log shipping server and transfer log backups. |

CDP Components

The following table describes network ports that must be opened to ensure proper communication of Veeam CDP components with other backup components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| ESXi host (source) | CDP proxy (source) | TCP | 33032 | Default port used as a transmission channel to the source CDP proxy. |
| ESXi host (source) | TCP | 33036 | Port used on the source ESXi host for communication between CDP components over HTTPS without HTTP Reverse Proxy. |
| CDP proxy (source) | CDP proxy (target) | TCP | 33033 | Default port used as a transmission channel to the target CDP proxy. |
| ESXi host (source and target) | TCP | 902 | Default VMware port used for data transfer. Used during initial synchronization and restore operations. |
| vCenter Server (source and target) | TCP | 443 | Default VMware web service port that can be customized in vCenter settings. Used during initial synchronization and restore operations. |
| CDP proxy (target) | ESXi host (target) | TCP | 33032 | Default port used as a transmission channel to the target ESXi host. |
| ESXi host (source and target) | TCP | 902 | Default VMware port used for data transfer. Used during initial synchronization and restore operations. |
| vCenter Server (source and target) | TCP | 443 | Default VMware web service port that can be customized in vCenter settings. Used during initial synchronization and restore operations. |
| ESXi host (target) | ESXi host (target) | TCP | 33036 | Port used on the target ESXi host for communication between CDP components over HTTPS without HTTP Reverse Proxy. |
| Backup server | ESXi host (source and target) | TCP | 443 | Port used as a control channel. |
| ESXi host (source and target) | TCP | 33035 | Port used to install I/O filter components on ESXi hosts. |
| vCenter Server (source and target) | TCP | 443 | Port used as a control channel. |
| CDP proxy (source and target) | TCP | 6182 | Port used as a control channel. |

Universal CDP Components

The following table describes network ports that must be opened to ensure proper communication of Veeam Universal CDP components with other backup components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Source workload | CDP proxy (source) | TCP | 33032 | Default port used as a transmission channel to the source CDP proxy. |
| CDP proxy (source) | CDP proxy (target) | TCP | 33033 | Default port used as a transmission channel to the target CDP proxy. |
| ESXi host (target) | TCP | 902 | Default VMware port used for data transfer. Used during initial synchronization and restore operations. |
| vCenter Server (target) | TCP | 443 | Default VMware web service port that can be customized in vCenter settings. Used during initial synchronization and restore operations. |
| CDP proxy (target) | ESXi host (target) | TCP | 33032 | Default port used as a transmission channel to the target ESXi host. |
| ESXi host (target) | TCP | 902 | Default VMware port used for data transfer. Used during initial synchronization and restore operations. |
| vCenter Server (target) | TCP | 443 | Default VMware web service port that can be customized in vCenter settings. Used during initial synchronization and restore operations. |
| ESXi host (target) | ESXi host (target) | TCP | 33036 | Port used on the target ESXi host for communication between CDP components over HTTPS without HTTP Reverse Proxy. |
| Backup server | Source workload | TCP | 33050 | Port used on the source workload for communication between the Veeam CDP Coordinator Service and Veeam CDP Agent Service over HTTPS. |
| ESXi host (target) | TCP | 443 | Port used as a control channel. |
| ESXi host (target) | TCP | 33035 | Port used to install I/O filter components on ESXi hosts. |
| vCenter Server (target) | TCP | 443 | Port used as a control channel. |
| CDP proxy (source and target) | TCP | 6182 | Port used as a control channel. |

Recovery Components

* [Guest OS File Recovery](#guest_os_file_recovery)
* [Veeam vPower NFS Service](#vpower)
* [SureBackup](#surebackup)
* [SureReplica Recovery Verification](#surereplica)
* [Microsoft Active Directory Domain Controller Connections During Application Item Restore](#ad)
* [Microsoft Exchange Server Connections During Application Item Restore](#ex)
* [Microsoft SQL Server Connections During Application Item Restore](#sql)
* [Restore to Amazon EC2](#restore_to_amazon)
* [Restore to Google Cloud](#restore_to_google_cloud)
* [Restore to Microsoft Azure](#restore_to_azure)
* [Instant Recovery to Microsoft Azure](#instant_recovery_to_azure)

Guest OS File Recovery

The following table describes network ports that must be opened to ensure proper communication between components for guest OS file recovery.

* [Mount Server Connections](#mount_server)
* [Helper Appliance Connections](#helper_appliance)
* [Helper Host Connections](#helper_host)
* [Guest OS Connections](#guest_os_recovery_connections)

Mount Server Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Mount server | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| Backup repository | TCP | 6162, 2500 to 3300 | Default range of ports used for communication with a backup repository.  Note: The port range 2500-3300 is optional. You can use it for failover if port 6162 is unavailable. |
| ESXi host | TCP | 443 | Default port used for connections to the ESXi host. |
| vCenter server | TCP | 443 | Default port used for connections to the vCenter server. |
| Veeam Signature Update Server  (avupdate.veeam.com) | TCP | 443 | Default port used by Veeam Threat Hunter to download information about new malware signatures from the Veeam Signature Update Server over HTTPS. |
| Backup server | Mount server | TCP | 445 | Port used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a mount server and for collecting log files. |
| TCP | 6160 | Default port used by Veeam Installer Service including checking the compatibility between components before starting the recovery process. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6170 | Port used for communication with a local or remote Mount Service. |

Helper Appliance Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Helper appliance | Backup repository | TCP | 2500 to 3300 | Default range of ports used for communication with a backup repository. |
| Helper appliance | ESXi server | TCP | 443 | Default port used for connections to the ESXi host if restore is performed over VIX API/vSphere Web Services.  [For VMware vSphere earlier than 6.5] Not required if vCenter connection is used. In VMware vSphere versions 6.5 and later, port 443 is required by vSphere Web Services. |
| Backup server | Helper appliance | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a helper appliance. |
| Mount server | Helper appliance | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a helper appliance. |

Helper Host Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Helper host | Backup repository | TCP | 2500 to 3300 | Default range of ports used for communication with a backup repository. |
| Helper host | ESXi server | TCP | 443 | Default port used for connections to the ESXi host if restore is performed over VIX API/vSphere Web Services.  [For VMware vSphere earlier than 6.5] Not required if vCenter connection is used. In VMware vSphere versions 6.5 and later, port 443 must also be open to vSphere Web Services. |
| Backup server | Helper host | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a helper host and for collecting log files. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 32768 to 60999 | Dynamic port range for Linux distributions. Used for communication with a helper host. For more information, see the [Linux kernel documentation](https://www.kernel.org/doc/html/latest/networking/ip-sysctl.html#ip-variables). |
| Mount server | Helper host | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a helper host. |
| TCP | 32768 to 60999 | Dynamic port range for Linux distributions. Used for communication with a helper host. For more information, see the [Linux kernel documentation](https://www.kernel.org/doc/html/latest/networking/ip-sysctl.html#ip-variables). |

Guest OS Connections

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| VM guest OS (Linux/Unix) | Helper appliance | TCP | 21 | Default port used for protocol control messages if FTP server is enabled. |
| Helper appliance | VM guest OS (Linux/Unix) | TCP | 20 | Default port used for data transfer if FTP server is enabled. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a VM guest OS. |
| Helper host | VM guest OS (Linux/Unix) | TCP | 2500 to 3300 | Default range of ports used for communication with a VM guest OS. |
| Backup server | VM guest OS (Linux/Unix) | TCP | 22 | Default SSH port used as a control channel. |
| Mount server | VM guest OS (Microsoft Windows) | TCP | 445, 135 | Required to deploy the runtime coordination process on the VM guest OS. |
| TCP | 6160, 11731 | Default port and failover port used by Veeam Installer Service. |
| TCP | 6162 | Port used by the Veeam Transport Service for file-level restore. |
| Backup server | VM guest OS | TCP | 2500 to 3300 | Default range of ports used for communication with a VM guest OS. |

Veeam vPower NFS Service

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Mount server running vPower NFS Service | TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6161 | Default port used by the Veeam vPower NFS Service. |
| ESXi host | Mount server running vPower NFS Service | TCP UDP | 111 | Standard port used by the port mapper service. |
| TCP UDP | 1058+ or 1063+ | Default mount port. The number of port depends on where the vPower NFS Service is located:   * 1058+: If the vPower NFS Service is located on the backup server. * 1063+: If the vPower NFS Service is located on a separate Microsoft Windows machine.   If port 1058/1063 is occupied, the succeeding port numbers will be used. |
| TCP UDP | 2049+ | Standard NFS port. If port 2049 is occupied, the succeeding port numbers will be used. |
| Backup repository or  gateway server working with backup repository | Mount server running vPower NFS Service | TCP | 2500 to 3300 | Default range of ports used as transmission channels during Instant Recovery, SureBackup or Linux file-level recovery.  For every TCP connection that a job uses, one port from this range is assigned. |
| Mount server running vPower NFS Service | Backup repository or  gateway server working with backup repository | TCP | 2500 to 3300 | Default range of ports used as transmission channels during Instant Recovery, SureBackup or Linux file-level recovery.  For every TCP connection that a job uses, one port from this range is assigned. |

SureBackup

The following table describes network ports that must be opened to ensure proper communication between SureBackup components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Proxy appliance | TCP | 443 | Port used for communication with the proxy appliance in the virtual lab. |
| Applications on VMs in the virtual lab | — | — | Application-specific ports to perform port probing test. For example, to verify a DC, Veeam Backup & Replication probes port 389 for a response. |
| Internet-facing proxy server | VMs in the virtual lab | TCP | 8080 | Port used to let VMs in the virtual lab access the Internet. |
| Mount server running vPower NFS Service | Backup repository or  gateway server working with backup repository | TCP | 2500 to 3300 | Default range of ports used as transmission channels during SureBackup.  For every TCP connection that a job uses, one port from this range is assigned. |
| ESXi server | TCP | 443 | Default port used for connections to ESXi host. |
| Backup repository or  gateway server working with backup repository | Mount server running vPower NFS Service | TCP | 2500 to 3300 | Default range of ports used as transmission channels during SureBackup.  For every TCP connection that a job uses, one port from this range is assigned. |
| Backup repository or  gateway server working with backup repository | Hyper-V server | TCP | 2500 to 3300 | Default range of ports used as transmission channels during SureBackup.  For every TCP connection that a job uses, one port from this range is assigned. |

SureReplica Recovery Verification

The following table describes network ports that must be opened to ensure proper communication between SureReplica components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Proxy appliance | TCP | 443 | Port used for communication with the proxy appliance in the virtual lab. |
| Applications on VMs in the virtual lab | — | — | Application-specific ports to perform port probing test. For example, to verify a DC, Veeam Backup & Replication probes port 389 for a response. |
| Internet-facing proxy server | VMs in the virtual lab | TCP | 8080 | Port used to let VMs in the virtual lab access the Internet. |

Microsoft Active Directory Domain Controller Connections During Application Item Restore

The following table describes network ports that must be opened to ensure proper communication of the backup server with the Microsoft Active Directory VM during application-item restore.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Microsoft  Active Directory VM guest OS | TCP | 135 | Port used for communication between the domain controller and backup server. |
| TCP, UDP | 389 | Port used for LDAP connections. |
| TCP | 636, 3268, 3269 | Ports used for LDAP connections. |

Microsoft Exchange Server Connections During Application Item Restore

The following table describes network ports that must be opened to ensure proper communication of the Veeam backup server with the Microsoft Exchange Server system during application-item restore.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Microsoft Exchange 2003/2007 CAS Server | TCP | 80, 443 | Ports used for WebDAV connections. |
| Microsoft Exchange 2010/2013/2016/2019 CAS Server | TCP | 443 | Port used for Microsoft Exchange Web Services Connections. |

Microsoft SQL Server Connections During Application Item Restore

The following table describes network ports that must be opened to ensure proper communication of the backup server with the VM guest OS system during application-item restore.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Microsoft  SQL VM guest OS | TCP | 1433, 1434 and other | Ports used for communication with the Microsoft SQL Server installed inside the VM.  Port numbers depends on configuration of your Microsoft SQL server. For more information, see [this Microsoft article](https://msdn.microsoft.com/en-us/library/cc646023.aspx#BKMK_ssde). |
| UDP | 1434 | Port used by the Microsoft SQL Server Browser service.  For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/tools/configuration-manager/sql-server-browser-service). |

Restore to Amazon EC2

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server or backup repository | Helper appliance | TCP | 22 | Port used as a communication channel to the helper appliance. |
| TCP | 443 | Default redirector port. You can change the port in helper appliance settings. For details, see the Specify Helper Appliance section in [Restore to Amazon EC2](restore_amazon_proxy.md). |

Restore to Google Cloud

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server or backup repository | Helper appliance | TCP | 22 | Port used as a communication channel to the helper appliance. |
| TCP | 443 | Default redirector port. You can change the port in helper appliance settings. For details, see the Specify Helper Appliance section in [Restore to Google Cloud](restore_google_proxy_appliance.md). |

Restore to Microsoft Azure

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Microsoft Azure Resource Manager service  (https://management.azure.com) | TCP | 443 | Port used for Azure resources management and deployment. |
| Microsoft Entra ID  (https://login.microsoftonline.com) | TCP | 443 | Port used for Entra ID authentication. |
| Certificate verification endpoints | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Microsoft Azure storage accounts (blob storage)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used for restored Windows-based VM conversion. Restored disks are temporarily mounted to the backup server.  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Azure Windows VM agent distribution location  (go.microsoft.com, aka.ms, github.com, objects.githubusercontent.com) | TCP | 443 | Port used to install the Azure Windows VM agent on the restored VM.  Consider that the URLs used are subject to change. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-windows#install-the-azure-windows-vm-agent). |
| Helper appliance | TCP | 22 | Port used by default as a communication channel to the helper appliance when restoring Linux workloads.  This port can be changed during helper appliance deployment. For details, see [Managing Helper Appliances](restore_azure_linux.md). |
| Backup server or backup repository | Azure restore proxy appliance | TCP | 443 | Default management and data transport port required for communication with the Azure restore proxy appliance. The port must be accessible from the backup server and backup repository storing VM backups.  This port can be changed in the settings of the Azure Restore proxy appliance. For details, see [Specify Credentials and Transport Port](restore_azure_proxy_credentials.md). |

Instant Recovery to Microsoft Azure

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Backup server | Microsoft Azure Resource Manager service  (https://management.azure.com) | TCP | 443 | Port used for Azure Resources management and deployment.  Service Tag: AzureResourceManager |
| Microsoft Azure storage account (Veeam packages upload)  (<storage-account>.queue.core.windows.net, <storage-account>.queue.storage.azure.net) | TCP | 443 | Port used to deliver Veeam components from the backup server to the temporary Azure VM used to create templates of Instant Recovery to Azure helper appliances.  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Microsoft Azure storage account (message queues)  (<storage-account>.queue.core.windows.net, <storage-account>.queue.storage.azure.net) | TCP | 443 | Port used for communication with Instant Recovery to Azure helper appliances via Azure Message queues.  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Microsoft Entra ID  (https://login.microsoftonline.com) | TCP | 443 | Port used for Entra ID authentication to access storage accounts and message queues.  Service Tag: AzureActiveDirectory |
| Certificate verification endpoints | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Instant Recovery for Azure helper appliance | Microsoft Azure storage account (message queues)  (<storage-account>.queue.core.windows.net, <storage-account>.queue.storage.azure.net) | TCP | 443 | Port used for communication with the backup server through Azure Message queues.  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Microsoft Azure storage account (backup repository) / Veeam Data Cloud Vault (backup repository)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used to access backups.  Consider that the <storage-account> part of the address must be replaced with the ID of your storage vault. You can find the storage vault ID in the Storage Vaults > Vault ID section in Veeam Data Cloud Vault. For more information, see the [Managing Storage Vaults](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#viewing-storage-vault-details) section in the Veeam Data Cloud User Guide.  Service Tag: Storage |
| Certificate verification endpoints | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Azure Windows VM Agent Distribution location  (go.microsoft.com, aka.ms, github.com, objects.githubusercontent.com) | TCP | 443 | Port used to install the Azure Windows VM agent on the restored Windows VM.  Consider that these URLs are subject to change. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-windows#install-the-azure-windows-vm-agent). |
| Microsoft Entra ID  (https://login.microsoftonline.com) | TCP | 443 | Port used for Entra ID authentication to access storage accounts and message queues. |
| Azure Instance Metadata Service endpoint  (http://169.254.169.254) | TCP | 80 | Port used for Entra ID authentication to access storage accounts and message queues and other purposes:  Service Tag: AzureActiveDirectory |
| Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Microsoft Azure storage account (Veeam packages upload)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used to deliver Veeam components from the backup server to the temporary VM,  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Microsoft Azure storage account (message queues)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used for communication with the backup server through Azure Message queues,  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Ubuntu Azure repository  (http://azure.archive.ubuntu.com/ubuntu/) | TCP | 80 | Port used to install prerequisite packages. |
| Certificate verification endpoints | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access |
| Restored VM | Instant Recovery to Azure helper appliance | TCP | 3260-3262 | Ports used to boot the restored VM from backed up disks with iSCSI protocol. |
| TCP | 9555 | Port used to get boot firmware configuration from the Platform Converter Service running on the appliance. |

Other Veeam Products and Components

Veeam Agents

* [Connections for Veeam Agent Backup with Veeam Backup & Replication](agents_used_ports.md)

Veeam Backup Enterprise Manager

* [Veeam Backup Enterprise Manager Connections](https://helpcenter.veeam.com/docs/vbr/em/used_ports.html?ver=13)

Veeam Explorers

* [Veeam Explorer for Microsoft Active Directory Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vead_ports.html?ver=13)
* [Veeam Explorer for Microsoft Exchange Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vex_ports.html?ver=13)
* [Veeam Explorer for Microsoft SharePoint and Veeam Explorer for Microsoft OneDrive for Business Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vesp_ports.html?ver=13)
* [Veeam Explorer for Microsoft SQL Server Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vesql_used_ports.html?ver=13)
* [Veeam Explorer for Microsoft Teams Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vet_ports.html?ver=13)
* [Veeam Explorer for Oracle Connections](https://helpcenter.veeam.com/docs/vbr/explorers/veo_used_ports.html?ver=13)
* [Veeam Explorer for PostgreSQL Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vep_used_ports.html?ver=13)

Veeam Backup for Microsoft Entra ID

* [Veeam Backup for Microsoft Entra ID Connections](https://helpcenter.veeam.com/docs/vbr/entraid/entra_id_ports.html?ver=13)

Veeam Cloud Connect

* [Veeam Cloud Connect Connections](https://helpcenter.veeam.com/docs/vbr/cloud/ports.html?ver=13)

Veeam Plug-Ins for Enterprise Applications

* [Connections for Veeam Plug-In for Oracle RMAN](ports_vprman.md)
* [Connections for Veeam Plug-In for SAP HANA](ports_vpsh.md)
* [Connections for Veeam Plug-In for SAP on Oracle](ports_sap_orcl.md)
* [Connections for Veeam Plug-In for SAP MaxDB](plugins_sap_maxdb_preparation_ports.md)
* [Connections for Veeam Plug-In for Microsoft SQL Server](ports_mssql.md)
* [Connections for Veeam Plug-In for IBM Db2](db2_plugin_ports.md)

* [Connections for Components in Veeam Plug-In Management Infrastructure](plan_and_manage_used_ports.md)

MongoDB Backup

* [Connections for MongoDB Backup](mongo_plan_and_manage_ports.md)

Veeam Plug-Ins for Cloud Solutions

* [AWS Plug-In for Veeam Backup & Replication](https://helpcenter.veeam.com/docs/vbaws/guide/ports.html?ver=10)
* [Microsoft Azure Plug-In for Veeam Backup & Replication](https://helpcenter.veeam.com/docs/vbazure/guide/ports.html?ver=8.1)
* [Veeam Plug-in for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/ports.html?ver=7)

Kasten

* [Veeam Kasten Plug-In for Veeam Backup & Replication Connections](https://helpcenter.veeam.com/docs/vbr/kasten_integration/used_ports.html?ver=13)

Virtualization Platforms

* [Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization Connections](https://helpcenter.veeam.com/docs/vbrhv/userguide/used_ports.html?ver=7)

* [Veeam Plug-In for Nutanix AHV Connections](https://helpcenter.veeam.com/docs/vbahv/userguide/used_ports.html?ver=9)
* [Veeam Plug-In for Proxmox VE Connections](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/used_ports.html?ver=3)

Nutanix Mine with Veeam

* [Nutanix Mine with Veeam Connections](https://helpcenter.veeam.com/docs/nutanixmine/userguide/used_ports.html?ver=40)


