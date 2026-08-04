---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html"
last_updated: "2026"
product_version: "13.1.0.411"
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
| Web UI and Host Management console PC,  Veeam Backup & Replication console,  Mount server,  Veeam Infrastructure Appliance | Backup server | TCP | 443 | — |
| Web UI and Host Management console PC | Backup server | TCP | 10443 | Required by Veeam Software Appliances only. |
| Web UI PC | Backup server | TCP | 80 | Optional. Redirects HTTP requests to HTTPS so the web UI can be opened without typing the https:// scheme explicitly.  You can disable redirecting and free this port for another software as described in [this Veeam KB article](https://www.veeam.com/kb4868). |
| Remote access PC | Backup server | TCP | 22 | Required by Veeam Software Appliances only. |
| UDP, TCP | 3389 | Required for RDP access. UDP connection is optional, used if available. |
| Veeam Backup & Replication console | Backup server | TCP | 9420 | [For console version 12.3.2 P1 (build 12.3.2.4165)] Port used by the Veeam Backup & Replication console to communicate with the backup server for console automatic update. |
| Backup proxy,  Backup repository (Linux),  Backup repository (Microsoft Windows),  Gateway server,  Mount server | Backup server | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| REST client | Backup server | TCP | 9419 | Required for direct Public REST API access. |
| REST client | Backup server | TCP | 443 | Public REST API access proxied through the WebUI backend. |

Veeam Servers and Services

The following table describes basic network ports that must be opened to ensure proper communication with Veeam servers and services.

Veeam Servers and Services

| From | To | Protocol | Port | Notes |
| Communication with Update Repositories | | | | |
| Backup server,  Veeam Infrastructure Appliance | Veeam Update Repository  (repository.veeam.com) | TCP | 443 or 80 | Required by Veeam Software and Infrastructure Appliances only. |
| Backup server,  Veeam Infrastructure Appliance | Veeam Update Repository (local mirror)  (<localmirrorrepository.domain>) | TCP | 443 or 80 | Required by Veeam Software and Infrastructure Appliances only.  Consider that the address must be replaced with the actual URL of your mirror repository. |
| Backup server | Veeam License Update Server  (vbr.butler.veeam.com, autolk.veeam.com) | TCP | 443 | — |
| Backup server | Veeam License Update Server CRL distribution points  (\*.ss2.us, \*.amazontrust.com) | TCP | 80 | Certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server can reach these verification endpoints. |
| Backup server | Veeam Update Notification Server  (dev.veeam.com, vbrad.butler.veeam.com, vbrce.butler.veeam.com) | TCP | 443 | — |
| Communication with Veeam AI Assistant | | | | |
| Veeam Backup & Replication console,  Web UI and Host Management console PC | Veeam AI Assistant  (rest-ai.veeam.com) | TCP | 443 | — |
| Communication with Veeam ONE | | | | |
| Backup server | Veeam ONE Server | TCP | 2741, 2805 | Required for Veeam ONE only. |
| Backup server | Veeam ONE Web Services Server | TCP | 1239 | Required for Veeam ONE only. |

Databases and External Services

The following table describes basic network ports that must be opened to ensure proper communication with databases and different external servers such as mail servers, time servers and others.

Databases and External Services

