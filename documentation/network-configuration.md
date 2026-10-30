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

## Planned Kali guest addressing

| Setting | Planned value |
| --- | --- |
| IPv4 address | `10.0.0.2` |
| Prefix | `/24` |
| Default gateway | `10.0.0.1` |
| DNS resolver | `8.8.8.8` |

DHCP is disabled on this NAT Network, so the guest will need a static IPv4 configuration.

## Guest-side verification

After configuring the guest, run these commands inside Kali and record the actual output:

```bash
ip -br address
ip route
ping -c 4 10.0.0.1
ping -c 4 1.1.1.1
getent hosts kali.org
```

Expected checks:
1. The guest interface has the intended `10.0.0.2/24` address.
2. The routing table has a default route through `10.0.0.1`.
3. The gateway responds.
4. An external IP responds.
5. DNS resolution returns an address for `kali.org`.

These are verification steps, not claimed results. Add observed results and date after testing.
