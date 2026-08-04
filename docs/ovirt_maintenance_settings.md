---
title: "Appendix A. Deprecated Functionality"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_maintenance_settings.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix A. Deprecated Functionality


Starting from version 7, Veeam Plug-in for oVirt KVM comes without the backup appliance that was previously used to perform management operations, process jobs and deliver backup traffic. The functionality of backup appliance is now integrated into the backup server.

When upgrading to 8 from version 6, you will be prompted to copy backup appliance configuration settings to the Veeam Backup & Replication configuration database. After the migration is complete, the backup appliance VM will be removed, and a worker will be deployed instead. For more information on upgrading to 8, see [Upgrading to Veeam Plug-In for oVirt KVM 8](ovirt_upgrading.md).

Page updated 2026-07-24

