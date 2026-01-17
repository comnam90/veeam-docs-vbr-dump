---
title: "Editing Organization Configuration"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_modifying_vcd_org_settings.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---

# Editing Organization Configuration


Users with the Portal Administrator role can edit VMware Cloud Director organization configurations.

Before you edit a configuration, consider the following recommendations:

* When you change a job template for a Cloud Director organization, the new configuration will be applied only to the new jobs, existing jobs will not be affected.
* To make an existing backup job save backups to another repository instead of the currently configured for a specific organization, take the following steps:

1. Add a new configuration for this organization. In the configuration settings, specify the new repository that you want to move backups to. For details, see [Adding Organization Configuration](em_configure_vcd_org.md).
2. In the Veeam Backup & Replication console, change the current repository to the new one for each backup job. When you specify a new repository, Veeam Backup & Replication prompts you to move the existing backups to the new repository or keep them on the current one. For details, see the [Specify Backup Storage Settings](https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_storage_vm.html?ver=13) and [Backup Move](https://helpcenter.veeam.com/docs/vbr/userguide/backup_moving.html?ver=13) sections of the Veeam Backup & Replication User Guide.

To edit an organization configuration, do the following:

1. Log in to Veeam Backup Enterprise Manager using an administrative account.
2. Click Configuration in the upper-right corner.
3. In the Configuration view, select the Self-service section.
4. In the Self-service section, select the Cloud Director tab.
5. On the Cloud Director tab, select an organization configuration and click Edit.
6. To edit organization settings, follow the same steps as for adding a configuration.

For more information, see [Adding Organization Configuration](em_configure_vcd_org.md).

![Editing Organization Configuration](images/em_vCD_show_job_settings.webp "Editing Organization Configuration")


