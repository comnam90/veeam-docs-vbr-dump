---
title: "Veeam Backup & Replication Services"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/services_and_components.html"
last_updated: "11/26/2025"
product_version: "13.0.1.1071"
---

# Veeam Backup & Replication Services


This section describes services used by Veeam Backup & Replication:

* [Linux services](#linux_services)
* [Microsoft Windows services](#win_services)

Linux Services

The following table describes Veeam services used by Veeam Backup & Replication deployed from Veeam Software Appliance. You can manage Veeam services through the Host Management console. For more information, see [Performing Maintenance Tasks](hmc_perform_maintenance_tasks.md).

| Name | Service | Description |
| --- | --- | --- |
| Primary Services | | |
| Veeam Backup Service | veeambackupsvc.service | Coordinates all operations performed by Veeam Backup & Replication such as backup, replication, recovery verification and restore tasks. |
| Veeam Backup REST API Service | veeamrestapisvc.service | Provides access to Veeam Backup & Replication by REST API. For more information on Veeam Backup & Replication REST API, see the [REST API Reference](https://helpcenter.veeam.com/references/vbr/13/rest). |
| Veeam Broker Service | veeambrokersvc.service | Interacts with the virtual infrastructure to collect and cache the virtual infrastructure topology. Jobs and tasks query information about the virtual infrastructure topology from the broker service, which accelerates job and task performance.  Used in VMware vSphere environments. |
| Veeam Catalog Service | veeamcatalogsvc.service | Manages guest OS file system indexing for VMs and replicates system index data files to enable search through guest OS files. Index data is stored in the /var/lib/veeam/catalog directory on the backup server.  Works in conjunction with search components installed on Veeam Backup Enterprise Manager and (optionally) a dedicated Microsoft Search Server. |
| Veeam CDP Coordinator Service | veeamcdpsvc.service | Communicates with VMware vCenter, assigns continuous data protection (CDP) tasks and manages the VMware vSphere infrastructure components involved in CDP. For more information on CDP, see [Continuous Data Protection (CDP) for VMware vSphere](cdp_replication.md). |
| Veeam CDP Proxy Service | veeamcdpproxy.service | Sends and receives virtual machine data during CDP.  Used in VMware vSphere environments. |
| Veeam Cloud Connect | veeamcloudconnect.service | Provides transparent connection to cloud resources over the secure SSL/TLS channel. |
| Veeam Data Analyzer Service | veeamdataanalyzersvc.service | Analyzes the malware detection metadata for potential threats. |
| Veeam Distribution Service | veeamdistributionsvc.service | Distributes the Veeam Agent setup packages to the protected computers. For more information, see [Veeam Agent Backup](agents_infrastructure.md). |
| Veeam Environment Service | veeamenvironment.service | Manages firewall rules. Runs as a dedicated process of the Veeam Transport Service. |
| Veeam Explorer Recovery Service | veeamexplorerrecovery.service | Executes data recovery workflows on behalf of some Veeam Explorers. Runs on the mount server associated with the backup repository. For more details on which Explorers use this service and how they use it, see the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13). |
| Veeam Guest Interaction Service daemon | veeamguestinteraction.service | Performs application-aware processing, file system indexing and enables guest OS file restore to the original location. |
| Veeam High Availability Service | veeamhasvc.service | Manages High Availability clusters. |
| Veeam Host Manager daemon | veeamhostmanager.service | Provides access to the Veeam Host Management console. |
| Veeam Identity Service | veeamidentitysvc.service | Manages authorization between Veeam backup infrastructure components. |
| Veeam Immutability Service | veeamimmurepo.service | Manages immutability attributes. Runs as a dedicated process of the Veeam Transport Service. For more information, see [How Immutability Works](hardened_repository_immutability.md). |
| Veeam Linux Deployer | veeamdeployment.service | Installs, updates or removes Veeam services when you add, update or remove backup infrastructure components. Runs as a dedicated process of the Veeam Installer Service. For more details, see [Veeam Installer Service](installer_service.md). |
| Veeam Mount Service | veeammountsvc.service | Mounts backups and replicas for file-level access, browsing the VM guest file system and restoring VM guest OS files and application items to the original location. |
| Veeam Network Filesystems Mount Service | veeamnetfsmount.service | Mounts NFS and SMB (CIFS) backup repositories. |
| Veeam Threat Hunter | veeamthreathuntersvc.service | Performs signature-based malware detection scans. For more information, see [Veeam Threat Hunter for Scan Backup](malware_detection_scan_backup_veeam_threat_hunter.md). |
| Veeam Transport Service | veeamtransport.service | Sends and receives protected data during backup, replication and restore processes. |
| Veeam Updater | veeam-updater.service | Manages updates on the backup server and backup infrastructure components deployed from Veeam Software Appliance. For more information, see [Updating Veeam Appliances](update_appliances.md). |
| Veeam Updater package manager | veeam-updater-package-manager.service | Manages packages for Veeam Updater. |
| Veeam vPower NFS | veeamnfssvc.service | Implements vPower NFS server that enables running virtual machines directly from backup files.  Used in VMware vSphere environments. |
| Veeam Web Service | veeamwebsvc.service | Provides access to the Veeam Backup & Replication web server. |
| Plug-In Services | | |
| Veeam AWS Service | veeam-platform-service-aws.service | Enables interaction between Veeam Backup & Replication and AWS infrastructure. |
| Veeam Kubernetes Service | veeam-platform-service-kasten.service | Enables interaction between Veeam Backup & Replication and Kasten for Kubernetes Infrastructure. |
| Veeam Microsoft Azure Platform Service | veeam-platform-service-azure.service | Enables interaction between Veeam Backup & Replication and Microsoft Azure infrastructure. |
| Veeam Nutanix AHV Platform Service | veeam-platform-service-ahv.service | Enables interaction between Veeam Backup & Replication and Nutanix AHV infrastructure. |
| Veeam Proxmox Virtual Environment Platform Service | veeam-platform-service-pve.service | Enables interaction between Veeam Backup & Replication and Proxmox Virtual Environment. |
| Veeam Scale Computing HyperCore Platform Service | veeam-platform-service-scp.service | Enables interaction between Veeam Backup & Replication and Scale Computing HyperCore infrastructure. |

Microsoft Windows Services

The following table describes Veeam services used by Veeam Backup & Replication installed on Microsoft Windows.

| Name | Service | Description |
| --- | --- | --- |
| Primary Services | | |
| Veeam Backup Service | VeeamBackupSvc | This is a Microsoft Windows service that coordinates all operations performed by Veeam Backup & Replication such as backup, replication, recovery verification and restore tasks. This service runs on the backup server. |
| Veeam Backup Server RESTful API Service | VeeamBackupRESTSvc | Provides access to Veeam Backup & Replication by using the web API. For more information, see the [REST API Reference](https://helpcenter.veeam.com/references/vbr/13/rest). |
| Veeam Backup Update Service | VeeamBackupUpdateSvc | Enables the update of backup servers. The service runs locally and does not connect to the internet. It only requires a connection to the configuration database server of the backup server. |
| Veeam Backup VSS Integration Service | VeeamFilesysVssSvc | Manages Microsoft VSS snapshots used for NAS, file share and Veeam Agent backups. |
| Veeam Broker Service | VeeamBrokerSvc | Interacts with the virtual infrastructure to collect and cache the virtual infrastructure topology. Jobs and tasks query information about the virtual infrastructure topology from the broker service, which accelerates job and task performance.  Used in VMware vSphere environments. |
| Veeam CDP Agent Service | VeeamCDPAgentSvc | Deploys the I/O filter drivers, receives the captured data, aggregates it and sends to the CDP proxies. For more information, see [Universal CDP to VMware vSphere](universal_cdp.md). |
| Veeam CDP Coordinator Service | VeeamBackupCdpSvc | Communicates with VMware vCenter, assigns continuous data protection (CDP) tasks and manages the infrastructure components involved in CDP. For more information on CDP, see [Continuous Data Protection (CDP)](cdp_replication.md). |
| Veeam CDP Proxy Service | VeeamCdpProxySvc | Sends and receives virtual machine data during CDP.  Used in VMware vSphere environments. |
| Veeam Cloud Connect Service | VeeamCloudSvc | Provides transparent connection to cloud resources over the secure SSL/TLS channel. |
| Veeam Cloud Gateway Service | VeeamGateSvc | Manages data exchange with Veeam Cloud Connect users. For more information on Veeam Cloud Connect, see the [Veeam Cloud Connect Guide](https://helpcenter.veeam.com/docs/vbr/cloud/cloud_overview.html?ver=13). |
| Veeam Data Analyzer Service | VeeamDataAnalyzerSvc | Analyzes the malware detection metadata for potential threats. |
| Veeam Data Mover Service | VeeamTransportSvc | Sends and receives protected data during backup, replication and restore processes. |
| Veeam Distribution Service | VeeamDistributionSvc | Distributes the Veeam Agent setup packages to the protected computers. For more information, see [Veeam Agent Backup](agents_infrastructure.md). |
| Veeam Deployment Service | VeeamMBPDeploymentService | Enables installing, updating and configuring Veeam Service Provider Console components. |
| Veeam Explorers Recovery Service | VeeamExplorersRecoverySvc | Executes data recovery workflows on behalf of some Veeam Explorers. This service runs on the mount server associated with the backup repository. For more details on which Explorers use this service and how they use it, see the [Veeam Explorers User Guide](https://helpcenter.veeam.com/docs/vbr/explorers/explorers_introduction.html?ver=13). |
| Veeam GCP Service | VeeamGCPSvc | Enables interaction between Veeam Backup & Replication and Google Cloud infrastructure. |
| Veeam Guest Agent | VeeamGuestHelper | Performs application-aware processing, file system indexing and enables guest OS file restore to the original location. |
| Veeam Guest Catalog Service | VeeamCatalogSvc | Manages guest OS file system indexing for VMs and replicates system index data files to enable search through guest OS files. Index data is stored in the Veeam Backup Catalog — a folder on the backup server. The Veeam Guest Catalog Service running on the backup server works in conjunction with search components installed on Veeam Backup Enterprise Manager and (optionally) a dedicated Microsoft Search Server. |
| Veeam Hyper-V Integration Service | VeeamHvIntegrationSvc | Enables Veeam Backup & Replication to perform on-host and off-host processing of Hyper-V virtual machines.  Used in Microsoft Hyper-V environments. |
| Veeam Installer Service | VeeamDeploySvc | Installs, updates or removes Veeam services when you add, update or remove backup infrastructure components. For more details, see [Veeam Installer Service](installer_service.md). |
| Veeam Log Shipping Service | VeeamLogShipper | Copies Microsoft SQL Server, Oracle and PostgreSQL transaction logs to the backup repository. In addition, Veeam Explorer for Microsoft SQL Server uses this service to restore transaction logs if the administrative share (for example, \\myserver\ADMIN$) is unavailable. |
| Veeam Management Agent Service | VeeamManagementAgentSvc | Collects data from Veeam products discovered on the machine. |
| Veeam Mount Service | VeeamMountSvc | Mounts backups and replicas for file-level access, browsing the VM guest file system and restoring VM guest OS files and application items to the original location. |
| Veeam ONE Agent | VeeamOneAgentSvc | Enables remediation actions and communication between Veeam ONE and monitored Veeam Backup & Replication servers. |
| Veeam Oracle Restore Service | Veeam.Oracle.Service | Enables item-level recovery of Oracle data for Windows machines. This runtime component is deployed on the target machine or staging server. |
| Veeam SQL Agent Service | Veeam.SQL.Agent.Service | Enables item-level recovery of Microsoft SQL Server data. This persistent component is deployed on the target machine or staging server if the administrative share (for example, \\myserver\ADMIN$) is unavailable. For more information, see the [How Data Recovery Works](https://helpcenter.veeam.com/docs/vbr/explorers/vesql_restore_service.html?ver=13) section of the Veeam Explorers User Guide. |
| Veeam SQL Restore Service | Veeam.SQL.Service | Enables item-level recovery of Microsoft SQL Server data. This runtime component is deployed on the target machine or staging server if the administrative share (for example, \\myserver\ADMIN$) is available. For more information, see the [How Data Recovery Works](https://helpcenter.veeam.com/docs/vbr/explorers/vesql_restore_service.html?ver=13) section of the Veeam Explorers User Guide. |
| Veeam Threat Hunter Service | VeeamThreatHunterSvc | Performs signature-based malware detection scans. For more information, see [Veeam Threat Hunter for Scan Backup](malware_detection_scan_backup_veeam_threat_hunter.md). |
| Veeam Tape Access Service | VeeamTapeSvc | Provides access to tape devices connected to this tape server for Veeam Backup & Replication tape jobs. |
| Veeam vPower NFS Service | VeeamNFSSvc | Implements vPower NFS server that enables running virtual machines directly from backup files.  Used in VMware vSphere environments. |
| Veeam VSS Hardware Provider Service | VeeamVssProviderSvc | Extends the Microsoft VSS to enable Veeam Agent backup from storage snapshots.  Used in VMware vSphere environments. |
| Veeam WAN Accelerator Service | VeeamWANSvc | Optimizes the network traffic consumption by identifying and caching repeatedly transferred data. |
| Veeam Web Service | VeeamWebSvc | Provides access to the Veeam Backup & Replication web server. |
| Plug-In Services | | |
| Veeam AWS Service | VeeamAWSSvc | Enables interaction between Veeam Backup & Replication and AWS infrastructure. |
| Veeam AHV Service | VeeamAHVSvc | Enables interaction between Veeam Backup & Replication and Nutanix AHV infrastructure |
| Veeam Azure Service | VeeamAzureSvc | Enables interaction between Veeam Backup & Replication and Microsoft Azure infrastructure. |
| Veeam Kubernetes Service | VeeamKastenSvc | Enables interaction between Veeam Backup & Replication and Kasten for Kubernetes Infrastructure. |
| Veeam KVM Service | VeeamRHVSvc | Enables interaction between Veeam Backup & Replication and oVirt KVM infrastructure. |
| Veeam PVE Service | VeeamPVESvc | Enables interaction between Veeam Backup & Replication and Proxmox Virtual Environment. |
| Veeam SC HyperCore Service | VeeamHyperCoreSvc | Enables interaction between Veeam Backup & Replication and Scale Computing HyperCore infrastructure. |


