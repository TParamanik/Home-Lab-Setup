# **Day 3: Apache Web Server and Firewall Setup in Ubuntu**

1. Installed Apache2 in ubuntu and enabled auto-start 

2. Configured firewall and set some rules. 
    
    -> first we need to check the status:
    ```bash
    ufw status
    ```

    -> then we can set the rules of what connections to allow and what not to:
    ```bash
    ufw allow OpenSSH           #to allow remote access
    ufw allow "Apache Full"     #to allow http and https
    ```

    -> At last enable the connection and check the status
    ```bash
    ufw enable 
    ufw stable
    ```

3. Host a test page in http://localhost. By default there are some content but if we want to change it we need to go to /var/www/html/ and change the content of index.html 