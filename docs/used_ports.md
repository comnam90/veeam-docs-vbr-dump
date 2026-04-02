---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html"
last_updated: "4/1/2026"
product_version: "13.0.1.2067"
---

# Ports


This section describes incoming connections for different components in the backup infrastructure. The first part describes ports that must be opened on the core backup infrastructure components. These ports allow basic operations for data protection such as backup and replication. The second part describes ports required for different features.

On backup infrastructure components, Veeam Backup & Replication automatically creates firewall rules for the required ports on Microsoft Windows-based machines. If you are using a third-party firewall, these rules must be created manually. These rules allow components to communicate with each other. You can find the full list of the ports for standard installations in this section.

Considerations

* Ports described for the core backup infrastructure components are considered basic ports that must be opened whenever these components are used for any data protection tasks.
* If a backup infrastructure component performs multiple roles (for example, acts as both a backup proxy and a repository), make sure all required ports for each role are opened.
* Some Linux distributions also require firewall and security rules to be created manually. For details, see [this Veeam KB article](https://www.veeam.com/kb2986).
* If you use an HTTP/HTTPS proxy server to access the Internet, make sure that WinHTTP settings are properly configured on Microsoft Windows machines with Veeam backup infrastructure components. For information on how to configure WinHTTP settings, see [Microsoft Docs](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/configure-proxy-internet).
* Tenants cannot access Veeam Cloud Connect infrastructure components through HTTP/HTTPS proxy servers. For information on supported protocols for Veeam Cloud Connect, see the [Ports](https://helpcenter.veeam.com/docs/vbr/cloud/ports.html?ver=13) section in the Veeam Cloud Connect Guide.

Backup Server

The following table describes basic network ports that must be opened to ensure proper communication with the [backup server](backup_server.md). For the high availability cluster feature, also see [High Availability (HA) Cluster Components](#ha).

Backup Server

| From | To | Protocol | Port | Notes |
| PC where web UI is open,  Remote Veeam Backup & Replication console,  Mount server | Backup server | TCP | 443 | Port used to communicate with the backup server. |
| PC where web UI is open | Backup server | TCP | 10443 | Port used by the Host Management console to connect to Linux-based backup servers deployed from the Veeam Software Appliance ISO. |
| Remote access PC | Backup server | TCP | 22 | Port used to connect to Linux-based backup servers deployed from the Veeam Software Appliance ISO through SSH. |
| TCP | 3389 | Default port used by Remote Desktop Services to connect to Windows-based backup servers.  If you use third-party solutions to connect to the backup server, other ports may need to be open. |
| Veeam Backup & Replication console | Backup server | TCP | 9420 | [For console version 12.3.2 P1 (build 12.3.2.4165)] Port used by the Veeam Backup & Replication console to communicate with the backup server for console automatic update. |
| Backup proxy | Backup server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine) for ransomware index transfer.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup repository (Linux),  Backup repository (Microsoft Windows),  Gateway server,  Mount server | Backup server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Mount server | Backup server | TCP | 9401 | Port used for communication with the Veeam Backup Service.  Also required to perform Copy to and Mount to console operations during Windows file-level recovery. |
| REST client | Backup server | TCP | 9419 | Default ports for communication with REST API service. |
| Veeam Infrastructure Appliance | Backup server | TCP | 443 | Port used by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO to authenticate incoming connections from Veeam Backup & Replication. |

Veeam Servers and Services

The following table describes basic network ports that must be opened to ensure proper communication with Veeam servers and services.

Veeam Servers and Services

| From | To | Protocol | Port | Notes |
| Communication with Update Repositories | | | | |
| Backup server,  Veeam Infrastructure Appliance | Veeam Update Repository  (repository.veeam.com) | TCP | 443 or 80 | Port used to connect to the Veeam Update Repository. The port is used by Linux-based backup servers deployed from the Veeam Software Appliance ISO and by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO.  The repository is Veeam-maintained and provides product, operating system, and security updates. For more information, see [How Updates Work](update_appliance_hiw.md). |
| Backup server,  Veeam Infrastructure Appliance | Veeam Update Repository (local mirror)  (<localmirrorrepository.domain>) | TCP | 443 or 80 | Port used to connect to a local mirror of the Veeam Update Repository. For more information, see [Configuring Updates](update_appliance_configure_updates.md).  This port is used by Linux-based backup servers deployed from the Veeam Software Appliance ISO and by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO.  Consider that the address must be replaced with the actual URL of your mirror repository. |
| Backup server | Veeam License Update Server  (vbr.butler.veeam.com, autolk.veeam.com) | TCP | 443 | Default port used to automatically update license from the Veeam License Update Server over HTTPS. Veeam Threat Hunter and Veeam Data Cloud Vault also require this communication to work properly. |
| Backup server | Veeam License Update Server  (\*.ss2.us, \*.amazontrust.com) | TCP | 80 | Port used for certificate validation when Veeam Backup & Replication connects to Veeam License Update Server to check if the new license is available and download it. Veeam Threat Hunter also requires this communication to work properly.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server can reach these verification endpoints. |
| Backup server | Veeam Update Notification Server  (dev.veeam.com, vbrad.butler.veeam.com, vbrce.butler.veeam.com) | TCP | 443 | Default port used to download information about available updates from the Veeam Update Notification Server over HTTPS. |
| Communication with Veeam AI Assistant | | | | |
| Veeam Backup & Replication console,  PC where web UI is open | Veeam AI Assistant  (rest-ai.veeam.com) | TCP | 443 | Default port for communication with the Veeam AI Assistant service. |
| Communication with Veeam ONE | | | | |
| Backup server | Veeam ONE Server | TCP | 2741 | Default port used for communication with Veeam ONE internal Web API.  Required for the Analytics view. For more information, see [Configuring Analytics View](configure_analytics.md). |
| 2805 | Port used for communication between Veeam Analytics Service and Veeam ONE Monitoring service. This is required for Veeam ONE data collection. |
| Backup server | Veeam ONE Web Services | TCP | 1239 | Default port used by Veeam ONE Web Services.  Required for the Analytics view. For more information, see [Configuring Analytics View](configure_analytics.md). |

Databases and External Services

The following table describes basic network ports that must be opened to ensure proper communication with databases and different external servers such as mail servers, time servers and others.

Databases and External Services

| From | To | Protocol | Port | Notes |
| Communication with Configuration Databases | | | | |
| Backup server | PostgreSQL configuration database | TCP | 5432 | Port used for communication with PostgreSQL configuration database. |
| Backup server | Microsoft SQL Server hosting the Veeam Backup & Replication configuration database | TCP | 1433 | Port used for communication with Microsoft SQL Server on which the Veeam Backup & Replication configuration database is deployed (if you use a Microsoft SQL Server default instance).  Additional ports may need to be open depending on your configuration. For more information, see [Microsoft Docs](https://msdn.microsoft.com/en-us/library/cc646023%28v%3Dsql.120%29.aspx#BKMK_ssde). |
| Communication with Mail Servers | | | | |
| Backup server | SMTP server | TCP | 25 | Port used by the SMTP server. |
| TCP | 587 | Port used by the SMTP server if SSL is enabled. |
| Backup server | Gmail REST API  (gmail.googleapis.com) | TCP | 443 | Port used to communicate with Google Mail services.  For the authentication process, you need to access accounts.google.com and also gstatic.com for resources like javascript. |
| Backup server | Microsoft Graph REST API  (graph.microsoft.com, login.microsoftonline.com) | TCP | 443 | Port used to communicate with Microsoft Exchange Online organizations. |
| Communication with Time Servers | | | | |
| Backup server,  Veeam Infrastructure Appliance | NTP server | UDP | 123 | Port used for synchronization with NTP time servers. The port is used by Linux-based backup servers deployed from the Veeam Software Appliance ISO and by backup infrastructure components deployed from the Veeam Infrastructure Appliance  ISO. |
| Backup server,  Veeam Infrastructure Appliance | NTS server | UDP | 123 | Ports used for synchronization with NTS time servers. The port is used by Linux-based backup servers deployed from the Veeam Software Appliance ISO and by backup infrastructure components deployed from theVeeam Infrastructure Appliance ISO. |
| TCP | 4460 |  |
| Other Communication | | | | |
| Any backup infrastructure component | DNS server | UDP, TCP | 53 | Port used for communication with the DNS server. It is required for forward/reverse name resolution of all backup and infrastructure servers including Active Directory domain controllers. |
| Backup server | Certificate Revocation Lists | TCP | 80 or 443 | Port used for access to the Certificate Revocation Lists (CRL) of the Certificate Authority (CA) that issued the certificate for each backup infrastructure component.  Note: The specific CRL endpoint that must be connected to depends on the CA that issued the certificate.  You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server can reach these verification endpoints. |
| Backup server | KMS server | TCP | 5696 | Default port used for communication with the Key Management System server. |
| Backup server | Syslog server | TCP, UDP | 514 | Default port used to communicate with the syslog server. |
| TCP | 6514 | Default port used to communicate with the syslog server over TLS. |
| Backup server,  Veeam Infrastructure Appliance | Active Directory Domain Controllers | TCP | 636, 3268, 3269 | Ports used for communication over LDAP and LDAPS protocols. |
| UDP, TCP | 389 |
| UDP, TCP | 445, 139 | Ports used for communication over SMB protocol. |
| UDP, TCP | 88 | Port used for Kerberos authentication. |
| Communication for SMB (CIFS) Repositories | | | | |
| Gateway server or  Backup proxy | Active Directory Domain Controllers | TCP | 389 | Port used for communication over LDAP and LDAPS protocols. |
| TCP | 88 | Port used for Kerberos authentication. |

Veeam Infrastructure Appliances

The following table describes basic network ports that must be opened to ensure proper communication with [Veeam Infrastructure Appliances](linux_infrastructure.md).

|  |
| --- |
| Note |
| The following ports are required by all Veeam Infrastructure Appliances. You must also open additional ports based on the role you have assigned to the Veeam Infrastructure Appliance. They can be found on this page in the relevant section for the role. For example, [Backup Proxy](#proxy) or [Gateway Server](#gateway).  For more information on the roles that can be assigned to a Veeam Infrastructure Appliance, see [Considerations and Limitations](linux_infrastructure_appliance_byb.md). |

Veeam Infrastructure Appliances

| From | To | Protocol | Port | Notes |
| Backup server | Veeam Infrastructure Appliance | TCP | 443 | Port used by Veeam Backup & Replication to synchronize Veeam Updater settings on backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO. |
| PC where web UI is open | Veeam Infrastructure Appliance | TCP | 10443 | Port used by backup infrastructure components deployed from the Veeam Infrastructure Appliance ISO. Required to connect to the Host Management console. |

Backup Proxies

The following table describes basic network ports that must be opened to ensure proper communication with [backup proxies](proxies.md). For more information about ports that must be opened for backup repositories, see [Backup Repositories](#backup_repos).

Backup Proxies

| From | To | Protocol | Port | Notes |
| Backup server,  Backup proxy,  Microsoft Windows/Linux-based backup repository,  Mount server | Backup proxy | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  [For Linux backup proxy] You can specify a different port while adding the Linux server to the Veeam Backup & Replication infrastructure. Note that you can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on this Linux server. For more information, see [Specify Credentials and SSH Settings](linux_server_ssh.md).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Backup proxy (Microsoft Windows) | TCP | 445, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| Backup server | Backup proxy (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 6160 | Default port used by Veeam Installer Service for Linux. |
| Communication for Veeam Data Cloud Vault, Object Storage Repositories, External Repositories | | | | |
| On-premises backup repository,  Gateway server | Backup proxy (direct connection) | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Gateway Servers

The following table describes basic network ports that must be opened to ensure proper communication with [gateway servers](gateway_server.md). For more information about ports that must be opened for backup repositories, see [Backup Repositories](#backup_repos).

Gateway Servers

| From | To | Protocol | Port | Notes |
| Backup server,  Backup proxy,  Hyper-V server/Off-host backup proxy,  VM Guest OS | Gateway server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  [For Linux gateway server] You can specify a different port while adding the Linux server to the Veeam Backup & Replication infrastructure. Note that you can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on this Linux server. For more information, see [Specify Credentials and SSH Settings](linux_server_ssh.md).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Gateway server (Microsoft Windows) | TCP | 445, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| Backup server | Gateway server (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 6160 | Default port used by Veeam Installer Service for Linux. |
| Mount server running vPower NFS Service | Gateway server working with backup repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine) during Instant Recovery, SureBackup or Linux file-level recovery.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Communication for Veeam Data Cloud Vault, Object Storage Repositories, External Repositories | | | | |
| On-premises backup repository,  Gateway server | Gateway server for Veeam Data Cloud Vault | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Backup Repositories

The following section describes ports that must be opened to ensure proper communication with different backup repositories:

* [Common ports](#repo_common)
* [Microsoft Windows/Linux-Based backup repositories](#repo)
* [NFS backup repositories](#nfs_repository)
* [SMB backup repositories](#smb_repository)
* [Dell Data Domain System](#emc)
* [ExaGrid, Quantum DXi, Fujitsu ETERNUS CS800, Infinidat InfiniGuard](#exagrid)
* [HPE StoreOnce](#storeonce)
* [Veeam Data Cloud Vault](#VDCvault)
* [Object storage repositories](#osrc)
* [Scale-out backup repositories](#scaleout)
* [External repositories](#external_repo)
* [Archive object storage repositories](#archive_tier)

Common Ports

The following table describes basic network ports that must be opened to ensure proper communication with backup repositories. These ports must be opened for all types of the backup repositories.

Common Ports

| From | To | Protocol | Port | Notes |
| Mount server running vPower NFS Service | Backup repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine) during Instant Recovery, SureBackup or Linux file-level recovery.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Veeam Backup & Replication console,  Backup proxy,  Hyper-V server/Off-host backup proxy | Backup repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  [For Linux repository] You can specify a different port while adding the Linux server to the Veeam Backup & Replication infrastructure. Note that you can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on this Linux server. For more information, see [Specify Credentials and SSH Settings](linux_server_ssh.md).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Microsoft Windows/Linux-Based Backup Repositories

The following table describes basic network ports that must be opened to ensure proper communication with Microsoft Windows/Linux-based backup repositories. You must also open ports described in [Backup Repository Common Ports](#repo_common).

Microsoft Windows/Linux-Based Backup Repositories

| From | To | Protocol | Port | Notes |
| Backup server | Backup repository | TCP | 6160 | Default port used by Veeam Installer Service. |
| Backup server | Backup repository (Microsoft Windows) | TCP | 445, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| Backup server | Backup repository (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| Source backup repository | Target backup repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  If the backup copy job utilizes WAN accelerators, make sure that [ports specific for WAN accelerators](used_ports.md#wan) are opened.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

NFS Backup Repositories

The following table describes basic network ports that must be opened to ensure proper communication with [NFS shares added as backup repositories](nfs_share.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

NFS Backup Repositories

| From | To | Protocol | Port | Notes |
| Gateway server or  Backup proxy | NFS backup repository | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service.  Also used as a transmission channel from the gateway server to the target NFS backup repository if a gateway server is specified explicitly in NFS backup repository settings. |
| Gateway server or  Backup proxy | NFS backup repository (NFS v3) | TCP, UDP | mountd\_port | Dynamic port used for mountd service. Can be assigned statically. |
| TCP, UDP | statd\_port | Dynamic port used for statd service. Can be assigned statically. |
| TCP, UDP | lockd\_port | Dynamic port used for lockd service. Can be assigned statically. |

SMB Backup Repositories

The following table describes basic network ports that must be opened to ensure proper communication with [SMB (CIFS) shares added as backup repositories](smb_share.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

SMB Backup Repositories

| From | To | Protocol | Port | Notes |
| Gateway server or  Backup proxy | SMB (CIFS) backup repository (Microsoft Windows) | TCP | 445 | Port used as a transmission channel from the gateway server to the target SMB (CIFS) backup repository if a gateway server is specified explicitly in SMB (CIFS) backup repository settings. |

Dell Data Domain System

The following table describes basic network ports that must be opened to ensure proper communication with [Dell Data Domain storage systems added as deduplicating appliances](dell_dd.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

For more information, see [Dell Documents](https://www.dell.com/support/kbdoc/en-us/000126375/powerprotect-and-data-domain-core-documents).

Dell Data Domain System

| From | To | Protocol | Port | Notes |
| Backup server,  Gateway server | Dell Data Domain | TCP | 111 | Port used to assign a random port for the mountd service used by NFS and DDBOOST. Mountd service port can be statically assigned. |
| TCP | 2049 | Main port used by NFS. Can be modified using the ‘nfs set server-port’ command. Command requires SE mode. |
| TCP | 2052 | Main port used by NFS MOUNTD. Can be modified using the 'nfs set mountd-port' command in SE mode. |

ExaGrid, Quantum DXi, Fujitsu ETERNUS CS800, Infinidat InfiniGuard

The following table describes basic network ports that must be opened to ensure proper communication with storage systems added as deduplicating appliances:

* [ExaGrid](deduplicating_appliance_exgrid.md)
* [Quantum DXi](deduplicating_appliance_quantum.md)
* [Fujitsu ETERNUS CS800](fujitsu.md)
* [Infinidat InfiniGuard](infinidat_infiniguard.md)

You must also open ports described in [Backup Repository Common Ports](#repo_common).

ExaGrid, Quantum DXi, Fujitsu ETERNUS CS800, Infinidat InfiniGuard

| From | To | Protocol | Port | Notes |
| Backup server | Deduplicating appliance | TCP | 22 | Default command port used for communication with the deduplicating appliance and initial installation of Veeam components. |
| TCP | 6160 | Default port used by Veeam Installer Service for components management and upgrade. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Data Mover Service.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

HPE StoreOnce

The following table describes basic network ports that must be opened to ensure proper communication with [HPE StoreOnce storage systems added as deduplicating appliances](deduplicating_appliance_storeonce.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

HPE StoreOnce

| From | To | Protocol | Port | Notes |
| Backup server or  Gateway server | HPE StoreOnce | TCP | 9387 | Default command port used for communication with HPE StoreOnce. |
| TCP | 9388 | Default data port used for communication with HPE StoreOnce. |

Veeam Data Cloud Vault

The following table describes network ports and endpoints that must be opened to ensure proper communication with Veeam Data Cloud Vault. You must also open ports described in [Backup Repository Common Ports](#repo_common).

Veeam Data Cloud Vault

| From | To | Protocol | Port | Notes |
| Backup server,  Backup proxy (direct connection)/  Gateway server/  Instant Recovery to Azure helper appliance | Veeam Data Cloud Vault  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used to communicate with the Microsoft Azure object storage.  Consider that the <storage-account> part of the address must be replaced with the ID of your storage vault. You can find the storage vault ID in the Storage Vaults > Vault ID section in Veeam Data Cloud Vault. For more information, see the [Managing Storage Vaults](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#viewing-storage-vault-details) section in the Veeam Data Cloud User Guide. |
| Backup server,  Backup proxy (direct connection)/  Gateway server/  Instant Recovery to Azure helper appliance | Veeam Data Cloud Vault | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server, or proxy, or gateway server, or helper appliance can reach these verification endpoints. |
| Backup server | Microsoft Entra ID  (login.microsoftonline.com, login.windows.net) | TCP | 443 | Port used for Entra ID authentication. |

Object Storage Repositories

The following table describes network ports and endpoints that must be opened to ensure proper communication with [object storage repositories](object_storage_repository.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

Object Storage Repositories

| From | To | Protocol | Port | Notes |
| Backup server | Smart Object Storage API (SOSAPI) compatible S3 object storage | TCP | 443 | Port used by Veeam Backup & Replication for auxiliary communication with object storage repositories that support Smart Object Storage API (SOSAPI). |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with the Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Amazon S3 object storage  (\*.amazontrust.com) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or gateway server, or helper appliance can reach these verification endpoints. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | S3 compatible object storage | TCP | Depends on device configuration | Port used to communicate with S3 compatible object storage. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | Port used to communicate with the Microsoft Azure object storage.  The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Microsoft Azure object storage | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or gateway server, or helper appliance can reach these verification endpoints. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Google Cloud storage  (storage.googleapis.com) | TCP | 443 | Port used to communicate with Google Cloud storage.  All cloud endpoints are specified in [this Google article](https://cloud.google.com/storage/docs/request-endpoints). |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Google Cloud storage  (ocsp.pki.goog, pki.goog, crl.pki.goog) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or gateway server, or helper appliance can reach these verification endpoints. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | IBM Cloud object storage | TCP | Depends on device configuration | Port used to communicate with IBM Cloud object storage. |

Scale-Out Backup Repositories

The following table describes basic network ports that must be opened to ensure proper communication with [scale-out backup repositories](backup_repository_sobr.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

Scale-Out Backup Repositories

| From | To | Protocol | Port | Notes |
| Source extent | Target extent | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Target extent | Source extent | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

External Repositories

The following table describes basic network ports that must be opened to ensure proper communication with [external repositories](external_repository.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

External Repositories

| From | To | Protocol | Port | Notes |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Amazon S3 object storage  (\*.amazontrust.com) | TCP | 80 | Port used to verify certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or backup server, or helper appliance can reach these verification endpoints. |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | Port used to communicate with Microsoft Azure object storage.  The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Microsoft Azure object storage | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or backup server, or helper appliance can reach these verification endpoints. |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Google Cloud storage  (storage.googleapis.com) | TCP | 443 | Port used to communicate with Google Cloud storage.  All cloud endpoints are specified in [this Google article](https://cloud.google.com/storage/docs/request-endpoints). |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Google Cloud storage  (ocsp.pki.goog, pki.goog, crl.pki.goog) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or backup server, or helper appliance can reach these verification endpoints. |

Archive Object Storage Repositories

The following table describes basic network ports that must be opened to ensure proper communication with object storage repositories used as a part of [Archive Tier](archive_tier.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

Archive Object Storage Repositories

| From | To | Protocol | Port | Notes |
| Gateway server or  Backup server | Amazon EC2 helper appliance | TCP | 443 | Port used by default to communicate with the Amazon EC2 helper appliance through public/private IPv4 addresses of EC2 appliances.  If you use Amazon S3 Glacier object storage, the gateway server should have direct connection to AWS service endpoints. HTTP/HTTPS proxy servers are not supported.  If there is no gateway server selected, the backup server will be used as a gateway server. |
| TCP | 22 | Default SSH port used as a control channel. |
| Gateway server or  Backup server | Microsoft Azure proxy appliance | TCP | 443 | Port used by default to communicate with the Microsoft Azure helper appliance through public/private IPv4 addresses of Azure appliances.  If there is no gateway server selected, the backup server will be used as a gateway server. |
| TCP | 22 | Default SSH port used as a control channel. |
| Amazon EC2 helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with the Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Amazon EC2 helper appliance | Amazon S3 object storage  (\*.amazontrust.com) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the helper appliance can reach these verification endpoints. |
| Microsoft Azure proxy appliance | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | Port used to communicate with the Microsoft Azure object storage.  The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Microsoft Azure proxy appliance | Microsoft Azure object storage | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy appliance can reach these verification endpoints. |

Mount Servers

The following table describes basic network ports that must be opened to ensure proper communication with mount servers. The mount server can be used in different data protection operations. For more information, see [Mount Servers](mount_server.md) and [Veeam vPower NFS Service](vpower_nfs_service.md).

Mount Servers

| From | To | Protocol | Port | Notes |
| Veeam Backup & Replication console | Mount server | TCP | 6162, 2500 to 3300 | [Remote console only] Ports used as data transmission channels for guest OS file-level restore. For every TCP connection that a job uses, one port from this range is assigned.  These ports are used if the mount server is not located on the console.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Mount server | TCP | 445 | Port used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component. |
| TCP | 6160 | Default port used by Veeam Installer Service including checking the compatibility between components before starting the recovery process. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6170 | Port used for communication with a local or remote Mount Service. |
| Connections of Mount Servers with vPower NFS Service | | | | |
| Backup server | Mount server running vPower NFS Service | TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6161 | Default port used by the Veeam vPower NFS Service. |
| ESXi host | Mount server running vPower NFS Service | TCP UDP | 111 | Standard port used by the port mapper service. |
| TCP UDP | 1058+ or 1063+ | Default mount port. The number of port depends on where the vPower NFS Service is located:   * 1058+: If the vPower NFS Service is located on the backup server. * 1063+: If the vPower NFS Service is located on a separate Microsoft Windows machine.   If port 1058/1063 is occupied, the succeeding port numbers will be used. |
| TCP UDP | 2049+ | Standard NFS port. If port 2049 is occupied, the succeeding port numbers will be used. |
| Backup repository or  Gateway server working with backup repository | Mount server running vPower NFS Service | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine) during Instant Recovery, SureBackup or Linux file-level recovery.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Storage Systems

The following tables describe basic network ports that must be opened to ensure proper communication with [storage systems](storage_infrastructure.md).

The following section describes ports that must be opened to ensure proper communication with different storage systems involved in [storage system snapshot integration](storage_integration.md):

* [Dell Unity XT, Unity storage](#dell_unity) [Storage System Snapshot Integration](storage_integration.md)
* [Dell PowerScale (formerly Isilon) storage](#dell_isilon)
* [HPE 3PAR StoreServ storage](#3par)
* [HPE Alletra Storage MP B10000, Alletra 9000, Primera storage](#hpe_primera)
* [HPE Alletra 5000, Alletra 6000, Nimble storage](#nimble)
* [Lenovo ThinkSystem DM/DG Series storage](#lenovo_thinksystem)
* [NetApp ONTAP storage](#netapp)
* [Nutanix Files storage](#nutanix_files_storage)
* [Universal storage API integrated system](#usais)

If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Dell Unity XT, Unity Storage

The following table describes basic network ports that must be opened to ensure proper communication with Dell Unity XT, Unity.

Dell Unity XT, Unity Storage

| From | To | Protocol | Port | Notes |
| Backup server | Dell Unity XT, Unity storage system | TCP | 443 | Default port used for communication with Dell Unity XT/Unity over HTTPS and sending REST API calls. |
| Backup proxy | Dell Unity XT, Unity storage system | TCP | 3260 | Default iSCSI target port. |
| TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |

Dell PowerScale (Formerly Isilon) Storage

The following table describes basic network ports that must be opened to ensure proper communication with Dell PowerScale (Formerly Isilon).

Dell PowerScale (Formerly Isilon) Storage

| From | To | Protocol | Port | Notes |
| Backup server | Dell PowerScale storage system | TCP | 8080 | Default port used for communication with Dell PowerScale over HTTPS and sending REST API calls. |
| Backup proxy | Dell PowerScale storage system | TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |

HPE 3PAR StoreServ Storage

The following table describes basic network ports that must be opened to ensure proper communication with HPE 3PAR StoreServ.

HPE 3PAR StoreServ Storage

| From | To | Protocol | Port | Notes |
| Backup server | HPE 3PAR StoreServ storage system | TCP | 8008 | Default port used for communication with HPE 3PAR StoreServ over HTTP. |
| TCP | 8080 | Default port used for communication with HPE 3PAR StoreServ over HTTPS. |
| TCP | 22 | Default command port used for communication with HPE 3PAR StoreServ over SSH. |
| Backup proxy | HPE 3PAR StoreServ storage system | TCP | 3260 | Default iSCSI target port. |

HPE Alletra Storage MP B10000, Alletra 9000, Primera Storage

The following table describes basic network ports that must be opened to ensure proper communication with HPE Alletra Storage MP B10000, Alletra 9000, Primera.

HPE Alletra Storage MP B10000, Alletra 9000, Primera Storage

| From | To | Protocol | Port | Notes |
| Backup server | HPE Alletra Storage MP B10000,  Alletra 9000, Primera storage system | TCP | 443 | Default port used for communication with HPE Alletra Storage MP B10000/Alletra 9000/Primera over HTTPS. |
| TCP | 22 | Default command port used for communication with HPE Alletra Storage MP B10000/Alletra 9000/Primera over SSH. |
| Backup proxy | HPE Alletra Storage MP B10000, Alletra 9000, Primera storage system | TCP | 3260 | Default iSCSI target port. |
| Backup proxy | HPE Alletra Storage MP B10000, Alletra 9000 | TCP | 4420, 8009 | Default NVMe-oF ports. |

HPE Alletra 5000, Alletra 6000, Nimble Storage

The following table describes basic network ports that must be opened to ensure proper communication with HPE Alletra 5000, Alletra 6000, Nimble.

HPE Alletra 5000, Alletra 6000, Nimble Storage

| From | To | Protocol | Port | Notes |
| Backup server | HPE Alletra 5000, Alletra 6000/Nimble storage system | TCP | 5392 | Default command port used for communication with HPE Alletra 5000/Alletra 6000/Nimble. |
| Backup proxy | HPE Alletra 5000, Alletra 6000/Nimble storage system | TCP | 3260 | Default iSCSI target port. |

Lenovo ThinkSystem DM/DG Series Storage, NetApp ONTAP Storage

The following table describes network ports that must be opened to ensure proper communication with the following storage systems:

* Lenovo ThinkSystem DM/DG Series
* NetApp ONTAP

Lenovo ThinkSystem DM/DG Series Storage, NetApp ONTAP Storage

| From | To | Protocol | Port | Notes |
| Backup server | Storage system | TCP | 80 | Default command port used for communication with Lenovo ThinkSystem DM/DG Series over HTTP. |
| TCP | 443 | Default command port used for communication with Lenovo ThinkSystem DM/DG Series over HTTPS. |
| Backup proxy | Storage system | TCP, UDP | 111, 2049, 635 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |
| TCP | 3260 | Default iSCSI target port. |

Nutanix Files Storage

The following table describes basic network ports that must be opened to ensure proper communication with Nutanix Files.

Nutanix Files Storage

| From | To | Protocol | Port | Notes |
| Backup server | Nutanix Files storage system | TCP | 9440 | Default port used for communication with Nutanix Files and sending REST API calls. |
| Backup proxy | Nutanix Files storage system | TCP, UDP | 111, 2049, 20048 | Default NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Default SMB port. |

Universal Storage API Integrated System

The following tables describe network ports that must be opened to ensure proper communication with Universal Storage API integrated systems:

* [DataCore SANsymphony](#DataCore), [Dell PowerMax](#dell_powermax), [Hitachi VSP/VSP One Block](#vsp), [HPE XP](#xp), [INFINIDAT InfiniBox](#infinidat), [NetApp SolidFire/HCI](#solidfire)
* [Dell SC Series](#DellEMC)
* [Dell PowerStore](#dell_powerstore)
* [Fujitsu ETERNUS DX/AF](#fujitsu), [IBM FlashSystem (formerly Spectrum Virtualize) Storage](#ibm), [NEC Storage M Series](#necm)
* [Pure Storage FlashArray](#pure), [Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)](#WesternDigital)

DataCore SANsymphony, Dell PowerStore, Hitachi VSP/VSP One Block, HPE XP, INFINIDAT InfiniBox,  NetApp SolidFire/HCI

The following table describes network ports that must be opened to ensure proper communication with the following storage systems:

* DataCore SANsymphony
* Dell PowerStore
* Hitachi VSP/VSP One Block
* HPE XP
* INFINIDAT InfiniBox
* NetApp SolidFire/HCI

DataCore SANsymphony, Dell PowerStore, Hitachi VSP/VSP One Block, HPE XP, INFINIDAT InfiniBox, NEC Storage V Series,NetApp SolidFire/HCI

| From | To | Protocol | Port | Notes |
| Backup server | Storage system | TCP | 443 | Default command port used for communication with DataCore SANsymphony over HTTPS. |
| Backup proxy | Storage system | TCP | 3260 | Default iSCSI target port. |

Dell SC Series

The following table describes basic network ports that must be opened to ensure proper communication with Dell SC Series.

Dell SC Series

| From | To | Protocol | Port | Notes |
| Backup server | Dell SC Series storage system | TCP | 3033 | Default command port used for communication with Dell SC Series over HTTPS. |
| Backup proxy | Dell SC Series storage system | TCP | 3260 | Default iSCSI target port. |

Dell PowerMax

The following table describes basic network ports that must be opened to ensure proper communication with Dell PowerMax.

Dell PowerMax

| From | To | Protocol | Port | Notes |
| Backup server | Dell PowerMax storage system | TCP | 8443 | Default command port used for communication with Dell PowerMax over HTTPS. |
| Backup proxy | Dell PowerMax storage system | TCP | 3260 | Default iSCSI target port. |

Fujitsu ETERNUS DX/AF, IBM FlashSystem (formerly Spectrum Virtualize) Storage, NEC Storage M Series

The following table describes network ports that must be opened to ensure proper communication with the following storage systems:

* Fujitsu ETERNUS DX/AF
* IBM FlashSystem (formerly Spectrum Virtualize) Storage
* NEC Storage M Series

Fujitsu ETERNUS DX/AF, IBM FlashSystem (formerly Spectrum Virtualize) Storage, NEC Storage M Series

| From | To | Protocol | Port | Notes |
| Backup server | Storage system | TCP | 22 | Default command port used for communication with Fujitsu ETERNUS DX/AF over SSH. |
| Backup proxy | Storage system | TCP | 3260 | Default iSCSI target port. |

Pure Storage FlashArray, Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)

The following table describes network ports that must be opened to ensure proper communication with the following storage systems:

* Pure Storage FlashArray
* Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)

Pure Storage FlashArray, Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)

| From | To | Protocol | Port | Notes |
| Backup server | Storage system | TCP | 443 | Default command port used for communication with Pure Storage FlashArray over HTTPS. |
| Backup proxy | Storage system | TCP | 3260 | Default iSCSI target port. |
| TCP, UDP | 111, 2049 | Default NFS ports. Port 111 is used by the port mapper service. |

High Availability (HA) Cluster Components

The following table describes network ports that must be opened to ensure proper communication for the [high availability cluster feature](high_availability_infrastructure.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

High Availability (HA) Cluster Components

| From | To | Protocol | Port | Notes |
| Backup server (primary or standby) | PostgreSQL configuration database | TCP | 5432 | Port used for communication with PostgreSQL configuration database.  Note: The connection should be opened from the primary backup server to its configuration database, and from the standby backup server to its configuration database. |
| Primary backup server with PostgreSQL configuration database | Standby backup server with PostgreSQL configuration database | TCP | 8008, 8500 | Port used by PostgreSQL database service to manage the High Availability clusters. |

VMware vSphere Components

The following table describes network ports that must be opened to ensure proper communication for [VMware vSphere](vmware_vsphere.md) and [VMware Cloud Director](vcloud_director.md) protection. If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

VMware vSphere Components

| From | To | Protocol | Port | Notes |
| Communication with vCenter Servers | | | | |
| Backup server | vCenter Server | TCP | 443 | Port used for connections to vCenter Server.  Note: The backup server should have a direct connection to vCenter Server. HTTP/HTTPS proxy servers are not supported.  If you use VMware Cloud Director, make sure you open port 443 on underlying vCenter Servers. |
| Backup proxy | vCenter Server | TCP | 443 | Default VMware web service port that can be customized in vCenter settings. |
| Communication with ESXi Servers | | | | |
| Backup proxy | ESXi server | TCP | 902 | Default VMware port used for data transfer.  This port is not required for VMware Cloud on AWS. |
| TCP | 443 | Default VMware web service port that can be customized in ESXi host settings. Not required if vCenter connection is used.  This port is not required for VMware Cloud on AWS. |
| Backup server | ESXi server | TCP | 443 | Port used for connections to ESXi host.  This port is not required for VMware Cloud on AWS. |
| TCP | 902 | Port used for data transfer to ESXi host. It is also used during guest OS file recovery if you recover files from replicas.  This port is not required for VMware Cloud on AWS. |
| Communication with VMware Cloud Director | | | | |
| Backup server | VMware Cloud Director | TCP | 443 | Port used for connections to VMware Cloud Director.  Note: The backup server should have a direct connection to VMware Cloud Director. HTTP/HTTPS proxy servers are not supported. |

Microsoft Hyper-V Components

The following tables describe network ports that must be opened to ensure proper communication for components involved in the [Microsoft Hyper-V protection](ms_hyperv.md):

* [Virtualization servers](#hv_virt)
* [Off-host backup proxies](#hv_proxy)
* [Other backup infrastructure components](#hv_other)

If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Virtualization Servers

The following table describes network ports that must be opened for [virtualization servers](setup_add_server.md) involved in Microsoft Hyper-V protection.

Virtualization Servers

| From | To | Protocol | Port | Notes |
| Backup server | SCVMM | TCP | 8732 | Port used to communicate with the VMM server. |
| TCP | 445, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Port used by Veeam Installer Service. |
| TCP | 6162, 2500 to 3300 | Port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Hyper-V server | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6163 | Default port used to communicate with Veeam Hyper-V Integration Service. |
| TCP | 2179 | Port used to connect to VMs using the Virtual Machine Connection during [Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md) and [Recovery Verification for Microsoft Hyper-V](recovery_verification_overview_hv.md). |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Microsoft Windows/Linux-based backup repository | Hyper-V server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine) during restore operations.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Hyper-V server/Off-host backup proxy | Hyper-V server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine) during replication.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Microsoft SMB3 server (Hyper-V storage) | TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162, 2500-3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6163 | Default port used by the Hyper-V Integration Service. |

Off-Host Backup Proxies

The following table describes network ports that must be opened for [off-host backup proxies](offhost_backup_proxy.md) involved in Microsoft Hyper-V protection.

Off-Host Backup Proxies

| From | To | Protocol | Port | Notes |
| Communication with Off-Host Backup Proxies | | | | |
| Backup server | Hyper-V server/Off-host backup proxy | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6163 | Default port used by the Hyper-V Integration Service. |
| TCP | 49152 to 65535 | Dynamic RPC port range for Microsoft Windows 2008 and later. For more information, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us).  Note: If you use default Microsoft Windows firewall settings, you do not need to configure dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on how to configure RPC dynamic port allocation to work with firewalls, see [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Backup server | Off-host backup proxy | TCP | 6210 | Default port used by the Veeam Backup VSS Integration Service for taking a VSS snapshot during the SMB file share backup. |

Other Backup Infrastructure Components

The following table describes network ports that must be opened for other backup infrastructure components involved in Microsoft Hyper-V protection.

Other Backup Infrastructure Components

| From | To | Protocol | Port | Notes |
| SCVMM | Backup server | TCP | 443 | Port used for Veeam PowerShell Management Service authorization on the SCVMM server. |
| Hyper-V server/Off-host backup proxy | Gateway server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine) during replication.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Unstructured Data Backup Components

The following tables describe network ports that must be opened to ensure proper communication for components involved in the [unstructured data backup](unstructured_data_backup_infrastructure.md):

* [Unstructured data sources](#nas_shares_connections)
* [Cache repositories](#cache_repository_connections)
* [Repositories](#archive_repository_connections)
* [NDMP servers](#ndmp)
* [Other backup infrastructure components](#unstr_other)
* [Active Directory Domain Controllers](#unstructured_ad)

If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Unstructured Data Sources

The following table describes network ports that must be opened for the [unstructured data sources](unstructured_data_backup_infrastructure.md) involved in unstructured data backup.

Unstructured Data Sources

| From | To | Protocol | Port | Notes |
| Backup server | File server (Windows or Linux) | TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6210 | Default port used by the Veeam Backup VSS Integration Service for taking a VSS snapshot during the SMB file share backup (if Veeam Backup & Replication is installed on the Microsoft Windows machine). For more information, see [Microsoft Windows Services](services_and_components.md#win_services). |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup proxy | NAS filer (NetApp Data ONTAP or Lenovo ThinkSystem DM/DG Series storage system) | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Standard SMB port. |
| TCP, UDP | 635 | The default port used by the NetApp Data ONTAP storage controller. |
| TCP | 80, 443 | Ports used by NetApp SnapDiff when changed file tracking (CFT) is enabled. |
| Backup proxy | NAS filer (Dell PowerScale (formerly Isilon) or Nutanix Files storage system) | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service. |
| TCP | 445 | Standard SMB port. |
| TCP | 20048 | Port used for the NFS mountd access and service request monitoring. |
| Cache repository | NAS filer (NetApp Data ONTAP) | TCP | 80, 443, 2049 | Ports used by NetApp SnapDiff when changed file tracking (CFT) is enabled.  Port 2049 is required if the cache repository is a Linux machine. |
| File server (Windows or Linux),  Backup proxy,  Tape server | NFS share | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service. |
| File server (Windows or Linux),  Mount server,  Backup proxy,  Tape server | SMB share | TCP | 445 | Standard SMB port. |
| Mount server | SMB share | TCP | 137-139 | Standard CIFS ports range. |
| File server (Windows or Linux),  Backup proxy,  Tape server | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| File server (Windows or Linux),  Backup proxy,  Tape server | Amazon S3 object storage  (\*.amazontrust.com) | TCP | 80 | Port used to verify certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the file server, or backup proxy, or tape server can reach these verification endpoints. |
| File server (Windows or Linux),  Backup proxy,  Tape server | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | Port used to communicate with Microsoft Azure object storage.  The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| File server (Windows or Linux),  Backup proxy,  Tape server | Microsoft Azure object storage | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the file server, or backup proxy, or tape server can reach these verification endpoints. |
| File server (Windows or Linux),  Backup proxy,  Tape server | S3 compatible object storage | TCP | Depends on device configuration | Port used to communicate with S3 compatible object storage. |

Cache Repositories

The following table describes network ports that must be opened for [cache repositories](unstructured_data_backup_infrastructure.md) involved in the unstructured data backup.

Cache Repositories

| From | To | Protocol | Port | Notes |
| Backup server,  File server (Windows or Linux),  Backup proxy | Cache repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Cache repository | TCP | 6160 | Default ports used by Veeam Installer Service. |
| Backup server | Cache repository (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| Backup server | Old cache repository | TCP | 6162, 2500 to 3300 | Default range of ports used for metadata migration during cache repository change. For more information, see [Changing Cache Repository](unstructured_data_backup_in_object_storage.md#change_cache_repo). |
| Backup server | New cache repository | TCP | 6162, 2500 to 3300 | Default range of ports used for metadata migration during cache repository change. For more information, see [Changing Cache Repository](unstructured_data_backup_in_object_storage.md#change_cache_repo). |

Repositories

The following table describes network ports that must be opened for [primary, secondary or archive repositories](unstructured_data_backup_infrastructure.md) involved in the unstructured data backup.

Repositories

| From | To | Protocol | Port | Notes |
| Primary backup repository | Archive repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Cache repository | Primary or secondary backup repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

NDMP Servers

The following table describes network ports that must be opened for [NDMP servers](ndmp_servers.md) involved in the unstructured data backup.

NDMP Servers

| From | To | Protocol | Port | Notes |
| Gateway server | NDMP server | NDMP | 10000 | Default port used to manage the NMDP server.  Note: The port range used for data transfer depends on your NDMP server configuration. For more information, contact your hardware vendor. |

Other Backup Infrastructure Components

The following table describes network ports that must be opened for other backup infrastructure components involved in the unstructured data backup.

Other Backup Infrastructure Components

| From | To | Protocol | Port | Notes |
| File server (Windows or Linux),  Backup proxy | Backup server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Backup proxy | TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6210 | Default port used by the Veeam Backup VSS Integration Service for taking a VSS snapshot during the SMB file share backup (if Veeam Backup & Replication is installed on the Microsoft Windows machine). For more information, see [Microsoft Windows Services](services_and_components.md#win_services). |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Mount server | TCP | 443, 445, 6170 | Ports used during Instant File Share Recovery. |
| Cache repository | Gateway server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Active Directory Domain Controllers

The following table describes network ports that must be opened for Active Directory Domain Controllers involved in the unstructured data backup.

Active Directory Domain Controllers

| From | To | Protocol | Port | Notes |
| Backup proxy,  File server (Windows or Linux),  Backup proxy or  Tape server | Active Directory Domain Controllers | TCP | 389 | Port used for communication over LDAP and LDAPS protocols. |
| TCP | 88 | Port used for Kerberos authentication. |

Tape Device Support Components

The following table describes network ports that must be opened to ensure proper communication for the [tape device support](tape_device_support.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Tape Device Support Components

| From | To | Protocol | Port | Notes |
| Communication for Backup Server | | | | |
| Tape server | Backup server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Communication for Tape Servers | | | | |
| Backup server | Tape server | TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6166 | Controlling port for RPC calls. |
| Backup server | Tape server (Windows) | TCP | 445, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| Backup server | Tape server (Linux) | TCP | 22 | Default SSH port used as a control channel. |
| Communication for Backup Repositories and Gateway Servers | | | | |
| Tape server | Backup repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Tape server | Gateway server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Communication for Shares | | | | |
| Tape server | NFS share | TCP, UDP | 111, 2049 | Standard NFS ports. Port 111 is used by the port mapper service. |
| Tape server | SMB share | TCP | 445 | Standard SMB port. |

WAN Acceleration Components

The following table describes network ports that must be opened to ensure proper communication for the [WAN acceleration](wan_acceleration.md) used in backup copy jobs and replication jobs. If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

WAN Acceleration Components

| From | To | Protocol | Port | Notes |
| Communication with WAN Accelerators | | | | |
| Backup server | WAN accelerator  (source and target) | TCP | 445, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6164 | Controlling port for RPC calls. |
| Backup server | WAN accelerator  (target) | TCP | 6220 | Port used for traffic control (throttling) for tenants that use WAN accelerators.  This port is required only in the Veeam Cloud Connect infrastructure. |
| WAN accelerator (source and target) | WAN accelerator (source and target) | TCP | 6164 | Controlling port for RPC calls. |
| TCP | 6165 | Default port used for data transfer between WAN accelerators. Ensure this port is open in firewall between sites where WAN accelerators are deployed. |
| Communication with Backup Repositories | | | | |
| WAN accelerator (target) | Backup repository (target) | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is selected dynamically. |
| WAN accelerator (source) | Backup repository (source) | TCP | 2500 to 3300 | Default range of ports used as data transmission channels. For every TCP connection that a job uses, one port from this range is selected dynamically. |

Guest Processing Components

The following tables describe network ports that must be opened to ensure proper communication for components involved in the [guest processing](guest_processing.md):

* [Guest interaction proxies](#guest_proxy)
* [Protected workloads](#guest_workload)
* [Gateway servers](#guest_gateway)
* [Hypervisors](#guest_hypervisor)

If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest OS File Recovery](used_ports.md#guest_os_file_recovery).

Guest Interaction Proxies

The following table describes network ports that must be opened for [guest interaction proxies](guest_interaction_proxy.md) involved in the guest processing.

Guest Interaction Proxies

| From | To | Protocol | Port | Notes |
| Backup server | Guest interaction proxy | TCP | 445, 135 | Ports used for adding Windows VMs to managed servers using local administrator credentials. Note: Kerberos domain account with administrator privileges should be used. |
| TCP | 6160 | Port used for adding both Windows and Linux VMs to managed servers using a certificate-based authentication. Note: Deployment kit should be pre-installed on VMs. |
| TCP | 22 | Port used for adding Linux VMs to managed servers using SSH credentials. |
| Connections for Non-Persistent Runtime Components | | | | |
| Backup server | Guest interaction proxy | TCP | 6190 | Port used for communication of the backup server and backup infrastructure components with the non-persistent runtime components deployed inside the VM guest OS for application-aware processing and indexing. |

Protected Workloads

The following table describes network ports that must be opened for protected workloads involved in the guest processing.

Protected Workloads

| From | To | Protocol | Port | Notes |
| Connections for Non-Persistent Runtime Components | | | | |
| Guest interaction proxy | VM guest OS | TCP | 2500 to 3300 | Default range of ports used as transmission channels for log shipping. Note: These ports are NOT required in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| Guest interaction proxy | VM guest OS (Microsoft Windows) | TCP | 445, 135 | Port used to deploy the runtime coordination process on the VM guest OS. Note: These ports are NOT required in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6173 | Port used by the runtime process deployed inside the VM for guest OS interaction. Note: This port NOT required in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| Guest interaction proxy | VM guest OS (Linux) | TCP | 22 | Default SSH port used as a control channel. Note: This port NOT required in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| Connections for Persistent Agent Components | | | | |
| Backup server | VM guest OS (Linux) | TCP | 22 | Default SSH port used as a control channel during persistent agent installation. |
| TCP | 2500 to 3300 | Range of ports used only during the installation of the persistent agent.  Default range of ports used for communication with a guest OS. |
| Guest interaction proxy | VM guest OS (Linux) | TCP | 6160 | Default port used by Veeam Installer Service for Linux. |
| TCP | 6162 | Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| Guest interaction proxy | VM guest OS (Windows) | TCP | 6160, 11731 | Default ports used by Veeam Installer Service.  Port 11731 is used for failover if port 6160 is unavailable. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing and file system indexing. |

Gateway Servers

The following table describes network ports that must be opened for [gateway servers](gateway_server.md) involved in the guest processing.

Gateway Servers

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | Gateway server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Hypervisors

The following table describes network ports that must be opened for the hypervisors involved in the guest processing.

Hypervisors

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | ESXi server | TCP | 443 | Default port used for connections to ESXi host. This port must be opened to ensure proper communication with the non-persistent runtime components deployed inside the VM guest OS for application-aware processing and indexing. [For VMware vSphere earlier than 6.5] Not required if vCenter connection is used. In VMware vSphere versions 6.5 and later, port 443 is required by vCenter Web Services. |

Log Shipping Components

The following tables describe network ports that must be opened to ensure proper communication for components involved in log backup, such as [Microsoft SQL Server log backup](sql_backup.md), [Oracle log backup](oracle_backup.md) and [PostgreSQL WAL files backup](postgresql_backup.md):

* [Log shipping servers](#log_shipping_server_connections)
* [MS SQL guest OS](#sql_guest_os_connections)

* [Oracle guest OS](#oracle_guest_os_connections)
* [PostgreSQL guest OS](#postgresql_guest_os_connections)

* [Backup repositories](#log_repo)
* [Gateway servers](#log_gateway)
* [Hypervisors](#log_hypervisor)

If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest OS File Recovery](used_ports.md#guest_os_file_recovery).

Log Shipping Servers

The following table describes network ports that must be opened for [log shipping servers](log_shipping_server.md) involved in the log backup.

Log Shipping Servers

| From | To | Protocol | Port | Notes |
| Backup server | Log shipping server | TCP | 445, 135, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | Default port used by Veeam Installer Service. |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| Hyper-V host | Log shipping server (backup server) | TCP | 6162, 2500 to 3300 | Port or range of ports used for communication with the Hyper-V host and for transfer log backups.  These ports are required only if the log shipping server transfers data over PowerShell Direct. In this case, the backup server performs the role of the log shipping server.  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| VM guest OS (VM with MS SQL, Oracle, or PostgreSQL) | Log shipping server | TCP | 6162, 2500 to 3300 | Default port or range of ports used for communication with a log shipping server and transfer log backups. |

MS SQL Guest OS

The following table describes network ports that must be opened for MS SQL VM guest OS involved in the log backup.

MS SQL Guest OS

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | MS SQL VM guest OS | TCP | 445, 135, 137, 139 | [Non-persistent runtime components only] Ports used for deploying Veeam Backup & Replication components including Veeam Log Shipper runtime component.  These ports are not required:   * When working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. * If the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.   Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing. |
| TCP | 6160, 11731 | [Persistent agent components only] Default ports used by Veeam Installer Service.  Port 11731 is used for failover if port 6160 is unavailable. |
| TCP | 6167 | Port used by the Veeam Log Shipping Service for preparing the database and taking logs. |

Oracle Guest OS

The following table describes network ports that must be opened for Oracle VM guest OS involved in the log backup.

Oracle Guest OS

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | Oracle VM guest OS | TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| Guest interaction proxy | Oracle VM guest OS (Microsoft Windows) | TCP | 445, 135 | [Non-persistent runtime components only] Ports used for deploying Veeam Backup & Replication components including Veeam Log Shipper runtime component.  These ports are not required:   * When working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. * If the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.   Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6173 | Port used by the Veeam Guest Helper for guest OS processing |
| TCP | 6160, 11731 | [Persistent agent components only] Default ports used by Veeam Installer Service.  Port 11731 is used for failover if port 6160 is unavailable. |
| TCP | 6167 | Port used by the Veeam Log Shipping Service for preparing the database and taking logs. |
| Guest interaction proxy | Oracle VM guest OS (Linux) | TCP | 22 | [Non-persistent runtime components only] Default SSH port used as a control channel.  This port is NOT required when working in networkless mode over VMware VIX/vSphere Web Services or PowerShell Direct. |
| TCP | 6162 | [Persistent agent components only] Default Management Agent port. Required if it is used as a control channel instead of SSH. |

PostgreSQL Guest OS

The following table describes network ports that must be opened for PostgreSQL VM guest OS involved in the log backup.

PostgreSQL Guest OS

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | PostgreSQL VM guest OS | TCP | 22 | [Non-persistent runtime components only] Default SSH port used as a control channel.  This port is NOT required when working in networkless mode over vSphere Web Services. |
| TCP | 6162 | [Persistent agent components only] Default Management Agent port. Required if it is used as a control channel instead of SSH. |
| TCP | 2500 to 3300 | Default range of ports used for communication with a guest OS.  These ports are NOT required when working in networkless mode over vSphere Web Services. |

Backup Repositories

The following table describes network ports that must be opened for backup repositories involved in the log backup.

Backup Repositories

| From | To | Protocol | Port | Notes |
| Log shipping server | Backup repository | TCP | 6162 or 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| VM guest OS (VM with MS SQL, Oracle, or PostgreSQL) | Backup repository | TCP | 6162 or 2500 to 3300 | Default port or range of ports used for communication with a backup repository and transfer log backups. Should be opened if log shipping servers are not used in the infrastructure and the MS SQL server has a direct connection to the backup repository. |

Gateway Servers

The following table describes network ports that must be opened for [gateway servers](gateway_server.md) involved in the log backup.

Gateway Servers

| From | To | Protocol | Port | Notes |
| Log shipping server | Gateway server | TCP | 6162 or 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |

Hypervisors

The following table describes network ports that must be opened for hypervisors involved in the log backup.

Hypervisors

| From | To | Protocol | Port | Notes |
| Log shipping server (backup server) | Hyper-V host | TCP | 6162 or 2500 to 3300 | Port or range of ports used for communication with the Hyper-V host and for transfer log backups.  These ports are required only if the log shipping server transfers data over PowerShell Direct. In this case, the backup server performs the role of the log shipping server.  Note: The port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| Log shipping server | ESXi host | TCP | 443 | Default port used for communication with a log shipping server and transfer log backups over vSphere API. |

VMware CDP and Universal CDP Components

The following tables describe network ports that must be opened to ensure proper communication for components involved in the [universal CDP](uni_cdp_infrastructure.md) and [VMware CDP](cdp_infrastructure.md):

* [CDP proxies](#cdp_proxy)
* [Virtualization servers](#cdp_hypervisor)
* [Source workloads](#cdp_workload)
* [Backup server](#cdp_backup)

If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

CDP Proxies

The following table describes network ports that must be opened for the [CDP proxies](cdp_proxy.md) involved in the universal CDP and VMware CDP.

CDP Proxies

| From | To | Protocol | Port | Notes |
| ESXi host (source) | CDP proxy (source) | TCP | 33032 | [For regular CDP] Default port used as a transmission channel to the source CDP proxy. |
| Source workload | CDP proxy (source) | TCP | 33032 | [For universal CDP] Default port used as a transmission channel to the source CDP proxy. |
| CDP proxy (source) | CDP proxy (target) | TCP | 33033 | Default port used as a transmission channel to the target CDP proxy. |
| Backup server | CDP proxy (source and target) | TCP | 6182 | Port used as a control channel. |

Virtualization Servers

The following table describes network ports that must be opened for the virtualization servers involved in the universal CDP and VMware CDP.

Virtualization Servers

| From | To | Protocol | Port | Notes |
| Communication with vCenter Servers | | | | |
| CDP proxy (source and target) | vCenter Server (VMware CDP — source and target;  universal CDP — target) | TCP | 443 | Default VMware web service port that can be customized in vCenter settings. Used during initial synchronization and restore operations. |
| Backup server | vCenter Server (VMware CDP — source and target;  universal CDP — target) | TCP | 443 | Port used as a control channel. |
| Communication with ESXi Hosts | | | | |
| ESXi host (source) | ESXi host (source) | TCP | 33036 | [For VMware CDP] Port used on the source ESXi host for communication between CDP components over HTTPS without HTTP Reverse Proxy. |
| CDP proxy (source and target) | ESXi host (VMware CDP — source and target;  universal CDP — target) | TCP | 902 | Default VMware port used for data transfer. Used during initial synchronization and restore operations. |
| ESXi host (target) | ESXi host (target) | TCP | 33036 | Port used on the target ESXi host for communication between CDP components over HTTPS without HTTP Reverse Proxy. |
| Backup server | ESXi host  (VMware CDP — source and target;  universal CDP — target) | TCP | 443 | Port used as a control channel. |
| Backup server | ESXi host (VMware CDP — source and target;  universal CDP — target) | TCP | 33035 | Port used to install I/O filter components on ESXi hosts. |
| CDP proxy (target) | ESXi host (target) | TCP | 33032 | Default port used as a transmission channel to the target ESXi host. |

Source Workloads

The following table describes network ports that must be opened for the source workloads involved in the universal CDP and VMware CDP.

Source Workloads

| From | To | Protocol | Port | Notes |
| Backup server | Source workload | TCP | 33050 | [For universal CDP] Port used on the source workload for communication between the Veeam CDP Coordinator Service and Veeam CDP Agent Service over HTTPS. |

Backup Server

The following table describes network ports that must be opened for the backup server involved in the universal CDP and VMware CDP.

Backup Server

| From | To | Protocol | Port | Notes |
| CDP proxy  (source and target),  ESXi host  (VMware CDP — source and target; universal CDP — target),  vCenter Server  (VMware CDP — source and target; universal CDP — target) | Backup server | TCP | 33034 | Port used for communication with Veeam CDP Coordinator Service: |
| vCenter Server,  ESXi host | Backup server | TCP | 33035 | Port used to install I/O filter components on the source and target vCenter servers and ESXi hosts. |

Data Recovery Components

The following section describes ports that must be opened to ensure proper communication for different data recovery operations:

* [Guest OS file recovery](#guest_os_file_recovery)
* [SureBackup](#surebackup)
* [SureReplica recovery verification](#surereplica)
* [Application item restore](#item_restore)
* [Restore to Amazon EC2 and restore to Google Cloud](#restore_to_amazon)
* [Restore to Microsoft Azure](#restore_to_azure)
* [Instant Recovery to Microsoft Azure](#instant_recovery_to_azure)

Guest OS File Recovery Components

The following tables describe network ports that must be opened to ensure proper communication for components involved in the [guest OS file recovery](guest_file_recovery.md):

* [Helper appliances](#helper_appliance)
* [Helper hosts](#helper_host)
* [Guest OS](#guest_os_recovery_connections)
* [Backup repositories](#guest_repo)
* [Virtualization servers](#guest_hypervisor)
* [Veeam Update servers](#guest_veeam)

If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Helper Appliances

The following table describes network ports that must be opened for the [helper appliances](guest_file_recovery.md) involved in guest OS file recovery.

Helper Appliances

| From | To | Protocol | Port | Notes |
| Backup server,  Mount server | Helper appliance | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| VM guest OS (Linux/Unix) | Helper appliance | TCP | 21 | Default port used for protocol control messages if FTP server is enabled. |

Helper Hosts

The following table describes network ports that must be opened for the [helper hosts](guest_file_recovery.md) involved in guest OS file recovery.

Helper Hosts

| From | To | Protocol | Port | Notes |
| Backup server,  Mount server | Helper host | TCP | 22 | Default SSH port used as a control channel. |
| TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Guest OS

The following table describes network ports that must be opened for the VM guest OS involved in guest OS file recovery.

Guest OS

| From | To | Protocol | Port | Notes |
| Helper appliance,  Helper host | VM guest OS (Linux/Unix) | TCP | 2500 to 3300 | Default range of ports used for communication with a VM guest OS. |
| Helper appliance | VM guest OS (Linux/Unix) | TCP | 20 | Default port used for data transfer if FTP server is enabled. |
| Backup server | VM guest OS (Linux/Unix) | TCP | 22 | Default SSH port used as a control channel. |
| Mount server | VM guest OS (Microsoft Windows) | TCP | 445, 135 | Required to deploy the runtime coordination process on the VM guest OS. |
| TCP | 6160, 11731 | Default ports used by Veeam Installer Service.  Port 11731 is used for failover if port 6160 is unavailable. |
| TCP | 6162 | Port used by the Veeam Transport Service for file-level restore. |
| Backup server | VM guest OS | TCP | 2500 to 3300 | Default range of ports used for communication with a VM guest OS. |

Backup Repositories

The following table describes network ports that must be opened for the backup repositories involved in guest OS file recovery.

Backup Repositories

| From | To | Protocol | Port | Notes |
| Mount server,  Helper appliance,  Helper host | Backup repository | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Virtualization Servers

The following table describes network ports that must be opened for the virtualization servers involved in guest OS file recovery.

Virtualization Servers

| From | To | Protocol | Port | Notes |
| Mount server | vCenter server | TCP | 443 | Default port used for connections to the vCenter server. |
| Mount server | ESXi host | TCP | 443 | Default port used for connections to the ESXi host. |
| Helper appliance,  Helper host | ESXi host | TCP | 443 | Default port used for connections to the ESXi host if restore is performed over VIX API/vSphere Web Services.  [For VMware vSphere earlier than 6.5] Not required if vCenter connection is used. In VMware vSphere versions 6.5 and later, port 443 is required by vSphere Web Services. |

Veeam Update Servers

The following table describes network ports that must be opened for the Veeam servers involved in guest OS file recovery.

Veeam Update Servers

| From | To | Protocol | Port | Notes |
| Mount server | Veeam Signature Update Server  (avupdate.veeam.com) | TCP | 443 | Default port used by Veeam Threat Hunter to download information about new malware signatures from the Veeam Signature Update Server over HTTPS. |

SureBackup Components

The following table describes network ports that must be opened to ensure proper communication for [SureBackup](surebackup_hiw.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

SureBackup Components

| From | To | Protocol | Port | Notes |
| Communication with Proxy Appliances | | | | |
| Backup server | Proxy appliance | TCP | 443 | Port used for communication with the proxy appliance in the virtual lab. |
| Communication with VMs | | | | |
| Backup server | Applications on VMs in the virtual lab | — | — | Application-specific ports to perform port probing test. For example, to verify a DC, Veeam Backup & Replication probes port 389 for a response. |
| Internet-facing proxy server | VMs in the virtual lab | TCP | 8080 | Port used to let VMs in the virtual lab access the Internet. |
| Communication with Hypervisors | | | | |
| Mount server running vPower NFS Service | ESXi server | TCP | 443 | Default port used for connections to ESXi host. |
| Backup repository  Gateway server working with backup repository | Hyper-V server | TCP | 6162, 2500 to 3300 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine) during SureBackup.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

SureReplica Recovery Verification Components

The following table describes network ports that must be opened to ensure proper communication for [SureReplica](surereplica_hiw.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

SureReplica Recovery Verification Components

| From | To | Protocol | Port | Notes |
| Communication with Proxy Appliances | | | | |
| Backup server | Proxy appliance | TCP | 443 | Port used for communication with the proxy appliance in the virtual lab. |
| Communication with VMs | | | | |
| Backup server | Applications on VMs in the virtual lab | — | — | Application-specific ports to perform port probing test. For example, to verify a DC, Veeam Backup & Replication probes port 389 for a response. |
| Internet-facing proxy server | VMs in the virtual lab | TCP | 8080 | Port used to let VMs in the virtual lab access the Internet. |

Application Item Restore

The following tables describe network ports that must be opened to ensure proper communication for components involved in the [application-item restore](restore_veeam_explorers.md):

* [VMs with Microsoft Active Directory Domain Controller](#ad)
* [VMs with Microsoft Exchange Server](#ex)
* [VMs with Microsoft SQL Server](#sql)

If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Microsoft Active Directory Domain Controller

The following table describes network ports that must be opened for the Microsoft Active Directory VM involved in application-item restore.

Microsoft Active Directory Domain Controller

| From | To | Protocol | Port | Notes |
| Backup server | Microsoft  Active Directory VM guest OS | TCP | 135 | Port used for communication between the domain controller and backup server. |
| TCP, UDP | 389 | Port used for LDAP connections. |
| TCP | 636, 3268, 3269 | Ports used for LDAP connections. |

Microsoft Exchange Server

The following table describes network ports that must be opened for the Microsoft Exchange Server involved in application-item restore.

Microsoft Exchange Server

| From | To | Protocol | Port | Notes |
| Backup server | Microsoft Exchange 2003/2007 CAS Server | TCP | 80, 443 | Ports used for WebDAV connections. |
| Backup server | Microsoft Exchange 2010/2013/2016/2019 CAS Server | TCP | 443 | Port used for Microsoft Exchange Web Services Connections. |

Microsoft SQL Server

The following table describes network ports that must be opened for the Microsoft SQL Server involved in application-item restore.

Microsoft SQL Server

| From | To | Protocol | Port | Notes |
| Backup server | Microsoft SQL VM guest OS | TCP | 1433, 1434 and other | Ports used for communication with the Microsoft SQL Server installed inside the VM.  Port numbers depends on configuration of your Microsoft SQL server. For more information, see [this Microsoft article](https://msdn.microsoft.com/en-us/library/cc646023.aspx#BKMK_ssde). |
| UDP | 1434 | Port used by the Microsoft SQL Server Browser service.  For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/sql/tools/configuration-manager/sql-server-browser-service). |

Restore to Amazon EC2 and Restore to Google Cloud Components

The following table describes network ports that must be opened to ensure proper communication for [restore to Amazon EC2](restore_amazon.md) and [restore to Google Compute Engine](restore_google.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Restore to Amazon EC2 and Restore to Google Cloud Components

| From | To | Protocol | Port | Notes |
| Backup server or  Backup repository | Helper appliance | TCP | 22 | Port used as a communication channel to the helper appliance. |
| TCP | 443 | Default redirector port. You can change the port in helper appliance settings. For details, see the Specify Helper Appliance section in [Restore to Amazon EC2](restore_amazon_proxy.md) and [Restore to Google Cloud](restore_google_proxy_appliance.md). |

Restore to Microsoft Azure Components

The following table describes network ports that must be opened to ensure proper communication for [Restore to Microsoft Azure](restore_azure_hiw.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Restore to Microsoft Azure Components

| From | To | Protocol | Port | Notes |
| Communication with Microsoft | | | | |
| Backup server | Microsoft Azure Resource Manager service  (https://management.azure.com) | TCP | 443 | Port used for Azure resources management and deployment. |
| Backup server | Microsoft Entra ID  (https://login.microsoftonline.com) | TCP | 443 | Port used for Entra ID authentication. |
| Backup server | Microsoft Azure storage accounts (blob storage)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used for restored Windows-based VM conversion. Restored disks are temporarily mounted to the backup server.  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Backup server | Azure Windows VM agent distribution location  (go.microsoft.com, aka.ms, github.com, objects.githubusercontent.com) | TCP | 443 | Port used to install the Azure Windows VM agent on the restored VM.  Consider that the URLs used are subject to change. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-windows#install-the-azure-windows-vm-agent). |
| Backup server | Certificate verification endpoints | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server can reach these verification endpoints. |
| Communication with Helper Appliances | | | | |
| Backup server | Helper appliance | TCP | 22 | Port used by default as a communication channel to the helper appliance when restoring Linux workloads.  This port can be changed during helper appliance deployment. For details, see [Managing Helper Appliances](restore_azure_linux.md). |
| Communication with Proxy Appliances | | | | |
| Backup server or backup repository | Azure restore proxy appliance | TCP | 443 | Default management and data transport port required for communication with the Azure restore proxy appliance. The port must be accessible from the backup server and backup repository storing VM backups.  This port can be changed in the settings of the Azure Restore proxy appliance. For details, see [Specify Credentials and Transport Port](restore_azure_proxy_credentials.md). |

Instant Recovery to Microsoft Azure Components

The following table describes network ports that must be opened to ensure proper communication for [Instant Recovery to Microsoft Azure](instant_recovery_to_azure.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Instant Recovery to Microsoft Azure Components

| From | To | Protocol | Port | Notes |
| Communication with Microsoft | | | | |
| Backup server | Microsoft Azure Resource Manager service  (https://management.azure.com) | TCP | 443 | Port used for Azure Resources management and deployment.  Service Tag: AzureResourceManager |
| Backup server | Microsoft Azure storage account (Veeam packages upload)  (<storage-account>.queue.core.windows.net, <storage-account>.queue.storage.azure.net) | TCP | 443 | Port used to deliver Veeam components from the backup server to the temporary Azure VM used to create templates of Instant Recovery to Azure helper appliances.  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Microsoft Azure storage account (Veeam packages upload)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used to deliver Veeam components from the backup server to the temporary VM,  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Backup server,  Instant Recovery for Azure helper appliance | Microsoft Azure storage account (message queues)  (<storage-account>.queue.core.windows.net, <storage-account>.queue.storage.azure.net) | TCP | 443 | Port used for communication using Azure Message queues.  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Microsoft Azure storage account (message queues)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used for communication with the backup server through Azure Message queues,  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Instant Recovery for Azure helper appliance | Microsoft Azure storage account (backup repository) / Veeam Data Cloud Vault (backup repository)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Port used to access backups.  Consider that the <storage-account> part of the address must be replaced with the ID of your storage vault. You can find the storage vault ID in the Storage Vaults > Vault ID section in Veeam Data Cloud Vault. For more information, see the [Managing Storage Vaults](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#viewing-storage-vault-details) section in the Veeam Data Cloud User Guide.  Service Tag: Storage |
| Backup server,  Instant Recovery for Azure helper appliance | Microsoft Entra ID  (https://login.microsoftonline.com) | TCP | 443 | Port used for Entra ID authentication to access storage accounts and message queues.  Service Tag: AzureActiveDirectory |
| Backup server,  Instant Recovery for Azure helper appliance,  Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Certificate verification endpoints | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server, helper appliance and temporary VMs can reach these verification endpoints. |
| Instant Recovery for Azure helper appliance | Azure Windows VM Agent Distribution location  (go.microsoft.com, aka.ms, github.com, objects.githubusercontent.com) | TCP | 443 | Port used to install the Azure Windows VM agent on the restored Windows VM.  Consider that these URLs are subject to change. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-windows#install-the-azure-windows-vm-agent). |
| Instant Recovery for Azure helper appliance | Azure Instance Metadata Service endpoint  (http://169.254.169.254) | TCP | 80 | Port used for Entra ID authentication to access storage accounts and message queues and other purposes:  Service Tag: AzureActiveDirectory |
| Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Ubuntu Azure repository  (http://azure.archive.ubuntu.com/ubuntu/) | TCP | 80 | Port used to install prerequisite packages. |
| Communication with Helper Appliances | | | | |
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

* [Veeam Plug-In for AWS](https://helpcenter.veeam.com/docs/vbaws/guide/ports.html?ver=10)
* [Veeam Plug-In for Microsoft Azure](https://helpcenter.veeam.com/docs/vbazure/guide/ports.html?ver=8.1)
* [Veeam Plug-In for Google Cloud](https://helpcenter.veeam.com/docs/vbgc/guide/ports.html?ver=7)

Kasten

* [Veeam Plug-In for Kasten Connections](https://helpcenter.veeam.com/docs/vbr/kasten_integration/used_ports.html?ver=13)

Virtualization Platforms

* [Veeam Backup for Oracle Linux Virtualization Manager and Red Hat Virtualization Connections](https://helpcenter.veeam.com/docs/vbrhv/userguide/used_ports.html?ver=7)
* [Veeam Plug-In for Nutanix AHV Connections](https://helpcenter.veeam.com/docs/vbahv/userguide/used_ports.html?ver=9)
* [Veeam Plug-In for Proxmox VE Connections](https://helpcenter.veeam.com/docs/vbproxmoxve/userguide/used_ports.html?ver=3)

Nutanix Mine with Veeam

* [Nutanix Mine with Veeam Connections](https://helpcenter.veeam.com/docs/nutanixmine/userguide/used_ports.html?ver=40)


