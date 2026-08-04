---
title: "EC2 Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_restore_hiw_ec2.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# EC2 Restore


Veeam Plug-in for AWS offers the following restore options:

* [Instance restore](aws_restore_hiw_ec2_entire.md) — restores an entire EC2 instance from a cloud-native snapshot, snapshot replica or an image-level backup. You can restore one or more EC2 instances at a time, to the original location or to a new location.
* [Volume restore](aws_restore_hiw_volume.md) — restores EBS volumes attached to an EC2 instance from a cloud-native snapshot, snapshot replica or an image-level backup. You can restore EBS volumes to the original location or to a new location.
* [File-level recovery](aws_restore_hiw_file_level.md) — recovers individual files and folders of an EC2 instance from a cloud-native snapshot, snapshot replica or an image-level backup. You can download the necessary files and folders to a local machine, or restore the files and folders of the source EC2 instance to the original location.

You can restore EC2 instance data to the most recent state or to any available restore point.

Page updated 2026-05-15

