---
title: "SureBackup Job Processing"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/surebackup_job_processing.html"
last_updated: "5/5/2025"
product_version: "13.0.1.1071"
---

# SureBackup Job Processing


SureBackup job processing depends on the verification mode, Full recoverability testing mode or Backup verification and content scan only mode.

Full recoverability testing

The recovery verification process in Full recoverability testing mode includes the following steps:

1. Getting virtual lab configuration. Veeam Backup & Replication gets information about configuration of the virtual lab where verified VMs must be started.
2. Starting proxy appliance VM. Veeam Backup & Replication starts the proxy appliance. The proxy appliance is used as a gateway that provides access to the virtual lab.
3. Configuring network routes. Veeam Backup & Replication adds to the routing table on the backup server new routes for the networks created in the virtual lab.
4. Performing malware scan. If the recovery verification process includes malware scan and YARA rule scan, Veeam Backup & Replication scans VM data with antivirus software and the YARA rule.

After the malware and the YARA scan, Veeam Backup & Replication runs recovery verification tests for this VM.

Veeam Backup & Replication verifies VMs sequentially — one after another. For example, when the malware scan and recovery verification tests for VM A complete, Veeam Backup & Replication verifies VM B, and so on.

1. Preparing application group. In the virtual lab, Veeam Backup & Replication starts VMs from the application group in the specified order and performs necessary tests for them.
2. Performing verification tasks. In the virtual lab, Veeam Backup & Replication starts verified VMs and performs necessary tests for them.
3. Performing heartbeat test. Veeam Backup & Replication checks whether the Hyper-V Integration Services heartbeat signal is coming from the VM or not. If the VM has no Hyper-V Integration Services, the test is not performed and a notification is written to the job session details.
4. Running ping tests. Veeam Backup & Replication checks if the VM responds to the ping requests or not. If the VM has no network adapters or mapped networks for them, the ping test is not performed and a notification is written to the job session details.
5. Application initialization. Veeam Backup & Replication waits for the applications installed in the VM, for example, Microsoft SQL Server, to start. The application initialization period is defined in settings of the SureBackup job and by default is equal to 120 sec.

Depending on the software installed in a VM, the application initialization process may require more time than specified in the job settings. If applications installed in a VM are not initialized within the specified period of time, test scripts can be completed with errors. If such error situation occurs, you will need to increase the Application initialization timeout value and start the job once again.

1. Running test scripts. Veeam Backup & Replication runs scripts to test whether the application installed in the VM is working correctly or not. If there are no network adapters on the VM or mapped networks for them, Veeam Backup & Replication skips tests that use the %vm\_ip% and %vm\_fqdn% variables as the IP address and FQDM of the VM cannot be determined.

Test results are written to the job session details. To define whether the script is completed successfully or not, Veeam Backup & Replication uses return codes. If the return code is equal to 0, the script is considered to complete successfully. Other values in the return code mean that the script failed.

1. Powering off. After all tests were performed, Veeam Backup & Replication powers off the verified VM and unregisters it on the Hyper-V host.
2. Running backup integrity check. After a VM was verified and powered off, Veeam Backup & Replication runs a CRC check to verify the VM backup at the file level and make sure that this file is not corrupted.
3. Stopping virtual lab engine. Veeam Backup & Replication powers off the proxy appliance in the virtual lab.
4. Deleting network routes. Veeam Backup & Replication deletes added network routes from the routing table on the backup server.

Stabilization Algorithm

To be able to perform tests for a verified VM without errors, Veeam Backup & Replication needs to know that the VM is ready for testing. To determine this, Veeam Backup & Replication waits for the VM to reach a stabilization point: that is, waits for the VM to boot completely and report it is ready for tests. After the stabilization point has been established, Veeam Backup & Replication can start performing heartbeat tests, ping tests and running test scripts against the VM.

Depending on the VM configuration, Veeam Backup & Replication establishes the stabilization point using one of three algorithms:

* Stabilization by IP. This algorithm is used if the VM has network adapters and there are mapped networks for these network adapters. In this case, Veeam Backup & Replication waits for an IP address of the VM for mapped networks that is sent by Hyper-V Integration Services running in the VM or by the Hyper-V host through the proxy appliance. The sent IP address must be valid and must not change for a specific period of time. For more information, see [Recovery Verification Tests](surebackup_tests_hv.md).
* Stabilization by heartbeat. This algorithm is used if the VM has Hyper-V Integration Services installed but there are no network adapters and mapped networks for them. In this case, Veeam Backup & Replication waits for a heartbeat signal from Hyper-V Integration Services installed inside the VM.
* Hybrid heartbeat/IP algorithm. Veeam Backup & Replication uses both the heartbeat signal (if available) and an IP of the VM to stabilize the VM boot process.
* Stabilization by Maximum allowed boot time. This algorithm is used if the VM has neither Hyper-V Integration Services installed, nor network adapters and mapped networks for them. In this case, Veeam Backup & Replication waits for the time specified in the Maximum allowed boot time field, which is considered to be a stabilization period for the VM. Once this time interval is exceeded, Veeam Backup & Replication considers that the VM runs successfully and it is ready for testing.

When the stabilization point has been established, Veeam Backup & Replication runs ping, heartbeat tests and performs test scripts against the verified VM.

The stabilization process cannot exceed the time specified in the Maximum allowed boot time field. For this reason, you should be careful when specifying this value. Typically, a VM started by a SureBackup job requires more time to boot than a VM started in the production environment. If the stabilization point cannot be determined within the Maximum allowed boot time, the recovery verification process is finished with the timeout error. When such an error occurs, you need to increase the Maximum allowed boot time value and start the job again.

Backup verification and content scan only

The recovery verification process includes the following steps:

1. Performing malware scan. If the recovery verification process includes malware scan and YARA rule scan, Veeam Backup & Replication scans VM data with antivirus software and the YARA rule.

Veeam Backup & Replication verifies VMs sequentially — one after another. For example, when the malware scan and recovery verification tests for VM A complete, Veeam Backup & Replication verifies VM B, and so on.

1. Running backup integrity check. Veeam Backup & Replication runs a CRC check to verify the VM backup at the file level and make sure that this file is not corrupted.


