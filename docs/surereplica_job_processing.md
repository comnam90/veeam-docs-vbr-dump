---
title: "SureBackup Job for VM Replicas Processing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surereplica_job_processing.html"
last_updated: "6/8/2023"
product_version: "13.0.1.1071"
---

# SureBackup Job for VM Replicas Processing


The recovery verification process for VM replicas includes the following steps:

1. Getting virtual lab configuration. Veeam Backup & Replication gets information about configuration of the virtual lab where verified VM replicas must be started.
2. Starting virtual lab routing engine. Veeam Backup & Replication starts a proxy appliance. The proxy appliance is used as a gateway that provides access to VM replicas the virtual lab.
3. Publishing. Veeam Backup & Replication triggers a protective VMware snapshot for the verified VM replica.
4. Reconfiguring. Veeam Backup & Replication updates configuration files of the VM replica to connect the VM replica to the isolated network in the virtual lab.
5. Configuring DC. If the VM replica has the Domain Controller or Global Catalog role, the VM replica is reconfigured.
6. Powering on. Veeam Backup & Replication powers on the VM replica in the isolated network.
7. Heartbeat test. Veeam Backup & Replication checks whether the green or yellow VMware Tools heartbeat signal is coming from the VM replica or not. If the VM replica has no VMware Tools, the test is not performed and a notification is written to the session details.
8. Running ping tests. Veeam Backup & Replication checks if the VM replica responds to the ping requests or not. If the VM replica has no NICs and mapped networks for them and has no VMware Tools installed, the ping test is not performed and a notification is written to the session details.
9. Application initialization. Veeam Backup & Replication waits for applications installed in the VM replica, for example, Microsoft SQL Server, to start. The application initialization period is defined in the properties of the SureBackup job and by default is equal to 120 sec. Depending on the software installed in a VM, the application initialization process may require more time than specified in the SureBackup job settings. If applications installed in a VM are not initialized within the specified period of time, test scripts can be completed with errors. If such error situation occurs, you need to increase the Application initialization timeout value and start the job once again.
10. Running test scripts. Veeam Backup & Replication runs scripts to test whether the application installed in the VM replica is working correctly or not. If the VM replica has no VMware Tools installed and there are no NICs and mapped networks for them, Veeam Backup & Replication skips tests that use variables %vm\_ip% and %vm\_fqdn%, as the IP address of the VM cannot be determined. Test results are written to the session details. To define whether the script has completed successfully or not, Veeam Backup & Replication uses return codes. If the return code is equal to 0, the script is considered to complete successfully. Other values in the return code mean that the script has failed.
11. Powering off. After all tests have been performed, Veeam Backup & Replication powers off the verified VM replica.
12. Unpublishing. Veeam Backup & Replication deletes the protective VMware snapshot and rollbacks all changes made to the VM replica while it was running in the virtual lab.
13. Stopping virtual lab engine. Veeam Backup & Replication powers off the proxy appliance in the virtual lab.

Stabilization Algorithm

To perform tests for a VM replica without errors, Veeam Backup & Replication needs to know that the VM replica is ready for testing. To determine this, Veeam Backup & Replication waits for the VM replica to reach a "stabilization point": — the moment when the VM replica booted and reports it is ready for tests. After the stabilization point has been reached, Veeam Backup & Replication can start heartbeat tests, ping tests and test scripts against the VM replica.

Veeam Backup & Replication establishes the stabilization point with the help of VMware parameters that it gets from the VM replica. Depending on the VM replica configuration, it uses one of the three algorithms:

* Stabilization by IP. This algorithm is used if the VM replica has VMware Tools installed, there are NICs and mapped networks for these NICs. In this case,Veeam Backup & Replication waits for an IP address of the VM replica for mapped networks that is sent by VMware Tools running in the VM replica. The sent IP address must be valid and must not change for a specific period of time.

* Stabilization by heartbeat. This algorithm is used if the VM replica has VMware Tools installed but there are no NICs and mapped networks for them. In this case, Veeam Backup & Replication waits for the green or yellow heartbeat signal from VMware Tools installed inside the VM replica.

* Stabilization by Maximum allowed boot time. This algorithm is used if the VM replica has neither VMware Tools installed, nor NICs and mapped networks for them. In this case, Veeam Backup & Replication will wait for the time specified in the Maximum allowed boot time field, which is considered to be a stabilization period for the VM replica. Once this time interval is exceeded, Veeam Backup & Replication considers that the VM replica is successfully booted and is ready for testing.

Once the stabilization point has been established, Veeam Backup & Replication runs ping, heartbeat tests and test scripts against the verified VM replica.

The stabilization process cannot exceed the value specified in the Maximum allowed boot time field. If the stabilization point cannot be determined within the Maximum allowed boot time, the recovery verification process will be finished with the timeout error. For this reason, you should be careful when specifying this value. Typically, a VM replica started by a recovery verification job requires more time to boot that a VM started regularly. When such error situation occurs, you need to increase the Maximum allowed boot time value and start the job again.


