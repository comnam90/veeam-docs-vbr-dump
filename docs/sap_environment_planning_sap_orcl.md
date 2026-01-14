---
title: "SAP Environment Planning"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sap_environment_planning_sap_orcl.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# SAP Environment Planning

In this article

The integration of SAP on Oracle and Veeam Plug-In requires additional environment planning. When you deploy the plug-in, keep in mind the following requirements and limitations.

Limitation for SAP Detection on Different Host

Veeam Plug-In may not be able to detect SAP instances during the configuration if the Oracle Database and SAP central instance are running on different hosts. If you work with Veeam Plug-In in the managed mode, this configuration is not supported. If you work with Veeam Plug-In in the standalone operation mode, see [Configuring Plug-In for SAP on Oracle](configure_sap_orcl.md).

Scheduling

You can schedule backup processes using Cron.

Also, you can schedule and run existing SAP BR\*Tools backup scripts within image-level or file-level backup job of Veeam Backup & Replication or Veeam Agent. For details, see [Pre-Freeze and Post-Thaw Scripts](backup_job_vss_scripts_vm.md).

Page updated 9/2/2025

Page content applies to build 13.0.1.1071
