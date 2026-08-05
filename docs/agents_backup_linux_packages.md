---
title: "Types of Veeam Agent for Linux Installation Packages"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/agents_backup_linux_packages.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Types of Veeam Agent for Linux Installation Packages


You can install Veeam Agent for Linux using one of the following installation package sets:

* Veeam Agent for Linux — This package set depends on the Veeam kernel module to create system snapshots. It supports the widest range of Linux distributions and file systems. For more information on system requirements and limitations, see [System Requirements for Linux Computers](agents_system_requirements_linux.md).
* Nosnap Veeam Agent for Linux — This package set does not depend on the Veeam kernel module to create system snapshots. Instead, nosnap Veeam Agent for Linux uses native file system snapshot capabilities on supported Linux distributions. For more information on system requirements and limitations, see [System Requirements for Linux Computers with Nosnap Veeam Agent](agents_system_requirements_linux_nosnap.md).
* Nosnap Veeam Agent for Linux on Power — This nosnap package set is designed specifically for IBM Power Systems. For more information on system requirements and limitations, see [System Requirements for Linux Computers with Nosnap Veeam Agent](agents_system_requirements_linux_nosnap.md).

Veeam Backup & Replication supports centralized management of Veeam Agent for Linux and nosnap Veeam Agent for Linux. You can configure automatic installation and upgrade in protection groups for individual computers, Microsoft Active Directory objects and computers from CSV file. Nosnap Veeam Agent for Linux on Power can be managed only through protection groups for pre-installed Veeam Agents. For more information, see [Protected Computers Discovery and Veeam Agent Deployment](agents_discovery_and_deployment.md).

Page updated 2026-07-02

