# AWS Two-Tier Cloud Infrastructure & Network Segmentation

## Overview
Design and deployment of a multi-tier enterprise web application on Amazon Linux 2023 EC2 instances within an Amazon Virtual Private Cloud (VPC)[cite: 3]. Demonstrates network isolation, least-privilege access, and defense-in-depth principles by decoupling web execution from persistent data storage[cite: 3].

## Architecture Highlights
* **Bastion Host Access (`Bastion V2`):** Secured SSH administration point (`bastionsg2`) restricting inbound access to designated IP spaces.
* **Web Layer (`hosta-web`):** Apache HTTP Server running PHP-FPM and WordPress, configured to accept HTTP traffic from designated subnets[cite: 2, 3].
* **Isolated Database Tier (`hostb-db`):** Dedicated MariaDB relational database node segmented inside private subnet space[cite: 2, 3].
* **Defense-in-Depth Security Groups:** 
  * `WebserverSG`: Allows HTTP ingress and limits SSH administrative access strictly to the Bastion host[cite: 2].
  * `DBserverSG`: Enforces strict database isolation by restricting MySQL (port 3306) access solely to incoming queries from the Web Server IP[cite: 2, 3].
* **Granular Database Permissions:** Configured dedicated application database user (`wpuser`) with restricted schema privileges, disabling remote root authentication[cite: 3].

## Tech Stack
* **Cloud Infrastructure:** AWS (EC2, VPC, Security Groups, Elastic IPs)[cite: 2, 3]
* **OS:** Amazon Linux 2023[cite: 3]
* **Services:** Apache HTTP Server, MariaDB, PHP-FPM, WordPress[cite: 2, 3]
