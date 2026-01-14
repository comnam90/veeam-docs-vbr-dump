---
title: "Configuring Jobs with Microsoft SQL Server VMs"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sql_job_reconfigure_hv.html"
last_updated: "10/20/2025"
product_version: "13.0.1.1071"
---

# Configuring Jobs with Microsoft SQL Server VMs

In this article

In some situations, you may need to modify a backup job that processes Microsoft SQL Server VMs and ships transaction logs. For example, you may want to create a separate backup job to process the virtualized database and then delete the VM running the database from the previously created job.

When you configure a new backup job, consider the restriction on transaction log shipping. By default, the new backup job that processes the VM will not ship transaction logs if another backup job on the same backup server has shipped the transaction logs for this VM for the last 7 days.

You can overcome this restriction by setting the value in the in the configuration file on the Linux-based backup server or with a registry value on the Microsoft Windows-based backup server. For more information, contact [Veeam Customer Support](https://www.veeam.com/support.html).

Page updated 10/20/2025

Page content applies to build 13.0.1.1071
