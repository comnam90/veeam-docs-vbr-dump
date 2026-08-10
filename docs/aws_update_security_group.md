---
title: "Step 4. Update Security Group"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/aws_update_security_group.html"
last_updated: "2025"
product_version: "13.1.0.411"
---

# Step 4. Update Security Group


To allow inbound traffic to the backup appliance from the on-premises network, update the security group for the appliance VPC:

1. In the Amazon VPC console, navigate to
   Security
    >
   Security Groups
   .
2. In the
   Security Group
    list, choose the default security group and click
   Actions
    >
   Edit Inbound Rules
   .
3. In the
   Edit inbound rules
    wizard, click
   Add rule
   , add a new inbound rule for the SSH, RDP and ICMP protocols, and click
   Save rules
   .

To learn how to add security group rules, see
[AWS Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/security-group-rules.html#working-with-security-group-rules)
.

Page updated 2025-10-10

