---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_used_ports.html"
last_updated: "1/19/2026"
product_version: "13.0.1.1071"
---

# Ports


For general requirements for ports that must be opened to ensure proper communication of the backup server with backup infrastructure components, see [Ports](used_ports.md).

For general requirements for ports that must be opened to ensure proper communication of the backup server with Veeam Cloud Connect infrastructure components, see the [Ports](https://helpcenter.veeam.com/docs/backup/cloud/ports.html?ver=120) section in the Veeam Cloud Connect Guide.

In addition to general port requirements applicable to a backup server, the following network ports must be opened to enable proper communication between Veeam Backup & Replication components:

Communication Between Veeam Backup & Replication Components

The following table describe network ports that must be opened to ensure proper communication of components in the Veeam Agent management infrastructure:

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam backup server | Veeam Agent computer (Microsoft Windows) | TCP | 6184+ | Default port used to communicate with the Veeam Agent for Microsoft Windows Service.  If port 6184 is already in use, Veeam Agent for Microsoft Windows Service tries to use the next port number in the allocated range (6184 to 6195). Once the service takes the next available port, it makes it the default port for all subsequent connections. |
| TCP | 135, | Default ports used to communicate with the Veeam Installer Service.  Port 135 is used by Veeam Backup & Replication on Microsoft Windows for WMI queries. WMI queries are mandatory for backing up failover clusters and perform file-level restore and optional for faster Veeam Agent deployment.  Port 137 to 139 are used to communicate using NetBIOS if you use NetBIOS in your infrastructure.  Ports 137 to 139 and 445 are used to deploy of Veeam Installer Service and to start restore from the Veeam Backup & Replication console.  Ports 6160 and 11731 are used to deploy Veeam Agent on the computer and to perform volume-level restore.  Notes:   * Port 11731 is used to connect to the Veeam Installer Service in Veeam Agent versions earlier than 13.0.1. If all Veeam Agents in your infrastructure are upgraded to the latest version, this port is not required. * If the backup repository server role and the mount server role are assigned to different servers in your infrastructure, you must open ports described in section [Mount Server Connections](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13#mount-server-connections). |
| UDP | 137, 138 |
| TCP | 6167,  2500 to 3300 | Ports 2500 to 3300 are used to collect Microsoft SQL logs from the Veeam Agent computer. For every TCP connection that a backup job uses, one port from this range is assigned. If Veeam Agent computer operates as part of a failover cluster with SQL Server Always On Availability Groups, ports 2500 to 3300 are used together with port 6167. |
| TCP | 6162 | Default port used by the Veeam Data Mover. |
| TCP | 5985 | Port 5985 is used in the following cases:   * to retrieve of Windows Failover Cluster configuration * to create WMI queries by Veeam Backup & Replication on Linux. WMI queries are mandatory for backing up failover clusters and perform file-level restore and optional for faster Veeam Agent deployment. |
| Veeam Agent computer (Linux) | TCP | 22,  6160,  6162 | Port 22 is used to establish an SSH connection from the Veeam Backup Server to the Veeam Agent computer.  Ports 6160 and 6162 are used to connect to the Veeam Agent computer using Veeam Deployer Service and Veeam Transport Service.  Port 6162 is the default port used by the Veeam Data Mover.  Notes:   * You can customize ports 6160 and 6162. To learn more, see [this Veeam KB article](https://www.veeam.com/kb4519). * If the backup repository server role and the mount server role are assigned to different servers in your infrastructure, you must open ports described in section [Mount Server Connections](https://helpcenter.veeam.com/docs/vbr/userguide/used_ports.html?ver=13#mount-server-connections). |
| TCP | 2500 to 3300 | Default range of ports used for communication between Veeam Agent components during data transmission. For every TCP connection that a backup job uses, one port from this range is assigned.  Note: Ports 2500 to 3300 are required during data transmission if the Veeam Data Mover Service is started on the Veeam backup server. This may happen when the backup is targeted at the default backup repository of the Veeam backup server or when Veeam backup server acts as a gateway to the target backup repository. |
| Veeam Agent computer (Unix) | TCP | 22 | Port 22 is used to establish an SSH connection from the Veeam Backup Server to the Veeam Agent computer. |
| TCP | 2500 to 3300 | Default range of ports used for communication between Veeam Agent components during data transmission. For every TCP connection that a backup job uses, one port from this range is assigned.  Note: Ports 2500 to 3300 are required during data transmission if the Veeam Data Mover Service is started on the Veeam backup server. This may happen when the backup is targeted at the default backup repository of the Veeam backup server or when Veeam backup server acts as a gateway to the target backup repository. |
| Distribution server (Linux) | TCP | 22 | Port used to deploy the Distribution Server component using an account with root privileges. |
| TCP | 6160 | Port used by the Veeam Deployer Service. |
| TCP | 9380 | Default port used to communicate with the Veeam Distribution Service. |
| Distribution server (Microsoft Windows) | TCP | 445 | Port used to deploy the Distribution Server component using local administrator credentials. |
| TCP | 6160, 11731 | Port used by the Veeam Installer Service.  Note: Port 11731 is used to connect to the Veeam Installer Service in Veeam Agent versions earlier than 13.0.1. If all Veeam Agents in your infrastructure are upgraded to the latest version, this port is not required. |
| TCP | 9380 | Default port used to communicate with the Veeam Distribution Service. |
| Distribution server | Veeam backup server | TCP | 443 | Port used to connect to the Veeam Identity Service. |
| Veeam Agent computer (Microsoft Windows) | TCP | 6160, 11731 | Ports on the Veeam Agent computer used for deploying Veeam Agent.  Note: Port 11731 is used to connect to the Veeam Installer Service in Veeam Agent versions earlier than 13.0.1. If all Veeam Agents in your infrastructure are upgraded to the latest version, this port is not required. |
| Veeam Agent computer (Linux) | TCP | 6160 | Default port used to connect to Veeam Agent computer using the Veeam Deployer Service and Veeam Transport Service. |
| Veeam Agent computer (Unix) | TCP | 22 | Port 22 is used to establish an SSH connection for Veeam Agent packages transmission and deployment control. |
| Veeam Agent computer (Microsoft Windows) | Veeam backup server | TCP | 10005 | Default port used by Veeam Agent for Microsoft Windows to communicate with the Veeam Backup server.  Data between the Veeam Agent computer and backup repositories is transferred directly, bypassing Veeam backup servers. |
| TCP | 2500 to 3300 | Default range of ports used to publish the ransomware index. For every TCP connection that a backup job uses, one port from this range is assigned. |
| Veeam Agent computer (Linux, Unix, macOS) | Veeam backup server | TCP | 10006 | Default port used by Veeam Agent operating in the managed mode for communication with the Veeam Backup server.  Data between the Veeam Agent computer and backup repositories is transferred directly, bypassing Veeam backup servers. |

Communication with Veeam Backup Repositories

The following table describes network ports that must be opened to ensure proper communication between Veeam Agent and backup repositories added to the Veeam Backup & Replication infrastructure.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Agent computer | Veeam backup repository | TCP | 6162, 2500 to 3300 | Ports used in the following cases:   * as data transmission channels * for sending logs by Veeam Agents in protection groups for pre-installed backup agents |
| Gateway server | TCP | 6162, 2500 to 3300 | Ports used as data transmission channels.  Ports 137 to 139 are used by backup infrastructure components to communicate using NetBIOS if you use NetBIOS in your infrastructure.  Tip: to learn about the ports required between gateway servers and backup repositories, see [Gateway Server](used_ports.md#gateway). |
| Gateway server (Microsoft Windows) | TCP | 139, 445 |
| UDP | 137, 138 |

Communication with Veeam Cloud Connect Repositories

The following table describes network ports that must be opened to ensure proper communication between Veeam Agents and Veeam Cloud Connect repositories.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Agent computer (Microsoft Windows, Linux, macOS) | Cloud gateway | TCP | 6180 | Default port on the cloud gateway used to transport Veeam Agent data to the Veeam Cloud Connect repository.  You can obtain the current list of ports or cloud gateway connection points from your Service Provider. |
| Certificate revocation lists | TCP | 80 or 443 | Veeam Agent computer needs access to Certificate Revocation Lists (CRLs) of the Certification Authority (CA) who issued a certificate to the Veeam Cloud Connect service provider.  Information about certificate verification endpoints (CRL and OCSP server URLs) can be found on the CA website. Certificate verification endpoints are subject to change. The actual list of addresses can be found in the certificate itself. |

Communication with Object Storage

The following table describes network ports that must be opened to ensure proper communication with object storage if you back up data to object storage that Veeam Agent accesses directly. For more information about object storage connection modes, see [Backup to Object Storage](agents_object_storage.md).

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Gateway server or backup server | Amazon S3 object storage | TCP | 443 | Used to communicate with the Amazon S3 object storage through the following endpoints:   * \*.amazonaws.com (for both Global and Government regions) * \*.amazonaws.com.cn (for China region)   All AWS service endpoints are specified in the [AWS documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| 80 | Used to verify the certificate status through the following endpoints:   * \*.amazontrust.com * \*.cloudfront.net   Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. The actual list of addresses can be found in the certificate itself. |
| Microsoft Azure object storage | TCP | 443 | Used to communicate with the Microsoft Azure object storage through the following endpoints:   * <storage-account>.blob.core.windows.net (for Global region) * <storage-account>.blob.core.chinacloudapi.cn (for China region) * <storage-account>.blob.core.usgovcloudapi.net (for Government region)   Consider that the <storage-account> part of the address must be replaced with your actual storage account URL that can be found in the Azure management portal. |
| 80 | Used to verify the certificate status through the following endpoints:   * ocsp.digicert.com * oneocsp.microsoft.com   Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. The actual list of addresses can be found in the certificate itself. For more details, see also [Microsoft documentation](https://learn.microsoft.com/en-us/azure/security/fundamentals/azure-CA-details?tabs=root-and-subordinate-cas-list#certificate-downloads-and-revocation-lists). |
| Google Cloud storage | TCP | 443 | Used to communicate with Google Cloud storage through the following endpoints:   * storage.googleapis.com   All cloud endpoints are specified in [this Google article](https://cloud.google.com/storage/docs/request-endpoints). |
| 80 | Used to verify the certificate status through the following endpoints:   * ocsp.pki.goog * pki.goog * crl.pki.goog   Consider that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. The actual list of addresses can be found in the certificate itself. |
| IBM Cloud object storage | TCP | Depends on device configuration | Used to communicate with IBM Cloud object storage. |
| S3 compatible object storage | TCP | Depends on device configuration | Used to communicate with S3 compatible object storage. |
| Veeam Data Cloud Vault storage | TCP | 443 | Used to communicate with the Veeam Data Cloud Vault storage through the <storage-account>.blob.core.windows.net endpoint. |

Communication with Shared Folder Targets

The following table describes network ports that must be opened to ensure proper communication between Veeam Agent and shared folder targets outside the Veeam Backup & Replication infrastructure.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam Agent computer | Shared folder SMB (CIFS) share | TCP | 139,  445 | Ports used as a transmission channel from the Veeam Agent computer to the target SMB (CIFS) share not added as a Veeam backup repository  Ports 137-139 are used by backup infrastructure components to communicate using NetBIOS if you use NetBIOS in your infrastructure. |
| UDP | 137, 138 |
| Shared folder NFS share | TCP | 111, 2049 | Standard NFS ports used as a data transmission channel from the Veeam Agent for Linux computer to the target NFS share not added as a Veeam backup repository. |

Communication with Cloud Machines

The following table describes network ports that must be opened to ensure proper communication between Veeam Backup & Replication and Veeam Agents installed on Amazon EC2 instances or Microsoft Azure virtual machines (both objects can be also referred to as cloud machines).

| From | To | Protocol | Port/Endpoint | Notes |
| --- | --- | --- | --- | --- |
| Veeam Backup & Replication,  Amazon EC2 instance with Veeam Agent | Amazon cloud | TCP | 443 | Port and endpoints used for communication from Veeam Backup & Replication and Amazon EC2 instance to the Amazon cloud where the instance is located. |
| HTTPS | AWS service endpoints:   * \*.amazonaws.com (for Global and Government regions) * \*.amazonaws.com.cn (for China region)   A complete list of connection endpoints can be found in [AWS Documentation](https://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region). |
| TCP | 80 | Port and endpoints used to verify the certificate status.  Keep in mind that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. The actual list of addresses can be found in the certificate itself. |
| HTTP | Certificate verification endpoints:   * \*.amazontrust.com |
| Veeam Backup & Replication, Microsoft Azure virtual machine with Veeam Agent | Microsoft Azure cloud | TCP | 443 | Port and endpoints used for communication from Veeam Backup & Replication and Microsoft Azure virtual machine to the Microsoft Azure cloud where the virtual machine is located.  Keep in mind that the <storage-account> part of the address must be replaced with your actual storage account URL, which can be found in the Azure management portal. |
| HTTPS | Global region endpoints:   * management.azure.com * login.microsoftonline.com * <storage-account>.blob.core.windows.net * <storage-account>.queue.core.windows.net * core.windows.net   China region endpoints:   * management.chinacloudapi.cn * login.chinacloudapi.cn * <storage-account>.blob.core.chinacloudapi.cn * <storage-account>.queue.core.chinacloudapi.cn * core.chinacloudapi.cn   Government region endpoints:   * management.chinacloudapi.cn * login.microsoftonline.us * <storage-account>.blob.core.usgovcloudapi.net * <storage-account>.queue.core.usgovcloudapi.net * core.usgovcloudapi.net |
| TCP | 80 | Port and endpoints used to verify the certificate status.  Keep in mind that certificate verification endpoints (CRL URLs and OCSP servers) are subject to change. The actual list of addresses can be found in the certificate itself. |
| HTTP | Certificate verification endpoints:   * \*.digicert.com * \*.digicert.cn (for China region) * oneocsp.microsoft.com * microsoft.com/pkiops |

Communication with 3rd Party Components

The following table describes network ports that must be opened to ensure proper communication between Veeam backup server and 3rd party infrastructure components.

| From | To | Protocol | Port | Notes |
| --- | --- | --- | --- | --- |
| Veeam backup server | Microsoft Active Directory | TCP | 389 | LDAP connections. |
| TCP | 636 | LDAPS (Secure LDAP) connections. |
| DNS server with forward/reverse name resolution of all backup servers | TCP | 53 | Port used for communication with the DNS Server. |


