---
title: "SureBackup Job Processing"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_job_processing_vm.html"
last_updated: "8/20/2024"
product_version: "13.0.1.1071"
---

# SureBackup Job Processing

In this article

SureBackup job processing depends on the verification mode, Full recoverability testing mode or Backup verification and content scan only mode.

Full recoverability testing

The recovery verification process includes the following steps:

1. Getting virtual lab configuration. Veeam Backup & Replication gets information about configuration of the virtual lab where verified VMs must be started.
2. Starting virtual lab routing engine. Veeam Backup & Replication starts a proxy appliance used as a gateway to provide access to the virtual lab.
3. Performing malware scan. If the recovery verification process includes malware scan, Veeam Backup & Replication scans VM data with antivirus software.

After the malware scan is complete, Veeam Backup & Replication registers the VM on the selected ESXi host, powers it on, and runs recovery verification tests for this VM.

Veeam Backup & Replication verifies VMs sequentially — one after another. For example, when the malware scan and recovery verification tests for VM A complete, Veeam Backup & Replication verifies VM B, and so on.

1. Publishing. Veeam Backup & Replication creates a vPower NFS datastore with a VM backup and registers it on the selected ESXi server. Veeam Backup & Replication does not deploy the whole VM from the backup file, it deploys VM configuration files only. Virtual disks are deployed per force and per required data blocks.
2. Reconfiguring. Veeam Backup & Replication updates configuration files for VMs that must be started in the isolated network.
3. Registering. Veeam Backup & Replication registers the verified VM on the selected ESXi host.
4. Configuring DC. If a verified VM has the Domain Controller or Global Catalog role, the VM is reconfigured.
5. Powering on. Veeam Backup & Replication powers on the verified VM in the isolated network.
6. Performing heartbeat test. Veeam Backup & Replication checks whether the VMware Tools heartbeat signal (green or yellow) is coming from the VM or not. If the VM has no VMware Tools, the test is not performed, and a notification is written to the session details.
7. Running ping tests. Veeam Backup & Replication checks if the VM responds to the ping requests or not. If the VM has no NICs and mapped networks for them and has no VMware Tools installed, the ping test is not performed, and a notification is written to the session details.
8. Application initialization. Veeam Backup & Replication waits for the applications installed in the VM, for example, Microsoft SQL Server, to start. The application initialization period is defined in settings of the SureBackup job and by default equals to 120 sec. Depending on the software installed in a VM, the application initialization process may require more time than specified in the job settings. If applications installed in a VM are not initialized within the specified period of time, test scripts can be completed with errors. If such an error situation occurs, you need to increase the Application initialization timeout value and start the job once again.
9. Running test scripts. Veeam Backup & Replication runs scripts to test whether the application installed in the VM is working correctly or not. If the VM has no VMware Tools installed or there are no NICs and mapped networks for them, Veeam Backup & Replication skips tests that use the %vm\_ip% and %vm\_fqdn% variables as the IP address and FQDN of the VM cannot be determined.

Test results are written to the job session details. To define whether the script is completed successfully or not, Veeam Backup & Replication uses return codes. If the return code is equal to 0, the script is considered to complete successfully. Other values in the return code mean that the script failed.

1. Powering off. After all tests were performed, Veeam Backup & Replication powers off the verified VM.
2. Unregistering. Veeam Backup & Replication unregisters the verified VM on the selected ESXi host.
3. Clearing redo logs. Veeam Backup & Replication deletes redo logs from the datastore in the production environment. Redo logs store changes made to the VM while it is running from the backup file.
4. Unpublishing. Veeam Backup & Replication unpublishes the content of the backup file on the ESXi host.
5. Running backup validation test. After a VM was verified, powered off and unpublished, Veeam Backup & Replication runs a CRC check to verify the VM backup at the file level and make sure that this file is not corrupted.
6. Stopping virtual lab engine. Veeam Backup & Replication powers off the proxy appliance in the virtual lab.
7. Deleting network routes. Veeam Backup & Replication deletes added network routes from the routing table on the backup server.

Stabilization Algorithm

Stabilization algorithm is the same for both recovery verification modes. To be able to perform tests for a verified VM without errors, Veeam Backup & Replication needs to know that the VM is ready for testing. To determine this, Veeam Backup & Replication waits for the VM to reach a stabilization point: that is, waits for the VM to boot completely and report it is ready for tests. After the stabilization point has been established, Veeam Backup & Replication can start performing heartbeat tests, ping tests and running test scripts against the VM.

Veeam Backup & Replication establishes the stabilization point with the help of VMware parameters that it gets from the VM. Depending on the VM configuration, it uses one of three algorithms to do that:

* Stabilization by IP. This algorithm is used if the VM has VMware Tools installed, there are NICs and mapped networks for these NICs. In this case, Veeam Backup & Replication waits for an IP address of the VM for mapped networks that is sent by VMware Tools running in the VM. The sent IP address must be valid and must not change for a specific period of time. For more information, see [Backup Recovery Verification Tests](surebackup_tests.md).
* Stabilization by heartbeat. This algorithm is used if the VM has VMware Tools installed but there are no vNICs and mapped networks for them. In this case, Veeam Backup & Replication waits for a green or yellow heartbeat signal from the VM. The signal is sent by VMware Tools running in the VM.
* Stabilization by Maximum allowed boot time. This algorithm is used if the VM has neither VMware Tools installed, nor NICs and mapped networks for them. In this case, Veeam Backup & Replication waits for the time specified in the Maximum allowed boot time field, which is considered to be a stabilization period for the VM. Once this time interval is exceeded, Veeam Backup & Replication considers that the VM runs successfully and it is ready for testing.

When the stabilization point has been established, Veeam Backup & Replication runs ping, heartbeat tests and performs test scripts against the verified VM.

The stabilization process cannot exceed the time specified in the Maximum allowed boot time field. For this reason, you should be careful when specifying this value. Typically, a VM started by a SureBackup job requires more time to boot than a VM started in the production environment. If the stabilization point cannot be determined within the Maximum allowed boot time, the recovery verification process is finished with the timeout error. When such an error occurs, you need to increase the Maximum allowed boot time value and start the job again.

Backup verification and content scan only

The recovery verification process includes the following steps:

1. Performing malware scan. If the recovery verification process includes malware scan and YARA rule scan, Veeam Backup & Replication scans VM data with antivirus software and the YARA rule.

Veeam Backup & Replication verifies VMs sequentially — one after another. For example, when the malware scan and recovery verification tests for VM A complete, Veeam Backup & Replication verifies VM B, and so on.

1. Running backup integrity check. Veeam Backup & Replication runs a CRC check to verify the VM backup at the file level and make sure that this file is not corrupted.

Page updated 8/20/2024

Page content applies to build 13.0.1.1071
