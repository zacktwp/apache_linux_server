# Configure an apache linux server

### Start up an AWS lightsail instance

### Configure instance ufw firewall

Block all incoming traffic

`sudo ufw default deny incoming`

Allow outgoing traffic on all ports

`sudo ufw default allow outgoing`

Allow ssh traffic on port 22

`sudo ufw allow 22`

Allow http traffic on port 80

`sudo ufw allow www`

Allow incoming NTP on port 123

`sudo ufw allow ntp`

Allow ssh incoming traffic on port 2200

`sudo ufw allow 2200/tcp`

Check firewall rules

`sudo ufw show added`

Enable firewall

`sudo ufw enable`

 
