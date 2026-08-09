---
title: "Ports"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_ports.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Ports


As Veeam Plug-in for Microsoft Azure is installed on the same machine where Veeam Backup & Replication runs, it uses the same ports as those described in [Ports](used_ports.md). In addition, Veeam Plug-in for Microsoft Azure also uses ports listed in the following table.

|  |
| --- |
| Tip |
| To allow inbound access to an Azure service, you can use the IP address, DNS name or [virtual network service tag](https://learn.microsoft.com/en-us/azure/virtual-network/service-tags-overview) of the service. If you want to use an IP address, you can download a .JSON file with the full list of Azure IP ranges and service tags from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519). |

Ports

| From | To | Protocol | Port | Description |
| Web browser (local machine) | Backup appliance | TCP/HTTPS | 443 | Required to access the Web UI component from a user workstation. |
| [Optional] Default port required to communicate with the public REST API service running on the backup appliance. For more information on Veeam Plug-in for Microsoft Azure REST API, see the [Veeam Plug-in for Microsoft Azure REST API Reference](https://helpcenter.veeam.com/references/vbazure/8.1/rest/main/tag/SectionAbout). |
| Worker instances | TCP/HTTPS | 443 | Required to access the file-level recovery browser running on a worker instance during the file-level restore process. |
| Backup appliance | Veeam Update Repository (DNS name: repository.veeam.com), Amazon CloudFront (DNS names: cloudfront.net, amazonaws.com) | TCP/HTTPS | 443 | Required to download available product updates, worker deployment packages and restore utilities.  Note: Veeam Update Repository uses the [Amazon CloudFront service](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) to distribute traffic when downloading product updates. |
| Ubuntu Security Repository (DNS name: security.ubuntu.com) and OS Update Repository (DNS name: archive.ubuntu.com) | TCP/HTTP | 80 | Required to get OS security updates. |
| PostgreSQL Apt Repository  (DNS name: apt.postgresql.org) | TCP/HTTPS | 443 | Required to get PostgreSQL updates. |
| PostgreSQL Website (DNS name: postgresql.org) | TCP/HTTPS | 443 | Required to download the [PostgreSQL Apt Repository key](https://www.postgresql.org/media/keys/ACCC4CF8.asc). |
| Microsoft Package Repository (DNS name: packages.microsoft.com) | TCP/HTTPS | 443 | Required to get .NET updates. |
| SMTP server (DNS name or IP address of the SMTP server) | TCP/SMTP | 25 | Default port used for sending email notifications.  Note: The TCP port 25 is used for unencrypted connection to SMTP servers. To instruct Veeam Backup for Microsoft Azure to use encrypted connection when sending email notifications, use port 587. |
| Microsoft Entra ID service (service tag: AzureActiveDirectory) | TCP/HTTPS | 443 | Required to add service accounts. |
| Azure Resource Manager service (service tag: AzureResourceManager) | TCP/HTTPS | 443 | Required to add service accounts, to create Azure VM and Azure Files snapshots, and to deploy and manage backup infrastructure components, including worker instances, backup repositories, virtual networks, and so on. |
| Azure Storage service (service tag: Storage) | TCP/HTTPS | 443 | Required to access Azure storage accounts, and to communicate with worker instances using the Azure Queue Storage messaging service.  If you plan to protect Windows-based Azure VMs, this port is also required to use the Azure Queue Storage messaging service to communicate with Volume Shadow Copy Service (VSS) agents installed on source Azure VMs with enabled guest processing option. For more information, see [Performing Backup](azure_vm_guest_processing.md#limit). |
| Azure Key Vault service (service tag: AzureKeyVault) | TCP/HTTPS | 443 | Required to encrypt backup repositories using cryptographic keys. |
| Azure Virtual Network service  (service tag: VirtualNetwork) | TCP/HTTPS | 443 | Required to communicate with storage accounts where Veeam applications and scripts are stored.  Note: This connection is required to back up Azure resources that operate in private environments only. |
| nginx web server (DNS name: nginx.org) | TCP/HTTPS | 443 | Required to upgrade the backup appliance. |
| Azure Cost Management service  (DNS name: apim-ratecard-v1.azure-api.net) | TCP/HTTPS | 443 | Required to calculate estimated costs for backup policies. |
| Veeam Backup & Replication repository service  (DNS name: vbr.butler.veeam.com) | TCP/HTTPS | 443 | Required to authenticate against Veeam Data Cloud Vault to create and manage storage vaults. For more information, see [Veeam Data Cloud Storage Vaults](azure_vdc_vaults.md). |
| Azure VMs | Azure Storage service (service tag: Storage) | TCP/HTTPS | 443 | [Applies to Windows-based Azure VMs only] Required to download VSS binary files and guest OS files when performing file-level recovery to the original location. |
| Worker instances | Ubuntu Security Repository (DNS name: security.ubuntu.com) and OS Update Repository (DNS name: archive.ubuntu.com) | TCP/HTTP | 80 | Required to get OS security updates. |
| Ubuntu Archive repository (DNS name: azure.archive.ubuntu.com) | TCP/HTTP | 80 | Required to get APT updates. |
| PostgreSQL Apt Repository  (DNS name: apt.postgresql.org) | TCP/HTTP | 80 | Required to get PostgreSQL updates. |
| PostgreSQL Website (DNS name: postgresql.org) | TCP/HTTPS | 443 | Required to download the [PostgreSQL Apt Repository key](https://www.postgresql.org/media/keys/ACCC4CF8.asc). |
| Azure SQL Database (service tag: Sql.<region>, where <region> is the [code name of the Azure region](https://learn.microsoft.com/en-us/azure/media-services/latest/azure-regions-code-names#region-code-name)) | TCP | 1433, 11000-11999 | Required to connect to SQL Servers.  Note: The usage of the specified TCP ports depends on the networking settings of SQL Servers. If the Redirect option is selected, port 1433 is used to establish only the first connection. If the Proxy option is selected, port 1433 is used to establish all connections by default. For more information on networking settings of SQL Servers, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-sql/database/connectivity-settings?view=azuresql&tabs=azure-portal#change-the-connection-policy). |
| Azure SQL Managed Instances  (DNS name or IP address of the Managed Instance) | TCP | 3342 | Required to connect to Azure SQL Managed Instances using public endpoints. |
| TCP | 1433, 11000-11999 | Required to connect to Azure SQL Managed Instances using private endpoints.  Note: The usage of the specified TCP ports depends on the networking settings of SQL Servers. If the Redirect option is selected, port 1433 is used to establish only the first connection. If the Proxy option is selected, port 1433 is used to establish all connections by default. For more information on networking settings of SQL Servers, see [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-sql/database/connectivity-settings?view=azuresql&tabs=azure-portal#change-the-connection-policy). |
| Azure Cosmos DB for PostgreSQL (service tag: AzureCosmosDB) | TCP | 5432 | Required to connect to Cosmos DB for PostgreSQL accounts. |
| Azure Cosmos DB for MongoDB (service tag: AzureCosmosDB) | TCP | 10255 | Required to connect to Cosmos DB for MongoDB accounts. |
| Azure Storage service (service tag: Storage) | TCP | 443, 445 | Required to download worker binary files from Veeam storage accounts.  Note: Port 445 is required only if you plan to enable file share indexing when protecting Azure file shares using an HTTP proxy on a backup appliance deployed in a private environment, or when protecting Azure file shares mounted using the [SMB protocol](https://learn.microsoft.com/en-us/azure/storage/files/files-smb-protocol?tabs=azure-portal#smb-protocol-settings) version 3.0 and later. |
| Veeam Plug-in for Microsoft Azure | Backup appliance | TCP/HTTPS | 443 | Port used for communication with Veeam Backup for Microsoft Azure. |
| Azure Resource Manager service (DNS name: management.azure.com) | TCP/HTTPS | 443 | Required to communicate with Microsoft Azure. |
| Microsoft Entra ID service (DNS name: login.microsoftonline.com) | TCP/HTTPS | 443 |
| Microsoft Graph API (DNS name: graph.microsoft.com) | TCP/HTTPS | 443 | Required to check permissions of Microsoft Entra applications during the upgrade of Veeam Plug-in for Microsoft Azure. |
| AWS CheckIP service (DNS name: checkip.amazonaws.com) | TCP/HTTPS | 443 | Required to get the public IP address of the Veeam Backup & Replication server during the deployment of Veeam Plug-in for Microsoft Azure. |
| Azure Storage service (DNS name: <blob\_name>.blob.core.windows.net, where <blob\_name> is the name of the Azure storage account) | TCP/HTTPS | 443 | Required to access Azure storage accounts when creating backup repositories using Veeam Plug-in for Microsoft Azure. |
| Veeam Backup & Replication console and Veeam ONE server | Backup server | TCP | 443 | Port used to connect to Veeam Plug-in for Microsoft Azure. |

|  |
| --- |
| Note |
| When you deploy a backup appliance from the Veeam Backup & Replication console, Veeam Backup & Replication automatically creates firewall rules for the required ports to allow communication between the backup server and the appliance components. |

Page updated 2026-07-17

