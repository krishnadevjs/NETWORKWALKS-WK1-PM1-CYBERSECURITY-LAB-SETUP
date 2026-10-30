# Lab Architecture

## Overview

This document describes the virtual lab created for the NetworkWalks Cybersecurity Internship, Week 1 Project Module 1 (WK1-PM1).

The environment consists of an Ubuntu host, Oracle VirtualBox, and a Kali Linux 2026.3 virtual machine connected through a dedicated NAT Network.

## Network topology

```text
                  Ubuntu host
                       |
                Oracle VirtualBox
                       |
          NAT Network: NetworkWalks
                 10.0.0.0/24
                       |
               Gateway: 10.0.0.1
                       |
              Kali Linux guest
                eth0: 10.0.0.2/24
```

## Host environment

| Component | Configuration |
| --- | --- |
| Operating system | Ubuntu 26.04.1 LTS |
| VirtualBox | 7.2.6 |
| Processor | AMD Ryzen 5 4600H |
| Memory | 14 GiB |

## Guest environment

- Operating system: Kali Linux 2026.3
- Deployment method: Prebuilt VirtualBox appliance
- Virtual CPUs: 2
- Virtual disk: Approximately 80 GB
- Network adapter: NAT Network — `NetworkWalks`

## Network parameters

- Subnet: `10.0.0.0/24`
- Gateway: `10.0.0.1`
- DHCP: Disabled
- Kali address: `10.0.0.2/24`
- DNS resolvers: `8.8.8.8` and `1.1.1.1`

## Validation

The Kali guest was assigned the configured static IPv4 address. Tests confirmed gateway reachability, external IP connectivity, and DNS resolution. See [Network Configuration](network-configuration.md) for commands and observed results.

Guest Additions, shared-folder access, and the final VM snapshot remain outstanding and will be documented after verification.
