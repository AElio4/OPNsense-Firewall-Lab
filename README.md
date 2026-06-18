# OPNsense Firewall Lab

## Project Overview

This project documents the deployment of OPNsense as a virtual firewall using VMware Workstation. The goal of the lab is to gain hands-on experience with firewall administration, routing, NAT, and network segmentation while building a secure virtual network environment.

## Goals

- Deploy OPNsense in VMware Workstation
- Configure WAN and LAN interfaces
- Implement firewall rules
- Configure Network Address Translation (NAT)
- Validate network connectivity
- Explore network segmentation concepts
- Document troubleshooting and lessons learned

## Lab Environment

- VMware Workstation Pro
- OPNsense
- Windows Host
- Virtual WAN Network
- Virtual LAN Network

## What I Built

I deployed OPNsense as a virtual firewall and configured separate WAN and LAN interfaces within VMware Workstation. The lab provided hands-on experience with firewall rule management, routing, NAT configuration, and troubleshooting network connectivity in a virtualized environment.

## Skills Demonstrated

- Firewall Administration
- Routing Fundamentals
- NAT Configuration
- Network Segmentation
- Network Troubleshooting
- Virtualization
- VMware Workstation

## Final Working Environment
  <img src="screenshots/01-opnsense-dashboard.png" width="800">

## Network Diagram
_To be completed._

## VMware Network Design

The lab was built using two VMware virtual networks. VMnet8 provided WAN connectivity through VMware NAT, while VMnet1 was configured as the isolated LAN network protected by OPNsense.

  <img src="screenshots/02-vmware-network-design.png" width="500">

## Interface Configuration

After deployment, WAN and LAN interfaces were assigned and configured within OPNsense. The LAN network was configured on a separate subnet to allow routing and firewall policy enforcement between networks.

  <img src="screenshots/03-opnsense-interface-assignment-success.png" width="600">
  <img src="screenshots/04-opnsense-lan-configuration.png" width="800">

## Firewall Validation

Firewall rules were created and tested to validate traffic control between networks. Connectivity tests confirmed that traffic was permitted or denied according to the configured policy.

  <img src="screenshots/05-opnsense-firewall-rule-google-dns-block.png" width="800">
  <img src="screenshots/06-ubuntu-firewall-rule-validation.png" width="500">
  
## Next Steps

- Configure additional firewall rules
- Explore VLAN segmentation
- Implement logging and monitoring
- Expand the lab environment with additional virtual hosts
