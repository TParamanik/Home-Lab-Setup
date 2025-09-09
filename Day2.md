# **Day 2 - Remote Access with SSH**

## Steps to follow

- Check if both Kali and Ubuntu can ping each other. 

- Install and enable ssh service on both the VMs

    -> Check if ssh is installed or not:
    ```bash
    ssh -v
    ```

    ->If installed check the status using systemctl, if not running enable it:
    ```bash
    systemctl enable ssh
    systemctl start ssh
    systemctl status ssh
    ```

    ->Now from the source VM connect to the target VM using the command:
    ```bash
    ssh username@target_ip
    ```
    - When you open your target VM's terminal, there will be a prompt like 
    kali@kali-virtual:~ kali is the username we will be using 