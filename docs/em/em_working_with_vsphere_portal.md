---
title: "vSphere Self-Service Backup Portal"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_working_with_vsphere_portal.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---


In this article

Veeam Backup & Replication allows backup administrators to delegate VM backup and restore operations to VMware vSphere users. For that, Veeam Backup & Replication offers vSphere Self-Service Backup Portal — a web tool based on Veeam Backup Enterprise Manager. With the portal, users can create and manage backup jobs that process VMware vSphere VMs and restore data from backups created with these jobs. All operations are performed from the web UI without the need to deploy the Veeam Backup & Replication console on the user machine.

To define what VMs vSphere users can back up and restore, Veeam Backup Enterprise Manager offers the concept of delegation mode. The delegation mode specifies conditions that must be met to allow a user to add a VM to the backup job. The administrator can choose from 3 delegation modes based on vSphere tags, vSphere roles or VM privileges. For more information, see [Configuring Delegation Mode](em_configuring_delegation_mode.md).

In terms of vSphere Self-Service Backup Portal, a vSphere user that works with the portal is considered a tenant. To access the portal, a tenant uses the tenant account created by the Enterprise Manager administrator. The administrator can create tenant accounts for a separate vSphere user and a group of users. Tenant account settings define storage quota available to the tenant in the backup repository and settings for backup jobs created by the tenant. For more information, see [Managing Tenant Accounts](em_managing_tenants.md).

To simplify backup job management for tenants, advanced job settings (such as backup settings and storage settings) are automatically populated from job templates. The administrator can assign a separate template to each tenant account.

When working with vSphere Self-Service Backup Portal, you can perform the following tasks:

* [Administrator tasks](#admin_tasks)
* [Tenant tasks](#tenant_tasks)

Administrator Tasks

To let tenants work with vSphere Self-Service Backup Portal, the Enterprise Manager administrator performs the following tasks:

1. [Configures the delegation mode](em_configuring_delegation_mode.md)

The default delegation mode allows tenants to access VMs with the VirtualMachine.Interact.Backup privilege. The administrator can change the delegation mode, if necessary.

1. [Creates and manages tenant accounts](em_managing_tenants.md)

By default, Veeam Backup Enterprise Manager offers a group tenant account for users of the domain that includes the Enterprise Manager server. Each user can access the portal and use a 30 GB quota on the default backup repository to create VM backups. Users can create backup jobs with default advanced settings and custom schedule. The administrator can edit settings of the default account and create other accounts to configure granular access to storage quotas and backup settings.

Tenant Tasks

Tenants access the vSphere Self-Service Backup portal using the portal URL obtained from the Veeam Backup Enterprise Manager administrator. Tenants can log in to the portal under a domain user account or single sign-on account. For more information, see [Using vSphere Self-Service Backup Portal](em_working_with_vsphere_vms.md#access).

Tenants can use the portal to work with vSphere VMs that are available to them according to the selected delegation mode. VM backup settings are defined by the properties of the tenant account.

Tenants can use vSphere Self-Service Backup Portal to perform the following operations:

* Create and manage backup jobs that process vSphere VMs.
* View VM backup statistics.
* Restore vSphere VMs to the original location.
* Restore files from indexed and non-indexed guest OS file systems of vSphere VMs.
* Perform item-level restore for Microsoft SQL Server and Oracle databases.

For more information, see [Using vSphere Self-Service Backup Portal](em_working_with_vsphere_vms.md).

In This Section

* [Configuring Delegation Mode](em_configuring_delegation_mode.md)
* [Managing Tenant Accounts](em_managing_tenants.md)
* [Using vSphere Self-Service Backup Portal](em_working_with_vsphere_vms.md)

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
