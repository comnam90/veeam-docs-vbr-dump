---
title: "Step 5. Configure Replication Network Settings"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_replication_job_create_network.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Step 5. Configure Replication Network Settings


[This step applies only if you have selected the Network remapping check box at the Name step of the wizard]

At the Network step of the wizard, configure a network mapping table.

By default, replica VMs are connected to the same Proxmox VE networks as the original VMs; if the same networks are not available in the disaster recovery (DR) site, you can create a network mapping table for the site so that the replicas are connected to the correct network. When the replication session starts, Veeam Backup & Replication will update replica configuration to replace the production networks with the specified networks in the DR site.

[![Network mapping](images/pve_replication_job_create_network.webp)](images/pve_replication_job_create_network.webp "Network mapping")

Page updated 2026-06-18

