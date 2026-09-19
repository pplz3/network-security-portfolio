# 🌐 Network Lab

## 📌 Objective

Build and document a small enterprise network
using VLANs, routing, DHCP and ACL.

## 🏗️ Network Topology

```text
Internet
   |
 Router
   |
 Switch
   |
   +---- VLAN 10 - Users
   |
   +---- VLAN 20 - Servers
   |
   +---- VLAN 30 - Management
   
   | VLAN | Name       | Network         |
| ---- | ---------- | --------------- |
| 10   | Users      | 192.168.10.0/24 |
| 20   | Servers    | 192.168.20.0/24 |
| 30   | Management | 192.168.30.0/24 |
