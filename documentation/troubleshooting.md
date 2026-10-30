# Troubleshooting Notes

Record the actual symptom, cause, commands used, and outcome for each issue encountered. Do not mark an issue as resolved until the result has been verified.

## Issue log

| Date | Symptom | Cause | Resolution | Status |
| --- | --- | --- | --- | --- |
| — | No issues recorded yet | — | Add notes when an issue occurs | — |

## Useful host checks

Check VirtualBox version:

```bash
VBoxManage --version
```

List registered VMs:

```bash
VBoxManage list vms
```

List NAT Networks:

```bash
VBoxManage list natnetworks
```

Check loaded VirtualBox kernel modules:

```bash
lsmod | grep -E 'vboxdrv|vboxnet'
```

## Kali network checks

Run inside the Kali guest:

```bash
ip -br address
ip route
nmcli connection show
```

If NetworkManager reports a duplicate-address-detection delay on a connection named `Wired connection 1`, the course material suggests:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

Use the actual connection name shown by `nmcli connection show` if it differs. Re-check the guest address and route afterward.

## Evidence to attach

For each resolved issue, add a short explanation and, where useful, a screenshot or sanitized command output. Never include passwords, private keys, recovery codes, or access tokens.
