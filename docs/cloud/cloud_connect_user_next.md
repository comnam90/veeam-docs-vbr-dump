---
title: "What You Do Next"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/cloud_connect_user_next.html"
last_updated: "10/24/2023"
product_version: "13.0.1.1071"
---


In this article

After the SP creates a tenant account, the SP must communicate the following information to the tenant:

1. User name and password for the created account.
2. Full DNS name or IP address of the cloud gateway over which the tenant will communicate with the Veeam Cloud Connect infrastructure:

* If the SP did not assign a cloud gateway pool to the tenant, the SP can provide information about any cloud gateway configured in the Veeam Cloud Connect infrastructure that is not part of a cloud gateway pool. When the tenant adds the SP in the tenant Veeam backup console, the Veeam backup server on tenant side will obtain a list of all cloud gateways that are not added to a cloud gateway pool. If the primary cloud gateway is unavailable, the Veeam backup server on the tenant side will fail over to another cloud gateway from the list.
* If the SP assigned a cloud gateway pool to the tenant, the SP can provide information about any cloud gateway added to this gateway pool. When the tenant adds the SP in the tenant Veeam backup console, the Veeam backup server on tenant side will obtain a list of all cloud gateways in the pool. If the primary cloud gateway is unavailable, the Veeam backup server on the tenant side will fail over to another cloud gateway in the same pool.

1. External port for the cloud gateway (if the SP has specified a non-default port).
2. [If Dell Data Domain is used as a cloud repository] Information about the backup chain limitations. The length of forward incremental and forever forward incremental backup chains that contain one full backup and a set of subsequent incremental backups cannot be greater than 120 restore points. To overcome this limitation, tenants can schedule full backups (active or synthetic) to split the backup chain into shorter series. For example, to perform backups at 15-minute intervals, 24 hours a day, tenants must schedule synthetic full backups every day. In this scenario, intervals immediately after midnight may be skipped due to the duration of synthetic processing.

Page updated 10/24/2023

Page content applies to build 13.0.1.1071
