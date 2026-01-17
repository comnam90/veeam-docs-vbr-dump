---
title: "Rental Machines Licensing"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_rental_lic.html"
last_updated: "11/9/2023"
product_version: "13.0.1.1071"
---

# Rental Machines Licensing


Tenant machines backed up with a Rental Veeam Backup & Replication license installed on the tenant backup server do not consume the Veeam Cloud Connect license installed on the SP backup server.

* If a tenant backs up a server or workstation with Veeam Agent that uses a rental license, the SP can host cloud backups of that server or workstation with no additional license fee for Veeam Cloud Connect Backup.

* Likewise, if a tenant backs up a VM with a Rental Veeam Backup & Replication license, the SP can host cloud backups of that VM with no additional license fee for Veeam Cloud Connect Backup.

With this functionality, SPs who manage Veeam backup infrastructure on the tenant side can deliver a complete managed backup service, including backup to the cloud, for a single license fee based on the protected machine type, regardless of its size. There is no need to pay an additional license fee for Veeam Cloud Connect Backup.

Tenant machines are considered as rental machines in case the tenant creates a backup in a cloud repository of the SP in the following way:

* Creates a VM backup with a backup job configured in Veeam Backup & Replication.
* Creates a backup of a physical or virtual machine with a Veeam Agent backup job.
* Creates a copy of a VM backup with a backup copy job configured in Veeam Backup & Replication.
* Creates a copy of a Veeam Agent backup with a backup copy job configured in Veeam Backup & Replication.

Veeam Backup & Replication running on the SP backup server counts rental machines according to the following rules:

* Rental machines do not consume the Points counter in the SP license.
* Rental machines are not included in monthly license usage reports for the SP license.
* Rental machines appear in tenant machine counts in the SP backup console and [Veeam Cloud Connect report](cc_report.md).

For example, Tenant 1 uses Veeam Backup & Replication and Veeam Agent for Microsoft Windows with rental licenses installed to back up 2 VMs and 1 server to the cloud repository. Tenant 2 uses Veeam Backup & Replication and Veeam Agent for Microsoft Windows with subscription licenses installed to back up 6 VMs and 2 servers to the cloud repository. In this case, the SP license will be consumed by 6 backed-up VMs and 2 servers processed by Tenant 2. 2 VMs and 1 server processed by Tenant 1 will be considered as rental machines and will not appear in the SP license.

In the tenant machine counts of the SP backup console, as well as in the SP Veeam Cloud Connect report, Veeam Backup & Replication will display the total number of 8 backed-up VMs and 3 servers — the number of machines processed by Tenant 2 plus the number of rental machines processed by Tenant 1.


