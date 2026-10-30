# Lab Architecture

## Purpose
This document describes the intended VirtualBox lab for the NetworkWalks Week 1 Project (WK1-PM1).

## Topology
```text
                  Host computer
                 Ubuntu 26.04.1
                       |
                 Oracle VirtualBox
                       |
              NAT Network: NetworkWalks
                  10.0.0.0/24
                       |
              Gateway: 10.0.0.1
                       |
             Kali Linux virtual machine
                Planned IP: 10.0.0.2
```

The NAT Network provides the virtual machine with network connectivity through the host while allowing VMs attached to the same NAT Network to communicate with one another.

## Host configuration
- Operating system: Ubuntu 26.04.1 LTS
- VirtualBox: 7.2.6
- Processor: AMD Ryzen 5 4600H
- Memory: 14 GiB

## Planned guest configuration
- VM name: `NetworkWalks-Kali`
- Guest OS: Kali Linux 64-bit
- RAM: 4096 MB
- CPU: 2 virtual CPUs
- Disk: 60 GB dynamically allocated
- Network adapter: NAT Network named `NetworkWalks`

## Current implementation state
The VirtualBox NAT Network named `NetworkWalks` has been created for `10.0.0.0/24`, with DHCP disabled and gateway `10.0.0.1`. The Kali virtual machine and guest network configuration remain to be completed and verified.
