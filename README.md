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

### Update all currently installed packages

`sudo apt-get update`

`sudo apt-get upgrade`

### Create a new user account named grader

`sudo adduser grader`

### Give grader the permission to sudo

sudo touch /etc/sudoers.d/grader

sudo nano /etc/sudoers.d/grader

past the below into the file:

`grader ALL=(ALL) NOPASSWD:ALL`

### Create an SSH key pair for grader using the ssh-keygen tool

in your local terminal type:

`ssh-keygen`

copy the .pub files contents and past in the lightsail instince in the below file

`sudo nano ~/.ssh/authorized_keys`


`su - grader
sudo mkdir .ssh
sudo chmod 700 .ssh
sudo nano .ssh/authorized_keys
sudo chmod 644 .ssh/authorized_keys
sudo service ssh restart`
