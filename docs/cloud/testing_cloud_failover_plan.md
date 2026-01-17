---
title: "Testing Cloud Failover Plan"
product: "vbr"
doc_type: "cloud"
source_url: "https://helpcenter.veeam.com/docs/vbr/cloud/testing_cloud_failover_plan.html"
last_updated: "12/20/2024"
product_version: "13.0.1.1071"
---

# Testing Cloud Failover Plan


You can test a cloud failover plan to ensure replicated VMs on the cloud host successfully start and can be accessed from external network after failover. When you test a cloud failover plan, Veeam Backup & Replication does not switch from a production VM to its replica. Instead, it reverts every VM replica in the cloud failover plan to the latest restore point, boots the replica operation system, waits for the VM replica to reach a "stabilization point" using the Stabilization by IP algorithm and checks if the VM replica responds to ping requests.

When the test operation is started by the tenant, Veeam Backup & Replication running on the tenant backup server does not communicate with VM replicas on the cloud host directly. Instead, Veeam Backup & Replication passes the command to start the test to the SP backup server, and performs operations with tenant VM replicas from the SP backup server.

This operation is supported for cloud failover plans that contain snapshot-based replicas and failover plans that contain CDP replicas.

|  |
| --- |
| Note |
| Consider the following limitations:   * Veeam Backup & Replication does not support this operation for failover plans that contain CDP replicas with I/O filters older than version 12.1 installed on the cluster where the VMs that you plan to protect reside and where replicas will reside. To learn more about updating I/O filters, see the [Updating and Uninstalling I/O Filter](https://helpcenter.veeam.com/docs/backup/vsphere/cdp_io_filter_remove.html?ver=120) section in the Veeam Backup & Replication User Guide. * If the SP starts the cloud failover plan test for CDP replicas created with VBR version 12.2 (or earlier), long-term retention policy creation will be stopped while testing. |

|  |
| --- |
| Tip |
| To keep CDP replica VMs running, for example, to reach data from the VM or from an application installed on the VM, you can use Veeam PowerShell cmdlets. To perform the operation, use the KeepAlive parameter. For detailed instructions, see the [Start-VBRFailoverPlan](https://helpcenter.veeam.com/docs/backup/powershell/start-vbrfailoverplan.html?ver=120) section in the Veeam PowerShell Reference.  The following limitations apply to the operation:   * You can use the keep alive mode only for cloud failover plans that contain CDP replicas. This operation is not supported for cloud failover plans that contain snapshot-based replicas.  * By default, this operation is available only for the SP. The SP can use a registry key to allow this operation to the tenant. The SP must configure the allowed keep alive time for their tenants by a registry key CdpTenantTestFailoverKeepAliveDurationLimitMin. For details, see [Allowing Tenants to Keep CDP Replicas Running](cloud_failover_plan_test_sp.md#keepalive). |

To test a cloud failover plan:

1. Open the Home view.
2. In the inventory pane, expand the Replicas node and click Failover Plans.
3. In the working area, right-click the necessary cloud failover plan and select Test.

[![Test Cloud Failover Plan](images/test_cloud_failover_plan.webp)](images/test_cloud_failover_plan.webp "Test Cloud Failover Plan")


