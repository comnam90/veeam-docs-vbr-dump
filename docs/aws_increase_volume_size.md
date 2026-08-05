---
title: "Appendix G. Increasing Volume Size of Backup Appliances"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_increase_volume_size.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Appendix G. Increasing Volume Size of Backup Appliances


To ensure proper operation, backup appliances regularly check free space on their EBS volumes and notify you when it is running low.

Specifically, a backup appliance includes the following volumes:

* System volume — the root EBS volume attached to the backup appliance.
* Data volume — the EBS volume where the backup appliance stores its configuration database.

You can monitor the state of each EBS volume on the Overview dashboard. For more information, see [Viewing Dashboard](aws_dashboard.md).

Increasing System Volume Size

If the configuration backup file on the system volume grows too large, open a [support case](https://helpcenter.veeam.com/docs/vbaws/guide/logs.html) to remove the unnecessary data from the volume. It is not recommended that you increase the volume size in the AWS Management Console manually.

Increasing Data Volume Size

If the configuration database on the data volume grows too large and data volume usage reaches 85%, the backup appliance sends a notification. To increase the volume size, do the following:

|  |
| --- |
| Important |
| Before modifying the volume size, it is recommended that you create a snapshot of the data volume in case you need to roll back the changes. For more information, see [AWS Documentation](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-creating-snapshot.html). |

1. Log in to the AWS Management Console using credentials of the AWS account to which the backup appliance belongs.
2. Navigate to All Services > Compute and click EC2.
3. In the Amazon EC2 console, navigate to Elastic Block Store and click Volumes.
4. Select the volume that you want to modify and click Actions > Modify volume.
5. On the Modify volume page, enter the new value in the Size field and click Modify.
6. After the modification completes, extend the file system of the data volume to use the additional storage capacity, as described in [AWS Documentation](https://docs.aws.amazon.com/ebs/latest/userguide/recognize-expanded-volume-linux.html).

|  |
| --- |
| Note |
| If no action is taken to increase the volume size and data volume usage reaches 90%, the backup appliance runs an automatic log cleanup mechanism to remove older log files, which allows you to free up 15% of volume space and ensure proper operation. However, it is not recommended that you rely on this mechanism regularly, since log files are helpful in troubleshooting backup appliance issues. |

Page updated 2026-07-22

