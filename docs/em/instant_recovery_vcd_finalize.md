---
title: "Finalizing Instant Recovery to VMware Cloud Director"
product: "vbr"
doc_type: "em"
source_url: "https://helpcenter.veeam.com/docs/vbr/em/instant_recovery_vcd_finalize.html"
last_updated: "9/2/2025"
product_version: "13.0.1.1071"
---

# Finalizing Instant Recovery to VMware Cloud Director


After you have performed instant recovery, you have to finalize the process. For this, test the recovered VMs and decide whether to migrate them to production environment or stop publishing.

Until you finalize instant recovery of all recovered VMs, a notification about running instant recovery sessions is displayed on the Dashboard tab.

Testing Recovered VM

To test a recovered VM before you migrate it to production, you can launch the VMware Remote Console software from the Veeam Backup & Replication console. For more information, see the [Finalizing Instant Recovery to VMware vSphere](https://helpcenter.veeam.com/docs/vbr/userguide/vcloud_instant_to_vcd_finalize.html?ver=13#test) section of the Veeam Backup & Replication User Guide.

Migrating Recovered VM

If a VM is recovered successfully, you can migrate it to the production environment.

To migrate a recovered VM to production, do the following:

1. Open the Instant Recovery tab and select the necessary VMware Cloud Director VM from the list.
2. On the toolbar, click Migrate to production.

[![Migrating Recovered VM](images/instant_recovery_vcd_migrate.webp)](images/instant_recovery_vcd_migrate.webp "Migrating Recovered VM")

1. At the Destination step of the VMware Cloud Director Quick Migration wizard, specify a VM storage policy and a datastore. You can choose from the storage policies and datastores that are available in the organization VDC hosting the vApp to which the VM is recovered.

[![Specifying Destination Settings](images/instant_recovery_vcd_migrate_destination.webp)](images/instant_recovery_vcd_migrate_destination.webp "Specifying Destination Settings")

1. At the Ready step of the wizard, review migration settings and click Finish.

[![Specifying Destination Settings](images/instant_recovery_vcd_migrate_ready.webp)](images/instant_recovery_vcd_migrate_ready.webp "Specifying Destination Settings")

To view the migration progress, on the Machines tab, click History.

Unpublishing Recovered VM

If your tests have failed, you can stop publishing the recovered VM. This will remove the recovered VM from the host that you selected as the destination for recovery. Note that all changes made in the recovered VMs will be lost.

To remove a recovered VM, do the following:

1. Open the Instant Recovery tab and select the necessary VMware Cloud Director VM from the list.
2. On the toolbar, click Stop Publishing.

[![Unpublishing Recovered VM](images/instant_recovery_vcd_stop_publishing.webp)](images/instant_recovery_vcd_stop_publishing.webp "Unpublishing Recovered VM")


