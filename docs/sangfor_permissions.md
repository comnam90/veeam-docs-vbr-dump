---
title: "Account Permissions"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sangfor_permissions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Account Permissions


The accounts used to deploy and administer backup infrastructure components must have the following permissions.

Backup Server Windows Account Permissions

The account used to install Veeam Backup & Replication on a Windows-based machine must have the following permissions.

Backup Server Windows Account Permissions

| Account | Required Permission |
| Setup Account | The account used to install Veeam Backup & Replication and Veeam Plug-in for Sangfor aSV must have the Local Administrator permissions on the backup server. |
| Veeam Backup & Replication User Account | The account used to run Veeam Backup & Replication services must be a LocalSystem account or must have the Local Administrator permissions on the backup server. |

Sangfor aSV Server Permissions

The account that the backup server uses to access the Sangfor aSV server must have the following permissions in the Sangfor Cloud Platform:

Sangfor aSV Server Permissions

| Category | | Permission |
| Services | | SDK Service |
| Resources | | All |
| Operations | Images | Read-Only   * Obtain list of images * Obtain list of images from cache   Write   * Upload image * Delete image * Create image * Edit image |
| Network | Read-Only   * Obtain list of edges * Obtain list of VPC subnets * Obtain list of virtual switches in classic network * Obtain details VPC subnets |
| Virtual Machine Management | Read-Only   * Obtain VM configuration * Obtain VM list * Obtain VM network IP list * Obtain execution results of VM internal script * Obtain VM snapshot list * Obtain VM snapshot * Obtain VM group list * Obtain VM * Obtain the list of tags * Obtain list of datastores   Write   * Start VM * Shut down VM * Reset VM * Permanently delete VM * Create VM * Update VM * Perform operations on VM disk * Create VM disk * Execute commands on VM internally * Create VM snapshot * Delete VM snapshot * Restore VM snapshot * Reset VM password * Edit VM configuration details |
| Resource Pools | Read-Only   * Obtain resource pool list information * Obtain resource pool overview * Obtain resource pool information * Obtain physical machine list * Obtain platform overview information * Obtain storage list * Obtain communication domain list information |
| Storage Management | Read-Only   * Obtain storage policy list for the resource pool |
| System Management | Read-Only   * Obtain cloud platform version information * Obtain SCP version information * Obtain log progress |
| User Management | Read-Only   * Obtain list of users * Obtain list of roles |
| Cluster Management | Read-Only   * Obtain cluster list * Obtain cluster information |
| Tenants | Read-Only   * Obtain list of tenants |
| Custom Attributes | Read-Only   * Obtain custom attribute list * Obtain the list of bound custom attributes   Write   * Edit bound custom attribute * Bulk bind with custom attributes * Bulk unbind custom attributes |
| Backup Resource Management | Read-Only   * Obtain disk resources * Obtain backup resources * Obtain the list of SDK versions and transmission modes supported by backup resources   Write   * Create disk resources * Create backup resources * Update backup resources * Delete backup resources * Delete disk resources |
| VM CBT Management | Read-Only   * Obtain VM CBT information * Obtain CBT differential bitmap of VM disk   Write   * Update VM CBT |

Page updated 2026-07-31

