---
title: "Appendix A. Deprecated Functionality"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_maintenance_settings.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# Appendix A. Deprecated Functionality


Starting from version 7, Veeam Plug-in for oVirt KVM comes without the backup appliance that was previously used to perform management operations, process jobs and deliver backup traffic. The functionality of backup appliance is now integrated into the backup server.

When upgrading to 7, you will be prompted to copy backup appliance configuration settings to the Veeam Backup & Replication configuration database. After the migration is complete, the backup appliance VM will be removed, and a worker will be deployed instead. For more information on on upgrading to 7, see [Upgrading to Veeam Plug-In for oVirt KVM 7](ovirt_upgrading.md).


