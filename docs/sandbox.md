---
title: "On-Demand Sandbox for VMware vSphere"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sandbox.html"
last_updated: "12/29/2025"
product_version: "13.0.1.1071"
---

# On-Demand Sandbox for VMware vSphere

In this article

If you need to perform tests for production VMs, you can use an On-Demand SandboxTM. The On-Demand Sandbox is an isolated virtual environment where you can start one or more VMs from backups, VM replicas or VMs from storage snapshots. You can use the On-Demand Sandbox to perform the following tasks:

* Troubleshoot problems with VMs
* Test software patches and upgrades
* Install new software and so on

The On-Demand Sandbox uses a virtual lab — an isolated environment that is fully fenced off from the production environment. VMs started in the virtual lab remain in the read-only state. All changes made to VMs are written to redo logs (for VM backups and storage snapshots) or saved to delta files (for VM replicas). Redo logs and delta files are deleted after you finish working with the On-Demand Sandbox and power it off.

To create the On-Demand Sandbox, you must configure the following objects:

* Virtual lab in which VMs will be started. For more information, see [Virtual Lab](virtual_lab.md).
* Application group. The application group must include all VMs and VM replicas that you want to start in the On-Demand Sandbox. This can be one VM or a group of VMs that work together. For more information, see [Application Group](application_group.md).
* SureBackup job. The virtual lab and application group must be linked to this job. For more information, see [SureBackup Job](surebackup_job.md).

Related Topics

* [On-Demand Sandbox for Storage Snapshots](sandbox_storages.md)
* [Mixed Scenarios](recovery_verification.md)
* [Configuring On-Demand Sandbox](sandbox_configure.md)

Page updated 12/29/2025

Page content applies to build 13.0.1.1071
