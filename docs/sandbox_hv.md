---
title: "On-Demand Sandbox for Microsoft Hyper-V"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sandbox_hv.html"
last_updated: "8/11/2025"
product_version: "13.0.1.1071"
---

# On-Demand Sandbox for Microsoft Hyper-V


If you need to perform tests for production VMs, you can use an On-Demand SandboxTM. The On-Demand Sandbox is an isolated virtual environment where you can start one or more VMs from backups. You can use the On-Demand Sandbox to perform the following tasks:

* Troubleshoot problems with VMs
* Test software patches and upgrades
* Install new software and so on

The On-Demand Sandbox uses a virtual lab — an isolated environment that is fully fenced off from the production environment. To start a VM in the virtual lab, Veeam Backup & Replication uses [Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md). When you finish working with the On-Demand Sandbox, Veeam Backup & Replication unpublishes the VM and powers off the virtual lab.

To create the On-Demand Sandbox, you must configure the following objects:

* Virtual lab in which VMs will be started. For more information, see [Virtual Lab](virtual_lab_hv.md).
* Application group. The application group must include all VMs that you want to start in the On-Demand Sandbox. This can be one VM or a group of VMs that work together. For more information, see [Application Group](application_group_hv.md).
* SureBackup job. The virtual lab and application group must be linked to this job. For more information, see [SureBackup Job](surebackup_job_hv.md).

Related Topics

[Configuring On-Demand Sandbox](sandbox_configure_hv.md)


