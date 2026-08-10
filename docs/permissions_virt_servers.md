---
title: "Virtualization Servers and Hosts"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/permissions_virt_servers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Virtualization Servers and Hosts


The following permissions and roles are required to work with virtualization servers and hosts during data protection tasks.

Virtualization Servers and Hosts

| Component | Required Permission or Role |
| Source/Target VMware vSphere Host | Root permissions on the ESXi host. When adding the credentials, use the MACHINE\USER format for local accounts or DOMAIN\USER format for domain accounts.  If the vCenter Server is added to the backup infrastructure, an account that has administrative permissions is required. You can either grant the Administrator role to the account or configure granular vCenter Server permissions for certain Veeam Backup & Replication operations in the VMware vSphere environment. For more information, see the [Permissions Reference](https://helpcenter.veeam.com/docs/vbr/permissions/installation.html?ver=13). |
| VMware Cloud Director Server | System administrative permissions on VMware Cloud Director for the account that you specify when adding a server. You cannot use the organization administrator account to add the Cloud Director server.  If the account is provisioned from an external identity provider (for example, LDAP, Active Directory, SAML, or OIDC) and mapped to the System organization, append the @system suffix to the user name — for example, administrator@system. |
| Source / Target Hyper-V host or cluster | Administrative permissions. |
| SCVMM | SCVMM user with administrative permissions on the SCVMM server, the Hyper-V hosts and clusters managed by SCVMM and involved in the data protection operations. |
| Windows Server [added to the backup infrastructure](add_windows_server.md) | User account added in the local administrators group (on the server being added). When adding the credentials, use the MACHINE\USER format for local accounts or DOMAIN\USER format for domain accounts. |
| Linux Server [added to the backup infrastructure](add_linux_server.md) | Root or equivalent permissions. |
| SMB Backup Repository | Read and write permission on the target folder and share. |
| Dell Data Domain Deduplicating Storage Appliance | Access permissions on the DD Boost storage unit where backup data will be kept. To specify the DD Boost User account settings, in Data Domain System Manager, open the Data Management > DD Boost Settings tab. |
| HPE StoreOnce Deduplicating Storage Appliance | Access permissions on the Catalyst store where backup data will be kept. To check the client account permissions, in the HPE StoreOnce management console, select the Catalyst store and open the Permissions tab for it. |

Page updated 2026-07-21

