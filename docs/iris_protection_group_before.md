---
title: "Before You Begin"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/iris_protection_group_before.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Before You Begin


Before creating a protection group, consider the following prerequisites and limitations:

1. Ensure that ODB servers, InterSystems IRIS instances, file systems, backup proxies, and storage systems meet the requirements. For details on requirements, see [System Requirements](iris_plan_and_manage_requirements.md).
2. Register the storage system that hosts the Epic EHR System Protection data volumes in Veeam Backup & Replication with the Block storage for application protection role before performing storage snapshot backup operations. For details, see [Registering Storage System for Application Protection](iris_storage_registration.md).
3. Make sure that every ODB server is powered on, reachable, and has valid credentials during discovery. During this process, Veeam Backup & Replication deploys the Veeam Transport service, the certificate, and the InterSystems IRIS application to each ODB server via SSH or by using the Deployment Kit. For more information, see [Computer Discovery and Veeam Components Deployment](iris_discovery_and_deployment.md).
4. Add ODB servers only by static IP address. Do not use a dynamic IP address.

Page updated 2026-07-28

