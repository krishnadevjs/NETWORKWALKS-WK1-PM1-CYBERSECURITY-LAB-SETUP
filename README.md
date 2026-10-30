# NetworkWalks Cybersecurity Lab

**Program:** NetworkWalks Cybersecurity Internship  
**Project:** Week 1 — Project Module 1 (WK1-PM1)  
**Platform:** Oracle VirtualBox and Kali Linux

This repository documents the setup and validation of a virtual cybersecurity lab hosted on Ubuntu. It includes the lab architecture, network configuration, verification results, and supporting evidence.

## Project overview

The lab uses a VirtualBox NAT Network to connect a Kali Linux virtual machine to the internet while maintaining a dedicated virtual subnet. The Kali guest is configured with a static IPv4 address.

## Host environment

| Component | Configuration |
| --- | --- |
| Operating system | Ubuntu 26.04.1 LTS |
| Virtualization platform | Oracle VirtualBox 7.2.6 |
| Processor | AMD Ryzen 5 4600H |
| Host memory | 14 GiB |
| Archive utility | 7-Zip 26.00 |

## Virtual machine

| Setting | Configuration |
| --- | --- |
| Guest operating system | Kali Linux 2026.3 |
| CPU allocation | 2 virtual CPUs |
| Virtual disk | Approximately 80 GB |
| Network attachment | NAT Network — `NetworkWalks` |

The VM was imported from the prebuilt Kali VirtualBox appliance.

## Network configuration

| Parameter | Value |
| --- | --- |
| VirtualBox network | `NetworkWalks` |
| Network mode | NAT Network |
| IPv4 subnet | `10.0.0.0/24` |
| Gateway | `10.0.0.1` |
| DHCP | Disabled |
| Kali interface | `eth0` |
| Kali static address | `10.0.0.2/24` |
| DNS resolvers | `8.8.8.8`, `1.1.1.1` |

### Connectivity validation

The following results were observed inside Kali:

| Test | Result |
| --- | --- |
| IPv4 address on `eth0` | `10.0.0.2/24` |
| Default route | Via `10.0.0.1` |
| Gateway ping | 4/4 replies; 0% packet loss |
| External IP ping (`1.1.1.1`) | 4/4 replies; 0% packet loss |
| DNS lookup for `kali.org` | Successful |

## Implementation status

| Component | Status |
| --- | --- |
| Ubuntu host preparation | Complete |
| VirtualBox installation and virtualization checks | Complete |
| NAT Network creation | Complete |
| Kali appliance import and boot | Complete |
| Static IPv4 configuration | Complete |
| Gateway and internet connectivity | Verified |
| DNS resolution | Verified |
| Guest Additions and desktop integration | In progress |
| Shared downloads folder | Pending |
| Final VM snapshot | Pending |
| Supporting screenshots | To be added |

The status table reflects work completed and verified to date. Pending items will be updated after testing.

## Repository structure

```text
.
├── README.md
├── documentation/
│   ├── lab-architecture.md
│   ├── network-configuration.md
│   └── troubleshooting.md
└── screenshots/
```

## Evidence

Screenshots will be added to the `screenshots/` directory as each configuration item is completed. Evidence should show the relevant VirtualBox settings or Kali terminal output.

Before committing screenshots, check that they do not expose passwords, recovery keys, personal tokens, or unrelated personal information.

## Documentation

- [Lab architecture](documentation/lab-architecture.md)
- [Network configuration](documentation/network-configuration.md)
- [Troubleshooting](documentation/troubleshooting.md)

## Safety

This environment is intended for education and authorized security testing. Test only systems you own or systems for which you have explicit permission and a defined scope.
