# Day 4 - 

Source VM - Ubuntu

Target VM - Kali

-> Create a wordlist.txt with possible passwords in source VM

-> Installed hydra tool and used the below command to check if I can attack the target machine. Attack was successful.

```bash
hydra -l username_of_target -P password_file ssh://target_ip>
```

->In target machine we can check if successfully got access of the device using the command:

```bash
sudo journalctl -u ssh --since "1 hour ago" | grep -E "Failed password|Accepted password|Connection closed"
```

-> Using Fail2ban to ban attacker IP
- Installed fail2ban in target VM to check for login attempts. 
```bash
apt install -y fail2ban
```

- Create Jail Local Configuration 
```bash
nano /etc/fail2ban/jail.local
```

- Add the following content
```bash
[sshd]
enabled = true
port    = ssh
logpath = %(sshd_log)s
maxretry = 3
bantime = 1m
findtime = 10m
```

- enable and restart fail2ban
```bash
systemctl restart fail2ban
systemctl enable fail2ban
```

- check the status before and after running hydra in source vm
```bash
fail2ban-client status sshd
```