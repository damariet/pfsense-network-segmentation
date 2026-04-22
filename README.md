
# 🔐 pfSense Network Segmentation Lab

## 📌 Project Overview

Most home and small business networks operate on a flat architecture, where all devices can communicate freely. This creates significant security risks, as a compromised device can move laterally across the network.

In this project, I designed and implemented a segmented network using pfSense to isolate traffic across multiple VLANs and enforce least privilege access. The goal was to reduce attack surface and prevent unauthorized communication between network segments.

---

## 🏗️ Network Architecture

The network was segmented into four VLANs, each with a dedicated subnet and purpose:

* **VLAN 10 — Trusted** (192.168.10.0/24)
  Personal devices with broader access to network resources

* **VLAN 20 — IoT** (192.168.20.0/24)
  Smart devices isolated to prevent lateral movement

* **VLAN 30 — Guest** (192.168.30.0/24)
  Internet-only access with no internal network visibility

* **VLAN 40 — Servers** (192.168.40.0/24)
  Internal services with restricted inbound access

---

## ⚙️ Technologies Used

* pfSense (Firewall & Routing)
* VMware Workstation (Virtualization)
* VLANs (802.1Q tagging)
* DHCP (per VLAN configuration)
* Firewall Rules (Traffic control & segmentation)

---

## 🔧 Implementation Steps

* Deployed pfSense in a virtualized environment with WAN and LAN interfaces
* Created and configured VLANs on the LAN interface
* Assigned VLANs as interfaces with unique IP subnets
* Configured DHCP servers for each VLAN to automate IP assignment
* Implemented firewall rules to control inter-VLAN and outbound traffic
* Applied least privilege principles to restrict unnecessary communication

---

## 🔒 Firewall Rule Logic

Firewall rules were designed to enforce strict network segmentation:

* **Trusted VLAN**

  * Block access to internal VLANs (192.168.0.0/16)
  * Allow outbound internet access

* **IoT VLAN**

  * Block access to all internal networks
  * Allow internet-only access

* **Guest VLAN**

  * Fully isolated from internal networks
  * Internet access only

* **Servers VLAN**

  * Restricted from initiating connections to other VLANs
  * Limited outbound internet access

---

## 🧪 Verification & Testing

To validate the configuration, connectivity tests were performed:

* ✅ Verified WAN connectivity (successful ping to 8.8.8.8)
* ✅ Confirmed all VLAN interfaces were reachable
* ❌ Verified inter-VLAN traffic was blocked according to firewall rules
* ✅ Confirmed internet access for allowed VLANs

These tests ensured that segmentation and access controls were functioning as intended.

---

## 🧠 Skills Demonstrated

* Network segmentation and VLAN design
* Firewall rule creation and policy enforcement
* pfSense configuration and management
* DHCP and IP addressing
* Network troubleshooting and validation
* Security best practices (least privilege, isolation)

---

## 📸 Screenshots

Screenshots of configuration and testing are included in the `/screenshots` directory.

---

## 🚀 Key Takeaway

This project demonstrates the ability to design and implement a secure, segmented network architecture that reduces risk and enforces controlled access between systems—mirroring real-world enterprise security practices.
