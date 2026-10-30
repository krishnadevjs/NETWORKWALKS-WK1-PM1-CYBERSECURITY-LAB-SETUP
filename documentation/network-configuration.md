# Network Configuration

## VirtualBox NAT Network

| Setting | Value |
| --- | --- |
| Name | `NetworkWalks` |
| IPv4 network | `10.0.0.0/24` |
| Gateway | `10.0.0.1` |
| DHCP | Disabled |

The network was created on the Ubuntu host with:

```bash
VBoxManage natnetwork add --netname NetworkWalks --network "10.0.0.0/24" --enable --dhcp off
VBoxManage natnetwork start --netname NetworkWalks
```

Inspect configured NAT Networks:

```bash
VBoxManage list natnetworks
```

## Kali guest addressing

| Setting | Planned value |
| --- | --- |
| IPv4 address | `10.0.0.2/24` |
| Prefix | `/24` |
| Default gateway | `10.0.0.1` |
| DNS resolvers | `8.8.8.8`, `1.1.1.1` |

DHCP is disabled on this NAT Network. Kali was configured with a static IPv4 address using NetworkManager:

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

## Guest-side verification

The following checks were run inside Kali:

```bash
ip -br address
ip route
ping -c 4 10.0.0.1
ping -c 4 1.1.1.1
getent hosts kali.org
```

## Recorded verification results

| Check | Observed result |
| --- | --- |
| `eth0` address | `10.0.0.2/24` |
| Default route | `default via 10.0.0.1 dev eth0` |
| Gateway ping | 4 transmitted, 4 received, 0% packet loss |
| External IP ping (`1.1.1.1`) | 4 transmitted, 4 received, 0% packet loss |
| DNS lookup (`kali.org`) | Successful; IPv6 addresses returned |

The captured terminal output confirms the guest received the intended static address and route, the gateway and external IP were reachable, and DNS resolution worked.