| From | To | Protocol | Port | Notes |
| Communication with Configuration Databases | | | | |
| Backup server | PostgreSQL configuration database | TCP | 5432 | Required for Microsoft Windows-based backup servers with an external configuration database. |
| Backup server | Microsoft SQL Server hosting the Veeam Backup & Replication configuration database | TCP | 1433 | Required for Microsoft Windows-based backup servers with an external SQL Server configuration database. Depending on your configuration, alternative ports may need to be open. For more information, see [Microsoft Docs](https://msdn.microsoft.com/en-us/library/cc646023%28v%3Dsql.120%29.aspx#BKMK_ssde). |
| Communication with Mail Servers for Notifications | | | | |
| Backup server | SMTP server | TCP | 25 | — |
| TCP | 587 | Required if SSL is enabled. |
| Backup server | Gmail REST API  (gmail.googleapis.com, accounts.google.com, gstatic.com) | TCP | 443 | — |
| Backup server | Microsoft Graph REST API  (graph.microsoft.com, login.microsoftonline.com) | TCP | 443 | — |
| Communication with Time Servers | | | | |
| Backup server,  Veeam Infrastructure Appliance | NTP server | UDP | 123 | Required by Veeam Software and Infrastructure Appliances only. |
| Backup server,  Veeam Infrastructure Appliance | NTS server | UDP | 123 | Required by Veeam Software and Infrastructure Appliances only. |
| TCP | 4460 |
| Other Communication | | | | |
| Any backup infrastructure component | DNS server | UDP, TCP | 53 | — |
| Backup server | Certificate Revocation Lists | TCP | 80 or 443 | The specific CRL endpoint that must be connected to depends on the CA that issued the certificate.  You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server can reach these verification endpoints. |
| Backup server | Key Management System (KMIP) server | TCP | 5696 | — |
| Backup server | Syslog server | TCP, UDP | 514 | — |
| TCP | 6514 | — |
| Backup server,  Veeam Infrastructure Appliance | Active Directory Domain Controllers | TCP | 636, 3268, 3269 | — |
| UDP, TCP | 389 |
| UDP, TCP | 445, 139 | — |
| UDP, TCP | 88 | Required for Kerberos authentication when Veeam Software or Infrastructure Appliances are domain-joined. |
| Communication for SMB (CIFS) Repositories | | | | |
| Gateway server or  Backup proxy | Active Directory Domain Controllers | TCP | 389 | — |
| TCP | 88 | Required for Kerberos authentication when Veeam Software or Infrastructure Appliances are domain-joined. |

Veeam Infrastructure Appliances

The following table describes basic network ports that must be opened to ensure proper communication with [Veeam Infrastructure Appliances](linux_infrastructure.md).

|  |
| --- |
| Note |
| The following ports are required by all Veeam Infrastructure Appliances. You must also open additional ports based on the role you have assigned to the Veeam Infrastructure Appliance. They can be found on this page in the relevant section for the role. For example, [Backup Proxy](#proxy) or [Gateway Server](#gateway).  For more information on the roles that can be assigned to a Veeam Infrastructure Appliance, see [Considerations and Limitations](linux_infrastructure_appliance_byb.md). |

Veeam Infrastructure Appliances

| From | To | Protocol | Port | Notes |
| Backup server | Veeam Infrastructure Appliance | TCP | 443 | — |
| Web UI PC,  Host Management console PC | Veeam Infrastructure Appliance | TCP | 10443 | — |
| Remote access PC | Veeam Infrastructure Appliance | TCP | 22 | — |

Backup Proxies

The following table describes basic network ports that must be opened to ensure proper communication with [backup proxies](proxies.md). For more information about ports that must be opened for backup repositories, see [Backup Repositories](#backup_repos).

Backup Proxies

| From | To | Protocol | Port | Notes |
| Backup server,  Backup proxy,  Backup repository,  Mount server,  Gateway server  (for on-premises backup repository in case of Veeam Data Cloud Vault)  On-premises backup repository | Backup proxy / Backup proxy (direct connection) | TCP | 6162, 2500 to 3300 | [For Linux backup proxy] You can specify a different port while adding Linux servers to the Veeam Backup & Replication infrastructure. You can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on the Linux server.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Backup proxy (Microsoft Windows) | TCP | 445, 137, 139 | These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | — |
| Backup server | Backup proxy (Linux) | TCP | 22 | — |
| TCP | 6160 | — |

Gateway Servers

The following table describes basic network ports that must be opened to ensure proper communication with [gateway servers](gateway_server.md). For more information about ports that must be opened for backup repositories, see [Backup Repositories](#backup_repos).

Gateway Servers

| From | To | Protocol | Port | Notes |
| Backup server,  Backup proxy,  Hyper-V server/Off-host backup proxy,  On-premises backup repository,  Gateway server (for on-premises backup repository in case of Veeam Data Cloud Vault)  VM Guest OS | Gateway server / Gateway server for Veeam Data Cloud Vault | TCP | 6162, 2500 to 3300 | [For Linux gateway server] You can specify a different port while adding Linux servers to the Veeam Backup & Replication infrastructure. You can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on the Linux server.    The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Gateway server (Microsoft Windows) | TCP | 445, 137, 139 | These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | — |
| Backup server | Gateway server (Linux) | TCP | 22 | — |
| TCP | 6160 | — |
| Mount server running vPower NFS Service | Gateway server working with backup repository | TCP | 6162, 2500 to 3300 | Required for Instant Recovery, SureBackup, and Linux file-level recovery.  Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine).  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

VM guest OS (Linux/Unix)

Helper appliance

* [VMs with Microsoft Active Directory Domain Controller](#ad)
* [VMs with Microsoft Exchange Server](#ex)
* [VMs with Microsoft SQL Server](#sql)

Veeam Backup for Microsoft Entra ID

Veeam Cloud Connect

Veeam Cloud Connect

| From | To | Protocol | Port | Notes |
| Mount server running vPower NFS Service | Backup repository | TCP | 6162, 2500 to 3300 | Required for Instant Recovery, SureBackup, and Linux file-level recovery.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Veeam Backup & Replication console,  Backup proxy,  Hyper-V server/Off-host backup proxy | Backup repository | TCP | 6162, 2500 to 3300 | [For Linux repository] You can specify a different port while adding Linux servers to the Veeam Backup & Replication infrastructure. You can specify a different port only if there is no previously installed Veeam Transport Service or Veeam Data Mover components on the Linux server.    The port range 2500-3300 is used for failover if the 6162 port is unavailable. |

Microsoft Windows/Linux-Based Backup Repositories

The following table describes basic network ports that must be opened to ensure proper communication with Microsoft Windows/Linux-based backup repositories. You must also open ports described in [Backup Repository Common Ports](#repo_common).

Microsoft Windows/Linux-Based Backup Repositories

| From | To | Protocol | Port | Notes |
| Backup server | Backup repository | TCP | 6160 | — |
| Backup server | Backup repository (Microsoft Windows) | TCP | 445, 137, 139 | These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| Backup server | Backup repository (Linux) | TCP | 22 | — |
| Source backup repository | Target backup repository | TCP | 6162, 2500 to 3300 | Required for backup copy jobs.  If the backup copy job utilizes WAN accelerators, make sure that [ports specific for WAN accelerators](used_ports.md#wan) are opened. |

NFS Backup Repositories, SMB Backup Repositories, Dell Data Domain System, and HPE StoreOnce

The following table describes basic network ports that must be opened to ensure proper communication with [NFS shares added as backup repositories](nfs_share.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

NFS Backup Repositories, SMB Backup Repositories, Dell Data Domain System, and HPE StoreOnce

| From | To | Protocol | Port | Notes |
| Gateway server or  Backup proxy | NFS backup repository | TCP, UDP | 111, 2049 | — |
| Gateway server or  Backup proxy | NFS backup repository (NFS v3) | TCP, UDP | mountd\_port, statd\_port, lockd\_port | These ports can be assigned statically. |
| Gateway server or  Backup proxy | SMB (CIFS) backup repository (Microsoft Windows) | TCP | 445 | Port used as a transmission channel from the gateway server to the target SMB (CIFS) backup repository if a gateway server is specified explicitly in SMB (CIFS) backup repository settings. |
| Backup server,  Gateway server | Dell Data Domain | TCP | 111 | Port used to assign a random port for the mountd service used by NFS and DDBOOST. Mountd service port can be statically assigned. |
| TCP | 2049 | Main port used by NFS. Can be modified using the ‘nfs set server-port’ command. Command requires SE mode. |
| TCP | 2052 | Main port used by NFS MOUNTD. Can be modified using the 'nfs set mountd-port' command in SE mode. |
| Backup server or  Gateway server | HPE StoreOnce | TCP | 9387 | — |
| TCP | 9388 | — |

ExaGrid, Quantum DXi, Fsas ETERNUS CS800, Infinidat InfiniGuard

The following table describes basic network ports that must be opened to ensure proper communication with storage systems added as deduplicating appliances:

* [Nutanix Mine with Veeam Connections](https://helpcenter.veeam.com/docs/nutanixmine/userguide/used_ports.html?ver=40)
* [Quantum DXi](deduplicating_appliance_quantum.md)
* [Fsas ETERNUS CS800](fujitsu.md)
* [Infinidat InfiniGuard](infinidat_infiniguard.md)

You must also open ports described in [Backup Repository Common Ports](#repo_common).

ExaGrid, Quantum DXi, Fsas ETERNUS CS800, Infinidat InfiniGuard

| From | To | Protocol | Port | Notes |
| Backup server | Deduplicating appliance | TCP | 22 | — |
| TCP | 6162, 2500 to 3300, 6160 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Veeam Data Cloud Vault

The following table describes network ports and endpoints that must be opened to ensure proper communication with Veeam Data Cloud Vault. You must also open ports described in [Backup Repository Common Ports](#repo_common).

Veeam Data Cloud Vault

| From | To | Protocol | Port | Notes |
| Backup server,  Backup proxy (direct connection)/  Gateway server/  Instant Recovery to Azure helper appliance | Veeam Data Cloud Vault  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Consider that the <storage-account> part of the address must be replaced with the ID of your storage vault. You can find the storage vault ID in the Storage Vaults > Vault ID section in Veeam Data Cloud Vault. For more information, see the [Managing Storage Vaults](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#viewing-storage-vault-details) section in the Veeam Data Cloud User Guide. |
| Backup server,  Backup proxy (direct connection)/  Gateway server/  Instant Recovery to Azure helper appliance | Veeam Data Cloud Vault CRL distribution points | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server, or proxy, or gateway server, or helper appliance can reach these verification endpoints. |
| Backup server | Microsoft Entra ID  (login.microsoftonline.com, login.windows.net) | TCP | 443 | — |

Object Storage Repositories

The following table describes network ports and endpoints that must be opened to ensure proper communication with [object storage repositories](object_storage_repository.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

Object Storage Repositories

| From | To | Protocol | Port | Notes |
| Backup server | Smart Object Storage API (SOSAPI) compatible S3 object storage | TCP | 443 | — |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Amazon S3 CRL distribution points  (\*.amazontrust.com) | TCP | 80 | Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or gateway server, or helper appliance can reach these verification endpoints. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | S3 compatible object storage | TCP | Depends on device configuration | — |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Microsoft Azure CRL distribution points | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or gateway server, or helper appliance can reach these verification endpoints. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Google Cloud CRL distribution points  (storage.googleapis.com) | TCP | 443 | All cloud endpoints are specified in [this Google article](https://cloud.google.com/storage/docs/request-endpoints). |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | Google Cloud CRL distribution points  (ocsp.pki.goog, pki.goog, crl.pki.goog) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or gateway server, or helper appliance can reach these verification endpoints. |
| Backup proxy (direct connection)/  Gateway server or backup server/  Instant Recovery to Azure helper appliance | IBM Cloud object storage | TCP | Depends on device configuration | — |

Scale-Out Backup Repositories

The following table describes basic network ports that must be opened to ensure proper communication with [scale-out backup repositories](backup_repository_sobr.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

Scale-Out Backup Repositories

| From | To | Protocol | Port | Notes |
| Source extent | Target extent | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Target extent | Source extent | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |

External Repositories

The following table describes basic network ports that must be opened to ensure proper communication with [external repositories](external_repository.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

External Repositories

| From | To | Protocol | Port | Notes |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Amazon S3 CRL distribution points  (\*.amazontrust.com) | TCP | 80 | Port used to verify certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or backup server, or helper appliance can reach these verification endpoints. |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Microsoft Azure CRL distribution points | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or backup server, or helper appliance can reach these verification endpoints. |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Google Cloud CRL distribution points  (storage.googleapis.com) | TCP | 443 | All cloud endpoints are specified in [this Google article](https://cloud.google.com/storage/docs/request-endpoints). |
| Gateway server/  Backup server/  Instant Recovery to Azure helper appliance | Google Cloud CRL distribution points  (ocsp.pki.goog, pki.goog, crl.pki.goog) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy, or backup server, or helper appliance can reach these verification endpoints. |

Archive Object Storage Repositories

The following table describes basic network ports that must be opened to ensure proper communication with object storage repositories used as a part of [Archive Tier](archive_tier.md). You must also open ports described in [Backup Repository Common Ports](#repo_common).

Archive Object Storage Repositories

| From | To | Protocol | Port | Notes |
| Gateway server or  Backup server | Amazon EC2 helper appliance | TCP | 443 | If you use Amazon S3 Glacier object storage, the gateway server should have direct connection to AWS service endpoints. HTTP/HTTPS proxy servers are not supported.  If there is no gateway server selected, the backup server will be used as a gateway server. |
| TCP | 22 | — |
| Gateway server or  Backup server | Microsoft Azure proxy appliance | TCP | 443 | If there is no gateway server selected, the backup server will be used as a gateway server. |
| TCP | 22 | — |
| Amazon EC2 helper appliance | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| Amazon EC2 helper appliance | Amazon S3 CRL distribution points  (\*.amazontrust.com) | TCP | 80 | Port used to verify the certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the helper appliance can reach these verification endpoints. |
| Microsoft Azure proxy appliance | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Microsoft Azure proxy appliance | Microsoft Azure CRL distribution points | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the proxy appliance can reach these verification endpoints. |

Mount Servers

The following table describes basic network ports that must be opened to ensure proper communication with mount servers. The mount server can be used in different data protection operations. For more information, see [Mount Servers](mount_server.md) and [Veeam vPower NFS Service](vpower_nfs_service.md).

Mount Servers

| From | To | Protocol | Port | Notes |
| Veeam Backup & Replication console | Mount server | TCP | 6162, 2500 to 3300 | Required for guest OS file-level restore. These ports are not required if the mount server is located on the same machine as the console.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Mount server | TCP | 445 | Not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component. |
| TCP | 6160 | — |
| TCP | 6162, 2500 to 3300 | — |
| TCP | 6170 | — |
| Connections of Mount Servers with vPower NFS Service | | | | |
| Backup server | Mount server running vPower NFS Service | TCP | 6160 | — |
| TCP | 6161 | — |
| ESXi host | Mount server running vPower NFS Service | TCP UDP | 111 | — |
| TCP UDP | 1058+ or 1063+ | Default mount port. The port depends on where the vPower NFS Service is located:   * 1058+: If the vPower NFS Service is located on the backup server. * 1063+: If the vPower NFS Service is located on a separate Microsoft Windows machine.   If port 1058/1063 is occupied, the succeeding port numbers will be used. |
| TCP UDP | 2049+ | — |
| Backup repository or  Gateway server working with backup repository | Mount server running vPower NFS Service | TCP | 6162, 2500 to 3300 | Required for Instant Recovery, SureBackup or Linux file-level recovery.  The port range 2500-3300 is used for failover if port 6162 is unavailable. |

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
| Backup server | Dell Unity XT, Unity storage system | TCP | 443 | — |
| Backup proxy | Dell Unity XT, Unity storage system | TCP | 3260 | Required for iSCSI connectivity. |
| TCP, UDP | 111, 2049 | Required for NFS connectivity. |

Dell PowerScale (Formerly Isilon) Storage

The following table describes basic network ports that must be opened to ensure proper communication with Dell PowerScale (Formerly Isilon).

Dell PowerScale (Formerly Isilon) Storage

| From | To | Protocol | Port | Notes |
| Backup server | Dell PowerScale storage system | TCP | 8080 | — |
| Backup proxy | Dell PowerScale storage system | TCP, UDP | 111, 2049 | Required for NFS connectivity. |
| TCP | 445 | Required for SMB connectivity. |

HPE 3PAR StoreServ Storage

The following table describes basic network ports that must be opened to ensure proper communication with HPE 3PAR StoreServ.

HPE 3PAR StoreServ Storage

| From | To | Protocol | Port | Notes |
| Backup server | HPE 3PAR StoreServ storage system | TCP | 8008 | Required for communication over HTTP. |
| TCP | 8080 | Required for communication over HTTPS. |
| TCP | 22 | Required for communication over SSH. |
| Backup proxy | HPE 3PAR StoreServ storage system | TCP | 3260 | Required for iSCSI connectivity. |

HPE Alletra Storage MP B10000, Alletra 9000, Primera Storage

The following table describes basic network ports that must be opened to ensure proper communication with HPE Alletra Storage MP B10000, Alletra 9000, Primera.

HPE Alletra Storage MP B10000, Alletra 9000, Primera Storage

| From | To | Protocol | Port | Notes |
| Backup server | HPE Alletra Storage MP B10000,  Alletra 9000, Primera storage system | TCP | 443 | Required for communication over HTTPS. |
| TCP | 22 | Required for communication over SSH. |
| Backup proxy | HPE Alletra Storage MP B10000, Alletra 9000, Primera storage system | TCP | 3260 | Required for iSCSI connectivity. |
| Backup proxy | HPE Alletra Storage MP B10000, Alletra 9000 | TCP | 4420, 8009 | Required for NVMe-oF connectivity. |

HPE Alletra 5000, Alletra 6000, Nimble Storage

The following table describes basic network ports that must be opened to ensure proper communication with HPE Alletra 5000, Alletra 6000, Nimble.

HPE Alletra 5000, Alletra 6000, Nimble Storage

| From | To | Protocol | Port | Notes |
| Backup server | HPE Alletra 5000, Alletra 6000/Nimble storage system | TCP | 5392 | — |
| Backup proxy | HPE Alletra 5000, Alletra 6000/Nimble storage system | TCP | 3260 | Required for iSCSI connectivity. |

Lenovo ThinkSystem DM/DG Series Storage, NetApp ONTAP Storage

The following table describes network ports that must be opened to ensure proper communication with the following storage systems:

* Lenovo ThinkSystem DM/DG Series
* NetApp ONTAP

Lenovo ThinkSystem DM/DG Series Storage, NetApp ONTAP Storage

| From | To | Protocol | Port | Notes |
| Backup server | Storage system | TCP | 80 | Required for communication over HTTP. |
| TCP | 443 | Required for communication over HTTPS. |
| Backup proxy | Storage system | TCP, UDP | 111, 2049, 635 | Required for NFS connectivity. |
| TCP | 445 | Required for SMB connectivity. |
| TCP | 3260 | Required for iSCSI connectivity. |

Nutanix Files Storage

The following table describes basic network ports that must be opened to ensure proper communication with Nutanix Files.

Nutanix Files Storage

| From | To | Protocol | Port | Notes |
| Backup server | Nutanix Files storage system | TCP | 9440 | — |
| Backup proxy | Nutanix Files storage system | TCP, UDP | 111, 2049, 20048 | Required for NFS connectivity. |
| TCP | 445 | Required for SMB connectivity. |

Universal Storage API Integrated System

The following tables describe network ports that must be opened to ensure proper communication with Universal Storage API integrated systems:

* [DataCore SANsymphony](#DataCore), [Dell PowerMax](#dell_powermax), [Fsas ETERNUS EP300](#fsas), [Hitachi VSP/VSP One Block](#vsp), [HPE XP](#xp), [INFINIDAT InfiniBox](#infinidat), [NEC Storage V Series](#necv), [NetApp SolidFire/HCI](#solidfire)
* [Dell SC Series](#DellEMC)
* [Dell PowerStore](#dell_powerstore)
* [Fsas ETERNUS DX/AF](#fujitsu), [IBM FlashSystem (formerly Spectrum Virtualize) Storage](#ibm), [NEC Storage M Series](#necm)
* [Everpure FlashArray](#pure), [Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)](#WesternDigital)

DataCore SANsymphony, Dell PowerStore, Fsas ETERNUS EP300, Hitachi VSP/VSP One Block, HPE XP, INFINIDAT InfiniBox, NEC Storage V Series, NetApp SolidFire/HCI

The following table describes network ports that must be opened to ensure proper communication with the following storage systems:

* DataCore SANsymphony
* Dell PowerStore
* Fsas ETERNUS EP300
* Hitachi VSP/VSP One Block
* HPE XP
* INFINIDAT InfiniBox
* NEC Storage V Series
* NetApp SolidFire/HCI

DataCore SANsymphony, Dell PowerStore, Fsas ETERNUS EP300, Hitachi VSP/VSP One Block, HPE XP, INFINIDAT InfiniBox, NEC Storage V Series, NetApp SolidFire/HCI

| From | To | Protocol | Port | Notes |
| Backup server | Storage system | TCP | 443 | Required for communication over HTTPS. |
| Backup proxy | Storage system | TCP | 3260 | Required for iSCSI connectivity. |

Dell SC Series

The following table describes basic network ports that must be opened to ensure proper communication with Dell SC Series.

Dell SC Series

| From | To | Protocol | Port | Notes |
| Backup server | Dell SC Series storage system | TCP | 3033 | Required for communication over HTTPS. |
| Backup proxy | Dell SC Series storage system | TCP | 3260 | Required for iSCSI connectivity. |

Dell PowerMax

The following table describes basic network ports that must be opened to ensure proper communication with Dell PowerMax.

Dell PowerMax

| From | To | Protocol | Port | Notes |
| Backup server | Dell PowerMax storage system | TCP | 8443 | Required for communication over HTTPS. |
| Backup proxy | Dell PowerMax storage system | TCP | 3260 | Required for iSCSI connectivity. |

Fsas ETERNUS DX/AF, IBM FlashSystem (formerly Spectrum Virtualize) Storage, NEC Storage M Series

The following table describes network ports that must be opened to ensure proper communication with the following storage systems:

* Fsas ETERNUS DX/AF
* IBM FlashSystem (formerly Spectrum Virtualize) Storage
* NEC Storage M Series

Fsas ETERNUS DX/AF, IBM FlashSystem (formerly Spectrum Virtualize) Storage, NEC Storage M Series

| From | To | Protocol | Port | Notes |
| Backup server | Storage system | TCP | 22 | Required for communication over SSH. |
| Backup proxy | Storage system | TCP | 3260 | Required for iSCSI connectivity. |

Everpure FlashArray, Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)

The following table describes network ports that must be opened to ensure proper communication with the following storage systems:

* Everpure FlashArray
* Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)

Everpure FlashArray, Tintri IntelliFlash (formerly Western Digital IntelliFlash, Tegile)

| From | To | Protocol | Port | Notes |
| Backup server | Storage system | TCP | 443 | Required for communication over HTTPS. |
| Backup proxy | Storage system | TCP | 3260 | Required for iSCSI connectivity. |
| TCP, UDP | 111, 2049 | Required for NFS connectivity. |

High Availability (HA) Cluster Components

The following table describes network ports that must be opened to ensure proper communication for the [high availability cluster feature](high_availability_infrastructure.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

High Availability (HA) Cluster Components

| From | To | Protocol | Port | Notes |
| Backup server (primary or standby) | PostgreSQL configuration database | TCP | 5432 | The connection should be opened from the primary backup server to its configuration database, and from the standby backup server to its configuration database. |
| Backup Server Cluster member | Backup Server Cluster member | TCP | 8008, 8500 | — |

VMware vSphere Components

The following table describes network ports that must be opened to ensure proper communication for [VMware vSphere](vmware_vsphere.md) and [VMware Cloud Director](vcloud_director.md) protection. If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

VMware vSphere Components

| From | To | Protocol | Port | Notes |
| Communication with vCenter Servers | | | | |
| Backup server | vCenter Server | TCP | 443 | The backup server should have a direct connection to vCenter Server. HTTP/HTTPS proxy servers are not supported.  If you use VMware Cloud Director, make sure you open port 443 on underlying vCenter Servers. |
| Backup proxy | vCenter Server | TCP | 443 | This port can be customized in vCenter settings. |
| Communication with ESXi Servers | | | | |
| Backup proxy | ESXi server | TCP | 902 | This port is not required for VMware Cloud on AWS. |
| TCP | 443 | Not required if a vCenter connection or VMware Cloud on AWS is used. |
| Backup server | ESXi server | TCP | 443 | This port is not required for VMware Cloud on AWS. |
| TCP | 902 | This port is not required for VMware Cloud on AWS. |
| Communication with VMware Cloud Director | | | | |
| Backup server | VMware Cloud Director | TCP | 443 | The backup server should have a direct connection to VMware Cloud Director. HTTP/HTTPS proxy servers are not supported. |

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
| Backup server | SCVMM | TCP | 8732 | — |
| TCP | 445, 137, 139 | These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | — |
| TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Hyper-V server | TCP | 445, 135, 137, 139 | These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | — |
| TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6163 | — |
| TCP | 2179 | Required for [Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md) and [Recovery Verification for Microsoft Hyper-V](recovery_verification_overview_hv.md). |
| TCP | 49152 to 65535 | If you use default Microsoft Windows firewall settings, you do not need to configure these dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on RPC dynamic port allocation, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us) and [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Microsoft Windows/Linux-based backup repository | Hyper-V server | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Hyper-V server/Off-host backup proxy | Hyper-V server | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Microsoft SMB3 server (Hyper-V storage) | TCP | 6160 | — |
| TCP | 6162, 2500-3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6163 | — |

Off-Host Backup Proxies

The following table describes network ports that must be opened for [off-host backup proxies](offhost_backup_proxy.md) involved in Microsoft Hyper-V protection.

Off-Host Backup Proxies

| From | To | Protocol | Port | Notes |
| Communication with Off-Host Backup Proxies | | | | |
| Backup server | Hyper-V server/Off-host backup proxy | TCP | 445, 135, 137, 139 | These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | — |
| TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6163 | — |
| TCP | 49152 to 65535 | If you use default Microsoft Windows firewall settings, you do not need to configure these dynamic RPC ports. During setup, Veeam Backup & Replication automatically creates a firewall rule for the runtime process. If you use firewall settings other than default ones or application-aware processing fails with the "RPC function call failed" error, you need to configure dynamic RPC ports. For more information on RPC dynamic port allocation, see [this Microsoft KB article](https://support.microsoft.com/kb/929851/en-us) and [this Microsoft KB article](https://support.microsoft.com/en-us/help/154596/how-to-configure-rpc-dynamic-port-allocation-to-work-with-firewalls). |
| Backup server | Off-host backup proxy | TCP | 6210 | Required for VSS snapshot during SMB file share backup. |

Other Backup Infrastructure Components

The following table describes network ports that must be opened for other backup infrastructure components involved in Microsoft Hyper-V protection.

Other Backup Infrastructure Components

| From | To | Protocol | Port | Notes |
| SCVMM | Backup server | TCP | 443 | — |
| Hyper-V server/Off-host backup proxy | Gateway server | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |

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
| Backup server | File server (Windows or Linux) | TCP | 6160 | — |
| TCP | 6210 | Required by Microsoft Windows-based backup servers for VSS snapshot during SMB file share backup. |
| TCP | 6162, 2500 to 3300 | — |
| Backup proxy | NAS filer (NetApp Data ONTAP or Lenovo ThinkSystem DM/DG Series storage system) | TCP, UDP | 111, 2049 | Required for NFS. |
| TCP | 445 | REquired for SMB. |
| TCP, UDP | 635 | — |
| TCP | 80, 443 | Required by NetApp SnapDiff when changed file tracking (CFT) is enabled. |
| Backup proxy | NAS filer (Dell PowerScale (formerly Isilon) or Nutanix Files storage system) | TCP, UDP | 111, 2049 | Required for NFS. |
| TCP | 445 | REquired for SMB connections. |
| TCP | 20048 | Required for NFS. |
| Cache repository | NAS filer (NetApp Data ONTAP) | TCP | 80, 443, 2049 | Required by NetApp SnapDiff when changed file tracking (CFT) is enabled.  Port 2049 is only required if the cache repository is a Linux machine. |
| File server (Windows or Linux),  Backup proxy,  Tape server | NFS share | TCP, UDP | 111, 2049 | Required for NFS. |
| File server (Windows or Linux),  Mount server,  Backup proxy,  Tape server | SMB share | TCP | 445 | REquired for SMB. |
| Mount server | SMB share | TCP | 137-139 | Required for CIFS. |
| File server (Windows or Linux),  Backup proxy,  Tape server | Amazon S3 object storage  (\*.amazonaws.com, \*.amazonaws.com.cn) | TCP | 443 | Port used to communicate with Amazon S3 object storage.  The endpoint used by the connection depends on the region:   * \*.amazonaws.com is used for the Global and Government regions. * \*.amazonaws.com.cn is used for the China region.   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| File server (Windows or Linux),  Backup proxy,  Tape server | Amazon CRL distribution points  (\*.amazontrust.com) | TCP | 80 | Port used to verify certificate status.  Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. You can find the actual list of addresses in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the file server, or backup proxy, or tape server can reach these verification endpoints. |
| File server (Windows or Linux),  Backup proxy,  Tape server | Microsoft Azure object storage  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net, <storage-account>.blob.core.chinacloudapi.cn, <storage-account>.blob.core.usgovcloudapi.net) | TCP | 443 | The endpoints used by the connection depend on the region:   * <storage-account>.blob.core.windows.net is used for the Global region. * <storage-account>.blob.storage.azure.net is used for the Global region. * <storage-account>.blob.core.chinacloudapi.cn is used for the China region. * <storage-account>.blob.core.usgovcloudapi.net is used for the Government region.   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| File server (Windows or Linux),  Backup proxy,  Tape server | Microsoft Azure CRL distribution points | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the file server, or backup proxy, or tape server can reach these verification endpoints. |
| File server (Windows or Linux),  Backup proxy,  Tape server | S3 compatible object storage | TCP | Depends on device configuration | — |

Cache Repositories

The following table describes network ports that must be opened for [cache repositories](unstructured_data_backup_infrastructure.md) involved in the unstructured data backup.

Cache Repositories

| From | To | Protocol | Port | Notes |
| Backup server,  File server (Windows or Linux),  Backup proxy | Cache repository | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Cache repository | TCP | 6160 | — |
| Backup server | Cache repository (Linux) | TCP | 22 | — |
| Old cache repository | New cache repository | TCP | 2500 to 3300 | Required for metadata migration during cache repository change. For more information, see [Changing Cache Repository](unstructured_data_backup_in_object_storage.md#change_cache_repo). |
| New cache repository | Old cache repository | TCP | 2500 to 3300 | Required for used for metadata migration during cache repository change. For more information, see [Changing Cache Repository](unstructured_data_backup_in_object_storage.md#change_cache_repo). |

Repositories

The following table describes network ports that must be opened for [primary, secondary or archive repositories](unstructured_data_backup_infrastructure.md) involved in the unstructured data backup.

Repositories

| From | To | Protocol | Port | Notes |
| Primary backup repository | Archive repository | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Cache repository | Primary or secondary backup repository | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |

NDMP Servers

The following table describes network ports that must be opened for [NDMP servers](ndmp_servers.md) involved in the unstructured data backup.

NDMP Servers

| From | To | Protocol | Port | Notes |
| Gateway server | NDMP server | NDMP | 10000 | The additional port range used for data transfer depends on your NDMP server configuration. For more information, contact your hardware vendor. |

Other Backup Infrastructure Components

The following table describes network ports that must be opened for other backup infrastructure components involved in the unstructured data backup.

Other Backup Infrastructure Components

| From | To | Protocol | Port | Notes |
| File server (Windows or Linux),  Backup proxy | Backup server | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Backup proxy | TCP | 6160 | — |
| TCP | 6210 | Required by Microsoft Windows-based backup servers for VSS snapshot during SMB file share backup. |
| TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Backup server | Mount server | TCP | 443, 445, 6170 | Required for Instant File Share Recovery. |
| Cache repository | Gateway server | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Active Directory Domain Controllers

The following table describes network ports that must be opened for Active Directory Domain Controllers involved in the unstructured data backup.

Active Directory Domain Controllers

| From | To | Protocol | Port | Notes |
| Backup proxy,  File server (Windows or Linux),  Backup proxy or  Tape server | Active Directory Domain Controllers | TCP | 389 | — |
| TCP | 88 | Required for Kerberos authentication. |

Tape Device Support Components

The following table describes network ports that must be opened to ensure proper communication for the [tape device support](tape_device_support.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Tape Device Support Components

| From | To | Protocol | Port | Notes |
| Communication for Backup Server | | | | |
| Tape server | Backup server | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Communication for Tape Servers | | | | |
| Backup server | Tape server | TCP | 6160 | — |
| TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| TCP | 6166 | — |
| Backup server | Tape server (Windows) | TCP | 445, 137, 139 | Ports used for deploying Veeam Backup & Replication components. These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| Backup server | Tape server (Linux) | TCP | 22 | — |
| Communication for Backup Repositories and Gateway Servers | | | | |
| Tape server | Backup repository | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Tape server | Gateway server | TCP | 6162, 2500 to 3300 | — |
| Communication for Shares | | | | |
| Tape server | NFS share | TCP, UDP | 111, 2049 | — |
| Tape server | SMB share | TCP | 445 | — |

WAN Acceleration Components

The following table describes network ports that must be opened to ensure proper communication for the [WAN acceleration](wan_acceleration.md) used in backup copy jobs and replication jobs. If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

WAN Acceleration Components

| From | To | Protocol | Port | Notes |
| Communication with WAN Accelerators | | | | |
| Backup server | WAN accelerator  (source and target) | TCP | 445, 137, 139 | These ports are not required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  Note: 137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | — |
| TCP | 6162 | Default port used by Veeam Transport Service (Veeam Data Mover Service if Veeam Backup & Replication is installed on the Microsoft Windows machine). |
| TCP | 6164 | — |
| Backup server | WAN accelerator  (target) | TCP | 6220 | Required for traffic control (throttling) for tenants that use WAN accelerators.  This port is required only in the Veeam Cloud Connect infrastructure. |
| WAN accelerator (source and target) | WAN accelerator (source and target) | TCP | 6164 | — |
| TCP | 6165 | This port must be open between sites where WAN accelerators are deployed. |
| Communication with Backup Repositories | | | | |
| WAN accelerator (target) | Backup repository (target) | TCP | 2500 to 3300 | — |
| WAN accelerator (source) | Backup repository (source) | TCP | 2500 to 3300 | — |

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
| Backup server | Guest interaction proxy | TCP | 445, 135 | Required for adding Windows machines to managed servers using local administrator credentials.  Kerberos domain account with administrator privileges should be used. |
| TCP | 6160 | Required for adding both Windows and Linux machines to managed servers using a certificate-based authentication.  Deployment kit should be pre-installed on VMs. |
| TCP | 22 | Required for adding Linux machines to managed servers using SSH credentials. |
| Connections for Non-Persistent Runtime Components | | | | |
| Backup server | Guest interaction proxy | TCP | 6190 | — |

Protected Workloads

The following table describes network ports that must be opened for protected workloads involved in the guest processing.

Protected Workloads

| From | To | Protocol | Port | Notes |
| Connections for Non-Persistent Runtime Components | | | | |
| Guest interaction proxy | VM guest OS (Microsoft Windows) | TCP | 445, 135 | NOT required in networkless mode over vSphere Web Services or PowerShell Direct. |
| TCP | 6173 | NOT required in networkless mode over vSphere Web Services or PowerShell Direct. |
| Guest interaction proxy | VM guest OS (Linux) | TCP | 22 | NOT required in networkless mode over vSphere Web Services or PowerShell Direct. |
| Connections for Persistent Agent Components | | | | |
| Backup server | VM guest OS (Linux) | TCP | 22 | — |
| TCP | 2500 to 3300 | — |
| Guest interaction proxy | VM guest OS (Linux) | TCP | 6160 | — |
| TCP | 6162 | Required if it is used as a control channel instead of SSH. |
| Guest interaction proxy | VM guest OS (Windows) | TCP | 6160, 11731 | Port 11731 is used for failover if port 6160 is unavailable. |
| TCP | 6173 | — |

Gateway Servers

The following table describes network ports that must be opened for [gateway servers](gateway_server.md) involved in the guest processing.

Gateway Servers

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | Gateway server | TCP | 6162, 2500 to 3300 | Port range 2500-3300 is used for failover if port 6162 is unavailable. |

Hypervisors

The following table describes network ports that must be opened for specific hypervisors involved in the guest processing.

Hypervisors

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | ESXi server | TCP | 443 | Required for connections to ESXi host.  This port must be opened to ensure proper communication with the non-persistent runtime components deployed inside the VM guest OS for application-aware processing and indexing.  [For VMware vSphere earlier than 6.5] Not required if vCenter connection is used. In VMware vSphere versions 6.5 and later, port 443 is required by vCenter Web Services. |

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
| Backup server | Log shipping server | TCP | 445, 135, 137, 139 | NOT required if the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.  137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6160 | — |
| TCP | 6162 | — |
| Hyper-V host | Log shipping server (backup server) | TCP | 6162, 2500 to 3300 | Required only if the log shipping server transfers data over PowerShell Direct. In this case, the backup server performs the role of the log shipping server.  Port range 2500 - 3300 is optional. You can use it for failover if port 6162 is unavailable. |
| VM guest OS (VM with MS SQL, Oracle, or PostgreSQL) | Log shipping server | TCP | 6162, 2500 to 3300 | — |

MS SQL Guest OS

The following table describes network ports that must be opened for MS SQL VM guest OS involved in the log backup.

MS SQL Guest OS

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | MS SQL VM guest OS | TCP | 445, 135, 137, 139 | For non-persistent runtime components only.  These ports are not required:   * When working in networkless mode over /vSphere Web Services or PowerShell Direct. * If the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component.   137 and 139 are legacy ports. If your backup infrastructure components do not use SMB 1.0, they are not required. |
| TCP | 6173 | — |
| TCP | 6160, 11731 | For persistent agent components only.  Port 11731 is used for failover if port 6160 is unavailable. |
| TCP | 6167 | — |

Oracle Guest OS

The following table describes network ports that must be opened for Oracle VM guest OS involved in the log backup.

Oracle Guest OS

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | Oracle VM guest OS (Microsoft Windows) | TCP | 445, 135 | For non-persistent runtime components only.  These ports are not required:   * When working in networkless mode over vSphere Web Services or PowerShell Direct. * If the [Veeam Deployment Kit](deployment_kit.md) is installed on the backup infrastructure component. |
| TCP | 6173 | — |
| TCP | 6160, 11731 | For persistent agent components only.  Port 11731 is used for failover if port 6160 is unavailable. |
| TCP | 6167 | — |
| Guest interaction proxy | Oracle VM guest OS (Linux) | TCP | 2500 to 3300 | NOT required when working in networkless mode over /vSphere Web Services or PowerShell Direct. |
| TCP | 22 | For non-persistent runtime components only.  NOT required when working in networkless mode over vSphere Web Services. |
| TCP | 6162 | For persistent agent components only.  Required if it is used as a control channel instead of SSH. |

PostgreSQL Guest OS

The following table describes network ports that must be opened for PostgreSQL VM guest OS involved in the log backup.

PostgreSQL Guest OS

| From | To | Protocol | Port | Notes |
| Guest interaction proxy | PostgreSQL VM guest OS | TCP | 22 | For non-persistent runtime components only.  NOT required when working in networkless mode over vSphere Web Services. |
| TCP | 6162 | For persistent agent components only.  Required if it is used as a control channel instead of SSH. |
| TCP | 2500 to 3300 | NOT required when working in networkless mode over vSphere Web Services. |

Backup Repositories

The following table describes network ports that must be opened for backup repositories involved in the log backup.

Backup Repositories

| From | To | Protocol | Port | Notes |
| Log shipping server | Backup repository | TCP | 6162 or 2500 to 3300 | Port range 2500-3300 is used for failover if port 6162 is unavailable. |
| VM guest OS (VM with MS SQL, Oracle, or PostgreSQL) | Backup repository | TCP | 6162 or 2500 to 3300 | Required if log shipping servers are not used in the infrastructure and the MS SQL server has a direct connection to the backup repository. |

Gateway Servers

The following table describes network ports that must be opened for [gateway servers](gateway_server.md) involved in the log backup.

Gateway Servers

| From | To | Protocol | Port | Notes |
| Log shipping server | Gateway server | TCP | 6162 or 2500 to 3300 | Port range 2500-3300 is used for failover if port 6162 is unavailable. |

Hypervisors

The following table describes network ports that must be opened for specific hypervisors involved in the log backup.

Hypervisors

| From | To | Protocol | Port | Notes |
| Log shipping server (backup server) | Hyper-V host | TCP | 6162 or 2500 to 3300 | Required only if the log shipping server transfers data over PowerShell Direct. In this case, the backup server performs the role of the log shipping server.  Port range 2500-3300 is used for failover if port 6162 is unavailable. |
| Log shipping server | ESXi host | TCP | 443 | — |

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
| ESXi host (source) | CDP proxy (source) | TCP | 33032 | Required for regular CDP. |
| Source workload | CDP proxy (source) | TCP | 33032 | Required for universal CDP. |
| CDP proxy (source) | CDP proxy (target) | TCP | 33033 | — |
| Backup server | CDP proxy (source and target) | TCP | 6182 | — |

Virtualization Servers

The following table describes network ports that must be opened for the virtualization servers involved in the universal CDP and VMware CDP.

Virtualization Servers

| From | To | Protocol | Port | Notes |
| Communication with vCenter Servers | | | | |
| CDP proxy (source and target) | vCenter Server (VMware CDP — source and target;  universal CDP — target) | TCP | 443 | Required for during initial synchronization and restore operations. The port used can be customized in your vCenter settings. |
| Backup server | vCenter Server (VMware CDP — source and target;  universal CDP — target) | TCP | 443 | — |
| Communication with ESXi Hosts | | | | |
| ESXi host (source) | ESXi host (source) | TCP | 33036 | Required for VMware CDP. This port is used by the source ESXi host for communication between CDP components over HTTPS without HTTP Reverse Proxy. |
| CDP proxy (source and target) | ESXi host (VMware CDP — source and target;  universal CDP — target) | TCP | 902 | Required for during initial synchronization and restore operations. The port used can be customized in your vCenter settings. |
| ESXi host (target) | ESXi host (target) | TCP | 33036 | Required for communication between CDP components over HTTPS without HTTP Reverse Proxy. |
| Backup server | ESXi host  (VMware CDP — source and target;  universal CDP — target) | TCP | 443 | — |
| Backup server | ESXi host (VMware CDP — source and target;  universal CDP — target) | TCP | 33035 | — |
| CDP proxy (target) | ESXi host (target) | TCP | 33032 | — |

Source Workloads

The following table describes network ports that must be opened for the source workloads involved in the universal CDP and VMware CDP.

Source Workloads

| From | To | Protocol | Port | Notes |
| Backup server | Source workload | TCP | 33050 | [For universal CDP] Port used on the source workload for communication between the Veeam CDP Coordinator Service and Veeam CDP Agent Service over HTTPS. |

Backup Server

The following table describes network ports that must be opened for the backup server involved in the universal CDP and VMware CDP.

Backup Server

| From | To | Protocol | Port | Notes |
| CDP proxy  (source and target),  ESXi host  (VMware CDP — source and target; universal CDP — target),  vCenter Server  (VMware CDP — source and target; universal CDP — target) | Backup server | TCP | 33034 | — |
| vCenter Server,  ESXi host | Backup server | TCP | 33035 | — |

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
| Backup server,  Mount server | Helper appliance | TCP | 22 | — |
| TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |
| VM guest OS (Linux/Unix) | Helper appliance | TCP | 21 | Required if FTP server is enabled. |

Helper Hosts

The following table describes network ports that must be opened for the [helper hosts](guest_file_recovery.md) involved in guest OS file recovery.

Helper Hosts

| From | To | Protocol | Port | Notes |
| Backup server,  Mount server | Helper host | TCP | 22 | — |
| TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Guest OS

The following table describes network ports that must be opened for the VM guest OS involved in guest OS file recovery.

Guest OS

| From | To | Protocol | Port | Notes |
| Helper appliance,  Helper host | VM guest OS (Linux/Unix) | TCP | 2500 to 3300 | — |
| Helper appliance | VM guest OS (Linux/Unix) | TCP | 20 | Required if FTP server is enabled. |
| Backup server | VM guest OS (Linux/Unix) | TCP | 22 | — |
| Mount server | VM guest OS (Microsoft Windows) | TCP | 445, 135 | — |
| TCP | 6160, 11731 | Port 11731 is used for failover if port 6160 is unavailable. |
| TCP | 6162 | Required for file-level restore. |
| Backup server | VM guest OS | TCP | 2500 to 3300 | — |

Backup Repositories

The following table describes network ports that must be opened for the backup repositories involved in guest OS file recovery.

Backup Repositories

| From | To | Protocol | Port | Notes |
| Mount server,  Helper appliance,  Helper host | Backup repository | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |

Virtualization Servers

The following table describes network ports that must be opened for the virtualization servers involved in guest OS file recovery.

Virtualization Servers

| From | To | Protocol | Port | Notes |
| Mount server | vCenter server | TCP | 443 | — |
| Mount server | ESXi host | TCP | 443 | — |
| Helper appliance,  Helper host | ESXi host | TCP | 443 | Required if restore performed over vSphere Web Services.  [For VMware vSphere earlier than 6.5] Not required if vCenter connection is used. In VMware vSphere versions 6.5 and later, port 443 is required by vSphere Web Services. |

Veeam Update Servers

The following table describes network ports that must be opened for the Veeam servers involved in guest OS file recovery.

Veeam Update Servers

| From | To | Protocol | Port | Notes |
| Mount server | Veeam Signature Update Server  (avupdate.veeam.com) | TCP | 443 | — |

SureBackup Components

The following table describes network ports that must be opened to ensure proper communication for [SureBackup](surebackup_hiw.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

SureBackup Components

| From | To | Protocol | Port | Notes |
| Communication with Proxy Appliances | | | | |
| Backup server | Proxy appliance | TCP | 443 | — |
| Communication with VMs | | | | |
| Backup server | Applications on VMs in the virtual lab | — | — | Application-specific ports to perform port probing test. For example, to verify a DC, Veeam Backup & Replication probes port 389 for a response. |
| Internet-facing proxy server | VMs in the virtual lab | TCP | 8080 | Required to allow VMs in a virtual lab access the Internet. |
| Communication with Hypervisors | | | | |
| Mount server running vPower NFS Service | ESXi server | TCP | 443 | — |
| Backup repository  Gateway server working with backup repository | Hyper-V server | TCP | 6162, 2500 to 3300 | The port range 2500-3300 is used for failover if port 6162 is unavailable. |

SureReplica Recovery Verification Components

The following table describes network ports that must be opened to ensure proper communication for [SureReplica](surereplica_hiw.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

SureReplica Recovery Verification Components

| From | To | Protocol | Port | Notes |
| Communication with Proxy Appliances | | | | |
| Backup server | Proxy appliance | TCP | 443 | — |
| Communication with VMs | | | | |
| Backup server | Applications on VMs in the virtual lab | — | — | Application-specific ports to perform port probing test. For example, to verify a DC, Veeam Backup & Replication probes port 389 for a response. |
| Internet-facing proxy server | VMs in the virtual lab | TCP | 8080 | Required to allow VMs in a virtual lab access the Internet. |

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
| Backup server | Microsoft  Active Directory VM guest OS | TCP | 135 | — |
| TCP, UDP | 389 | — |
| TCP | 636, 3268, 3269 | — |

Microsoft Exchange Server

The following table describes network ports that must be opened for the Microsoft Exchange Server involved in application-item restore.

Microsoft Exchange Server

| From | To | Protocol | Port | Notes |
| Backup server | Microsoft Exchange 2003/2007 CAS Server | TCP | 80, 443 | — |
| Backup server | Microsoft Exchange 2010/2013/2016/2019 CAS Server | TCP | 443 | — |

Microsoft SQL Server

The following table describes network ports that must be opened for the Microsoft SQL Server involved in application-item restore.

Microsoft SQL Server

| From | To | Protocol | Port | Notes |
| Backup server | Microsoft SQL VM guest OS | TCP | 1433, 1434 and other | Port numbers depends on configuration of your Microsoft SQL server. For more information, see [this Microsoft article](https://msdn.microsoft.com/en-us/library/cc646023.aspx#BKMK_ssde). |
| UDP | 1434 | — |

Restore to Amazon EC2 and Restore to Google Cloud Components

The following table describes network ports that must be opened to ensure proper communication for [restore to Amazon EC2](restore_amazon.md) and [restore to Google Compute Engine](restore_google.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Restore to Amazon EC2 and Restore to Google Cloud Components

| From | To | Protocol | Port | Notes |
| Backup server or  Backup repository | Helper appliance | TCP | 22 | — |
| TCP | 443 | You can change this port in helper appliance settings. For details, see the Specify Helper Appliance section in [Restore to Amazon EC2](restore_amazon_proxy.md) and [Restore to Google Cloud](restore_google_proxy_appliance.md). |

Restore to Microsoft Azure Components

The following table describes network ports that must be opened to ensure proper communication for [Restore to Microsoft Azure](restore_azure_hiw.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Restore to Microsoft Azure Components

| From | To | Protocol | Port | Notes |
| Communication with Microsoft | | | | |
| Backup server | Microsoft Azure Resource Manager service  (https://management.azure.com) | TCP | 443 | — |
| Backup server | Microsoft Entra ID  (https://login.microsoftonline.com) | TCP | 443 | — |
| Backup server | Microsoft Azure storage accounts (blob storage)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Required for restored Windows-based VM conversion. Restored disks are temporarily mounted to the backup server.  Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| Backup server | Azure Windows VM agent distribution location  (go.microsoft.com, aka.ms, github.com, objects.githubusercontent.com) | TCP | 443 | Consider that these URLs used are subject to change. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-windows#install-the-azure-windows-vm-agent). |
| Backup server | Microsoft Azure CRL distribution points | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server can reach these verification endpoints. |
| Communication with Helper Appliances | | | | |
| Backup server | Helper appliance | TCP | 22 | Required when restoring Linux workloads. This port can be changed during helper appliance deployment. For details, see [Managing Helper Appliances](restore_azure_linux.md). |
| Communication with Proxy Appliances | | | | |
| Backup server or backup repository | Azure restore proxy appliance | TCP | 443 | The port must be accessible from the backup server and backup repository storing VM backups.  This port can be changed in the settings of the Azure Restore proxy appliance. For details, see [Specify Credentials and Transport Port](restore_azure_proxy_credentials.md). |

Instant Recovery to Microsoft Azure Components

The following table describes network ports that must be opened to ensure proper communication for [Instant Recovery to Microsoft Azure](instant_recovery_to_azure.md). If any basic backup infrastructure components will also be used, you also need to open ports for these components. For example, [Backup Server](#backup). You may also need to open ports for other features described in this section. For example, [Guest Processing](#guest_processing_components).

Instant Recovery to Microsoft Azure Components

| From | To | Protocol | Port | Notes |
| Communication with Microsoft | | | | |
| Backup server | Microsoft Azure Resource Manager service  (https://management.azure.com) | TCP | 443 | Service Tag: AzureResourceManager |
| Backup server | Microsoft Azure storage account (Veeam packages upload)  (<storage-account>.queue.core.windows.net, <storage-account>.queue.storage.azure.net) | TCP | 443 | Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Microsoft Azure storage account (Veeam packages upload)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Backup server,  Instant Recovery for Azure helper appliance | Microsoft Azure storage account (message queues)  (<storage-account>.queue.core.windows.net, <storage-account>.queue.storage.azure.net) | TCP | 443 | Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Microsoft Azure storage account (message queues)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal.  Service Tag: Storage |
| Instant Recovery for Azure helper appliance | Microsoft Azure storage account (backup repository) / Veeam Data Cloud Vault (backup repository)  (<storage-account>.blob.core.windows.net, <storage-account>.blob.storage.azure.net) | TCP | 443 | Consider that the <storage-account> part of the address must be replaced with the ID of your storage vault. You can find the storage vault ID in the Storage Vaults > Vault ID section in Veeam Data Cloud Vault. For more information, see the [Managing Storage Vaults](https://helpcenter.veeam.com/docs/vdc/userguide/vault_storage_vaults_edit.html#viewing-storage-vault-details) section in the Veeam Data Cloud User Guide.  Service Tag: Storage |
| Backup server,  Instant Recovery for Azure helper appliance | Microsoft Entra ID  (https://login.microsoftonline.com) | TCP | 443 | Service Tag: AzureActiveDirectory |
| Backup server,  Instant Recovery for Azure helper appliance,  Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Microsoft Azure CRL distribution points | TCP | 80 | Port used to verify the certificate status through the certificate verification endpoints (CRL URLs and OCSP servers).  These endpoints are subject to change. You can find the actual list of addresses in [this Microsoft article](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists) or in the certificate details in the following fields:   * CRL Distribution Points * Authority Information Access   Make sure that the backup server, helper appliance and temporary VMs can reach these verification endpoints. |
| Instant Recovery for Azure helper appliance | Azure Windows VM Agent Distribution location  (go.microsoft.com, aka.ms, github.com, objects.githubusercontent.com) | TCP | 443 | Consider that these URLs are subject to change. For more information, see [this Microsoft article](https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/agent-windows#install-the-azure-windows-vm-agent). |
| Instant Recovery for Azure helper appliance | Azure Instance Metadata Service endpoint  (http://169.254.169.254) | TCP | 80 | Required for Entra ID authentication to access storage accounts and message queues and other purposes.  Service Tag: AzureActiveDirectory |
| Temporary Azure VMs used to create templates of Instant Recovery to Azure helper appliances | Ubuntu Azure repository  (http://azure.archive.ubuntu.com/ubuntu/) | TCP | 80 |  |
| Communication with Helper Appliances | | | | |
| Restored VM | Instant Recovery to Azure helper appliance | TCP | 3260-3262 | — |
| TCP | 9555 | — |

Other Veeam Products and Components

Veeam Agents

* [Connections for Veeam Agent Backup with Veeam Backup & Replication](agents_used_ports.md)

Veeam Backup Enterprise Manager

* [Veeam Backup Enterprise Manager Connections](https://helpcenter.veeam.com/docs/vbr/em/used_ports.html?ver=13)

Veeam Explorers

* [Veeam Explorer for Microsoft Active Directory Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vead_ports.html?ver=13)
* [Veeam Explorer for Microsoft Exchange Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vex_ports.html?ver=13)
* [Veeam Explorer for Microsoft SharePoint and Veeam Explorer for Microsoft OneDrive Connections](https://helpcenter.veeam.com/docs/vbr/explorers/vesp_ports.html?ver=13)
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

Page updated 2026-08-03

