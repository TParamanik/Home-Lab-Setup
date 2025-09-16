# Day 4 - 

Source VM - Ubuntu

Target VM - Kali

-> Installed hydra tool and used the below command to check if I can attack the target machine. Attack was successful.

```bash
hydra -l username_of_target -P password_file ssh://target_ip>
```

->In target machine we can check if successfully got access of the device using the command:

```bash
sudo journalctl -u ssh --since "1 hour ago" | grep -E "Failed password|Accepted password|Connection closed"
```

-> Using Fail2ban to ban attacker IP
    - Installed fail2ban in Kali to check for login attempts. 
    ```bash
    apt install -y fail2ban
    ```
    
    - Create Jail Local COnfiguration 
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
    bantime = 10m
    findtime = 10m
    ```

