#**Day 1 – VM Installation & Networking Progress**

1. Installation Summary

-> Installed Kali Linux, Windows 10, and Ubuntu in VMware.

-> All set to NAT mode for internet + inter-VM communication(Host-only).

-> Error Resolving:

2. Network Auto-Configuration

*Kali Linux*

-> Configured eth0 and eth1 for automatic IP assignment.

-> Edited /etc/network/interfaces:

```bash 
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```
-> Restarted networking:

```bash
sudo systemctl restart networking
```

*Ubuntu*

-> Configured ens33 and ens37 for auto DHCP via netplan.

-> Edited /etc/netplan/01-netcfg.yaml

```bash
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: true
    ens37:
      dhcp4: true

```
-> Applied netplan after adjusting permissions:

```bash
sudo chmod 600 /etc/netplan/*.yaml
sudo netplan apply
```

*Windows 10(Firewall)*

->Allowed inbound ICMP (Ping) instead of disabling firewall:

```bash
netsh advfirewall firewall add rule name="ICMPv4-In" protocol=icmpv4:8,any dir=in action=allow
```

3. Connectivity Test

Ping from Windows → Kali ✅

Ping from Ubuntu → Windows ✅

Ping from Kali → Ubuntu ✅

⚡ End of Day Summary:

- Installed and configured 3 VMs.

- Added auto DHCP network configs in Kali + Ubuntu.

- Configured Windows firewall properly for ping.

- Verified full connectivity with ping tests.