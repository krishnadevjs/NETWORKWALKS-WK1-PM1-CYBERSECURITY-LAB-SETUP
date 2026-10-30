# NetworkWalks Cybersecurity Lab Setup

A hands-on cybersecurity lab built with **Oracle VirtualBox** and **Kali Linux** for the NetworkWalks Cybersecurity Internship — Week 1 Project (WK1-PM1).

This repository documents preparation of the virtual lab, network configuration, Kali Linux installation, connectivity validation, and troubleshooting.

> **Project status:** In progress. The Kali Linux 2026.3 prebuilt VirtualBox appliance has been imported and booted. The static IPv4 configuration, gateway connectivity, internet connectivity, and DNS resolution have been verified.

## Lab objectives

- Prepare a host system for virtualization.
- Create a VirtualBox NAT Network using the `10.0.0.0/24` subnet.
- Install Kali Linux in a virtual machine.
- Configure a static IP address for the Kali guest.
- Enable clipboard integration, drag and drop, and a shared downloads folder.
- Verify gateway access, internet connectivity, and DNS resolution.
- Capture evidence and document setup issues and their resolutions.

## Host environment

| Component | Configuration |
| --- | --- |
| Host operating system | Ubuntu 26.04.1 LTS |
| Virtualization platform | Oracle VirtualBox 7.2.6 |
| Archive utility | 7-Zip 26.00 |
| Host hardware | Lenovo Legion 5 (15ARH05) |
| Processor | AMD Ryzen 5 4600H |
| Memory | 14 GiB RAM |

## Planned virtual machine configuration

| Setting | Planned value |
| --- | --- |
| VM name | `NetworkWalks-Kali` |
| Guest operating system | Kali Linux (64-bit) |
| Memory | 4096 MB |
| Virtual CPUs | 2 |
| Virtual disk | 80.09 GB (imported appliance) |
| Network attachment | NAT Network |

These are the intended VM settings; the VM configuration and installation will be confirmed after setup.

## Network design

| Item | Value |
| --- | --- |
| VirtualBox network mode | NAT Network |
| Network name | `NetworkWalks` |
| Subnet | `10.0.0.0/24` |
| Gateway | `10.0.0.1` |
| DHCP | Disabled |
| Kali address | `10.0.0.2/24` |
| Default gateway | `10.0.0.1` |
| Configured DNS resolvers | `8.8.8.8`, `1.1.1.1` |

**Verified:** The `NetworkWalks` NAT Network was created with DHCP disabled. Inside Kali, `eth0` has `10.0.0.2/24`, the default route is via `10.0.0.1`, gateway and external-IP pings both passed with 0% packet loss, and `kali.org` resolved successfully.

## Repository structure

```text
.
├── README.md
├── documentation/
│   ├── lab-architecture.md
│   ├── network-configuration.md
│   └── troubleshooting.md
└── screenshots/
    └── .gitkeep
```

## Setup record

| Area | Current status |
| --- | --- |
| Host preparation and virtualization checks | Completed |
| VirtualBox and 7-Zip availability | Verified |
| NAT Network creation | Completed |
| Kali VM import and boot | Completed |
| Kali Linux 2026.3 guest available and booted | Completed (prebuilt appliance) |
| Static IP configuration in Kali | Verified |
| Guest Additions and integration features | Pending |
| Shared folder configuration | Pending |
| Gateway, internet, and DNS tests | Passed |
| Final VM snapshot | Pending |

Statuses will be updated as each step is completed and evidence is collected.

## Evidence

Add genuine screenshots to `screenshots/` as the lab is built. Suggested evidence:

- VirtualBox NAT Network configuration
- Kali VM hardware and network settings
- Kali desktop after installation
- Guest IP address and default route
- Successful gateway, internet, and DNS tests
- Shared folder mounted in Kali
- Final VirtualBox snapshot

Do not add passwords, recovery keys, personal tokens, or other secrets to screenshots or repository files.

## Documentation

- [Lab architecture](documentation/lab-architecture.md)
- [Network configuration](documentation/network-configuration.md)
- [Troubleshooting notes](documentation/troubleshooting.md)

## Safety and scope

Use this lab only for learning and authorized security testing. Test only systems you own or systems for which you have explicit written permission and a clearly defined scope. Do not scan or attack third-party systems without authorization.

## Program

**NetworkWalks Cybersecurity Internship — Week 1 Project (WK1-PM1)**

This repository is a work log and technical record. It will be updated with verified configuration details, test results, screenshots, and troubleshooting notes as the lab setup progresses.
