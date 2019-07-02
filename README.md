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


`su - grader`
`sudo mkdir .ssh`
`sudo chmod 700 .ssh`
`sudo nano .ssh/authorized_keys`
`sudo chmod 644 .ssh/authorized_keys`
`sudo service ssh restart`

### Configure the local timezone to UTC

`sudo timedatectl set-timezone UTC`

###  Install and configure Apache to serve a Python mod_wsgi application

`sudo apt-get install apache2`

`sudo apt-get install libapache2-mod-wsgi`

### Install and configure PostgreSQL

`sudo apt-get install postgresql postgresql-contrib`

`sudo -u postgres createuser -P catalog`

`sudo -u postgres createdb -O catalog catalog`

### Install packages for your application

`sudo apt-get install python-sqlalchemy python-pip`
`sudo apt-get install python-psycopg2 python-flask`
`sudo pip install oauth2client`
`sudo pip install requests`

### Install git

`sudo apt-get install git`

# Deploy the Item Catalog project

### Clone and setup your Item Catalog

`cd /var/www/`
`sudo mkdir fullstack-nanodegree-vm`
`sudo chown www-data:www-data fullstack-nanodegree-vm/`
`sudo -u www-data git clone https://github.com/zacktwp/Item_Catalog.git fullstack-nanodegree-vm`

### Configure postgresql

Replace the engine in the database_setup.py, PopulateDB.py, and Application.py with :

`engine = create_engine('postgresql://catalog:DB-PASSWORD@localhost/catalog')`

### buy and register domain name zacktwp.com and change google sign in json file
