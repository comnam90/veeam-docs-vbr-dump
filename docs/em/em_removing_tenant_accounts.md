---
title: "Removing Tenant Account"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/em_removing_tenant_accounts.html"
last_updated: "10/30/2025"
product_version: "13.0.1.1071"
---


In this article

The Veeam Backup Enterprise Manager administrator can remove tenant accounts configured for vSphere Self-Service Backup Portal.

To remove a tenant account:

1. Log in to Veeam Backup Enterprise Manager using an administrative account.
2. To open the Configuration view, click Configuration in the upper-right corner.
3. In the Configuration view, select the Self-service section.

The Self-service section is available if you have added to Enterprise Manager at least one Veeam backup server with a vCenter Server as part of its infrastructure.

1. If a VMware Cloud Director server is added to your Veeam backup infrastructure, make sure that the vSphere tab is selected.
2. Select the account you want to remove.
3. Click Remove.
4. In the Remove configuration window, select necessary options:

* To delete backup jobs created by the tenant, select the Delete jobs check box.
* To delete all backups created by the tenant, select the Delete backup files check box.

If four-eyes authorization is enabled on the backup server, backup files will remain in the backup repository and become orphaned.

1. To confirm the removal, click Yes.

Page updated 10/30/2025

Page content applies to build 13.0.1.1071
