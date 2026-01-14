---
title: "Helper Appliance Template"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/helper_appliance_template.html"
last_updated: "8/21/2025"
product_version: "13.0.1.1071"
---

# Helper Appliance Template

In this article

The helper appliance template is required for [Instant Recovery to Microsoft Azure](instant_recovery_to_azure.md). During recovery, Veeam Backup & Replication deploys helper appliances from the templates. Linux-based templates are used during recovery of Linux workloads. Microsoft Windows-based templates during recovery of Microsoft Windows-based workloads.

The templates are published in the Azure Compute Gallery. This approach reduces storage costs because storing templates is less expensive than storing VMs.

Template Creation

To create a helper appliance template, Veeam Backup & Replication first sends a command to create two VMs: one Linux-based and one Microsoft Windows-based. The size of these VMs is Standard\_D4lds\_v5. The VMs are created in the Azure region selected in the [Helper Appliance Templates](ha_template_add.md) wizard. Veeam Backup & Replication uses the selected storage account to upload all required components and services to the VMs. Then the VMs are captured as templates (managed images) and published to the Azure Compute Gallery. The published templates are stored in the resource group selected in the wizard.

In This Section

* [Adding Helper Appliance Template](ha_template_add.md)
* [Changing](ha_template_change_size.md) [Template and Helper Appliance Size](ha_template_change_size.md)

Page updated 8/21/2025

Page content applies to build 13.0.1.1071
