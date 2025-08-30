# Design-and-Implementation-of-a-Simple-Office-Network

📌 Project Overview

This project demonstrates a basic office network setup using Cisco Packet Tracer.
The network is divided into two departments:

Accounts Department (192.168.40.0/25)

Delivery Department (192.168.40.128/25)

Both departments are connected via a router and configured with proper IP addressing for seamless communication.

🖥️ Network Topology

Router: Cisco 2911

Switches: Cisco 2960-24TT (one for each department)

End Devices:

Accounts Dept: 2 PCs + 1 Printer

Delivery Dept: 2 PCs + 1 Printer

Connections

Router Gig0/0 → Accounts Switch (Fa0/1)

Router Gig0/1 → Delivery Switch (Fa0/1)

PCs and Printers connected to their respective departmental switches.


⚙️ IP Addressing Scheme
Department	Network Address	Subnet Mask	Range	Router Interface
Accounts	192.168.40.0	255.255.255.128	192.168.40.1 – 192.168.40.126	192.168.40.1 (Gig0/0)
Delivery	192.168.40.128	255.255.255.128	192.168.40.129 – 192.168.40.254	192.168.40.129 (Gig0/1)



Router> enable
Router# configure terminal

! Configure Accounts Dept (Gig0/0)
Router(config)# interface gigabitEthernet 0/0
Router(config-if)# ip address 192.168.40.1 255.255.255.128
Router(config-if)# no shutdown
Router(config-if)# exit

! Configure Delivery Dept (Gig0/1)
Router(config)# interface gigabitEthernet 0/1
Router(config-if)# ip address 192.168.40.129 255.255.255.128
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# exit
Router#


✅ Testing

Assign IP addresses to all PCs and Printers within the subnet ranges.

Use the ping command to test:

PC ↔ Printer in the same department

PC in Accounts ↔ PC in Delivery (via Router)

Example:

PC0> ping 192.168.40.130


This should succeed, proving inter-department connectivity.


