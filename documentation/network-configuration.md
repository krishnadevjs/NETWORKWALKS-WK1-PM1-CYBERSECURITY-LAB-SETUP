# Network Configuration

## VirtualBox NAT Network

The lab uses a VirtualBox NAT Network named `NetworkWalks`.

| Setting | Value |
| --- | --- |
| Network name | `NetworkWalks` |
| IPv4 network | `10.0.0.0/24` |
| Gateway | `10.0.0.1` |
| DHCP | Disabled |

The network was created and started on the Ubuntu host with:

```bash
VBoxManage natnetwork add --netname NetworkWalks --network "10.0.0.0/24" --enable --dhcp off
VBoxManage natnetwork start --netname NetworkWalks
```

To inspect the configured NAT Networks:

```bash
VBoxManage list natnetworks
```

## Kali guest IPv4 configuration

| Setting | Value |
| --- | --- |
| Interface | `eth0` |
| IPv4 address | `10.0.0.2/24` |
| Default gateway | `10.0.0.1` |
| DNS resolvers | `8.8.8.8`, `1.1.1.1` |
| IPv6 | Disabled for this connection |

The static configuration was applied through NetworkManager:

```bash
sudo nmcli connection modify "Wired connection 1" \
  ipv4.method manual \
  ipv4.addresses 10.0.0.2/24 \
  ipv4.gateway 10.0.0.1 \
  ipv4.dns "8.8.8.8 1.1.1.1" \
  ipv6.method disabled

sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

## Verification commands

The following commands were run inside Kali:

```bash
ip -br address
ip route
ping -c 4 10.0.0.1
ping -c 4 1.1.1.1
getent hosts kali.org
```

## Observed results

| Check | Result |
| --- | --- |
| Interface address | `eth0` has `10.0.0.2/24` |
| Default route | `default via 10.0.0.1 dev eth0` |
| Gateway connectivity | 4 packets received; 0% packet loss |
| External IP connectivity | 4 packets received from `1.1.1.1`; 0% packet loss |
| DNS resolution | `kali.org` resolved successfully |

These results confirm that the guest's static IPv4 configuration, default route, outbound connectivity, and DNS resolution were working when tested.
