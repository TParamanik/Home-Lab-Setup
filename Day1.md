**Day 1 – VM Installation & Networking Progress**

Installation Steps 

🔹 Kali Linux

Installed using Debian 11.x (64-bit) version in VMware.

Assigned 30 GB disk (split into multiple files).

Default desktop environment selected (gdm3).

🔹 Windows 10

Installed via VMware with 2 GB RAM.

Disabled extra taskbar items (like News) later for a clean environment.

🔹 Ubuntu

Installed using Interactive Installation.

Selected Install third-party software (graphics, Wi-Fi, media formats).

Hostname customized after installation:

sudo hostnamectl set-hostname ubuntu-lab
hostname

🌐 2. Network Configuration
🔹 VMware Network Mode

Set all VMs to NAT → allows:

Internet access.

Inter-VM communication.

🔹 Kali Linux Networking

At first, only eth0 had internet.

Added DHCP to eth1:

sudo dhclient eth1


Confirmed IPs using:

ip a

🔹 Ubuntu Networking

Interfaces showed as ens33 and ens37.

Checked IPs with:

ip a


Applied netplan after adjusting permissions:

sudo chmod 600 /etc/netplan/*.yaml
sudo netplan apply

🔒 3. Firewall Rules (Windows 10)

Instead of disabling firewall, allowed ICMP (Ping) with:

netsh advfirewall firewall add rule name="ICMPv4-In" protocol=icmpv4:8,any dir=in action=allow

📡 4. Connectivity Test (Ping)

From Windows → Ping Kali’s eth1 IP:

ping 192.168.xxx.xxx


From Ubuntu → Ping Windows:

ping 192.168.xxx.xxx


From Kali → Ping Ubuntu:

ping 192.168.xxx.xxx


✅ All machines successfully communicated with each other.