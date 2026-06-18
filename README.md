# OPNsense Firewall Lab

## Project Overview

This project documents the deployment of OPNsense as a virtual firewall using VMware Workstation. The goal of the lab was to gain hands-on experience with firewall administration, routing, DHCP, DNS, and network segmentation while building and troubleshooting a secure virtual network environment.

## Goals

* Deploy OPNsense in VMware Workstation
* Configure WAN and LAN interfaces
* Configure DHCP and DNS services
* Implement and validate firewall rules
* Troubleshoot routing and connectivity issues
* Document lessons learned and solutions

## Lab Environment

* VMware Workstation Pro
* OPNsense
* Windows Host
* Ubuntu Client VM
* VMware VMnet8 WAN/NAT Network
* VMware VMnet1 LAN Network

## Skills Demonstrated

* Firewall Administration
* Routing Fundamentals
* DHCP Configuration
* DNS Configuration
* Network Segmentation
* Network Troubleshooting
* Virtualization
* VMware Workstation

---

## Final Working Environment

The completed lab successfully routed traffic between isolated LAN and WAN networks using OPNsense as the primary firewall. DHCP, DNS, routing, and firewall policies were configured and validated through connectivity testing and firewall log analysis.

<img src="screenshots/01-opnsense-dashboard.png" width="800">

---

## Network Diagram

```text
             Internet
                 │
                 ▼
          VMware NAT
           VMnet8
                 │
                 ▼
    ┌────────────────────┐
    │      OPNsense      │
    │                    │
    │ WAN: 192.168.83.x  │
    │ LAN: 192.168.168.2 │
    └────────────────────┘
                 │
                 ▼
            VMnet1 LAN
                 │
                 ▼
    ┌────────────────────┐
    │   Ubuntu Client    │
    │ 192.168.168.128    │
    └────────────────────┘
```

---

## Initial Deployment

The firewall was deployed as a virtual machine with separate WAN and LAN interfaces. VMware NAT networking was used for WAN connectivity while a dedicated host-only network was used for the internal LAN segment.

<img src="screenshots/vmware-hardware-config.png" width="700">

<img src="screenshots/03-opnsense-interface-assignment-success.png" width="700">

---

## Network Services Configuration

The LAN interface was configured with a dedicated subnet and DHCP services were deployed to automatically assign addresses to client systems.

<img src="screenshots/04-opnsense-lan-configuration.png" width="700">

<img src="screenshots/opnsense-dhcp-scope-config.png" width="700">

---

## Problem Encountered

Following deployment, the Ubuntu client was unable to reach external networks. Initial testing showed that internet-bound traffic could not leave the LAN segment.

<img src="screenshots/troubleshooting/network-is-unreachable.png" width="700">

---

## Investigation

Troubleshooting focused on validating interface assignments, routing information, DHCP configuration, and client network settings.

Reviewing the Ubuntu routing table revealed that the client was missing a default route, preventing traffic from reaching external networks.

<img src="screenshots/troubleshooting/ubuntu-missing-default-route.png" width="700">

Further investigation confirmed that DHCP configuration and interface assignments required correction before proper routing could occur.

<img src="screenshots/troubleshooting/interface-assignment-error.png" width="700">

---

## Resolution

After correcting the interface configuration and DHCP settings, the Ubuntu client successfully received a valid gateway, DNS server, and domain information from OPNsense.

<img src="screenshots/troubleshooting/ubuntu-received-dhcp-from-opnsense.png" width="700">

---

## Firewall Validation

A custom firewall rule was created to block DNS traffic to Google's public DNS server (8.8.8.8). Firewall logs confirmed that traffic was being inspected and filtered according to the configured policy.

<img src="screenshots/05-opnsense-firewall-rule-order.png" width="700">

<img src="screenshots/opnsense-firewall-block-log-google.png" width="700">

---

## Connectivity Validation

Final testing confirmed successful communication between the Ubuntu client, the OPNsense firewall, and external network resources.

<img src="screenshots/06-ubuntu-firewall-rule-validation.png" width="700">

---

## Lessons Learned

* Proper interface assignment is critical for successful routing.
* DHCP configuration issues can appear as general connectivity failures.
* Missing default routes prevent hosts from reaching external networks.
* Firewall rules should always be validated through testing and log analysis.
* Structured troubleshooting helps isolate issues more efficiently than making configuration changes at random.

## Next Steps

* Implement VLAN segmentation
* Expand the lab with additional client systems
* Configure centralized logging
* Explore IDS/IPS functionality
* Integrate additional security monitoring tools
