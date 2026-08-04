---
title: "Converting Restored Standalone Instance to Cluster"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/vep_restoring_instance_convert_to_cluster.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Converting Restored Standalone Instance to Cluster


When you restore a Linux-based PostgreSQL instance that belongs to a Patroni high-availability cluster, Veeam Explorer for PostgreSQL restores it as a standalone instance. The restore operation removes the existing patroni.dynamic.json file from the instance and other existing cluster metadata in the PostgreSQL directory.

To convert the restored standalone instance to a cluster, do the following:

1. Stop the Patroni service.
2. Update the Patroni configuration file of the instance (for example, /etc/patroni/patroni.yml). Configure the global settings, DCS backend, bootstrap settings and so on. For more information, see the [Patroni documentation](https://patroni.readthedocs.io/en/latest/yaml_configuration.html).
3. Set ownership and permissions on the PostgreSQL data directory:

|  |
| --- |
| sudo chown -R postgres:postgres /var/lib/postgresql/<version>/main sudo chmod 700 /var/lib/postgresql/<version>/main |

where <version> is the major version of PostgreSQL.

1. Remove stale state files:

|  |
| --- |
| sudo -u postgres rm -f /var/lib/postgresql/<version>/main/postmaster.pid |

1. Start the Patroni service. For the restored data to be preserved, the instance must become the cluster leader — otherwise, the instance joins as a replica and is re-cloned from the current leader.

Page updated 2026-07-22

