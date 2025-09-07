Tasks Completed

Installed Kali Linux, Parrot OS, and Windows 10 in VirtualBox.

Configured network adapters (NAT + Host-Only).

Fixed network issues (DNS resolution, IPv6).

Verified internet connectivity on all VMs.

Successfully tested ping communication:

Kali ↔ Parrot

Kali ↔ Windows

Parrot ↔ Windows

Notes

Initial DNS errors in Kali were resolved by disabling IPv6 and setting DNS manually.

Windows Firewall blocked ICMP (ping); allowed inbound ICMP via firewall rule.

All three systems can now communicate with each other.