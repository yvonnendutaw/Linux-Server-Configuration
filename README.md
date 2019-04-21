# Linux-Server-Configuration

IP address - http://178.62.15.240:8000/

## Get your server
I installed the Digital Ocean Droplet using these [instructions](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04)

## Secure your server
Update all currently installed packages
```bash
sudo apt-get update && sudo apt-get upgrade
```
Configured the firewalls to accept various ssh ports including 22, and 2200 using the digital oceans interface.

## Give grader access.
Create a new user account named grader.
```bash
sudo adduser grader
```
Give grader the permission to sudo.
```bash
sudo nano /etc/sudoers.d/grader
```
Add the following below root ALL=(ALL:ALL) ALL
```bash
grader ALL=(ALL:ALL) ALL
```
Create an SSH key pair for grader using the 
```bash
ssh-keygen
```
## Deploy Project
Install prerequisites for running a wsgi project
1.Apache
```bash
sudo apt-get install apache2
```
2. mod_wsgi
```bash
sudo apt-get install libapache2-mod-wsgi-py3
```
3. postresql
```bash
sudo apt-get install postresql
```
4. Install git and clone project in /var/www/ 
```bash
sudo apt-get install git
```
5. Install flask and the other application's dependencies using pip
6. Rename views.py to __init__.py and change the host to the server's IP address
7. Create catalog.wsgi in /var/www/catalog
```bash
import sys
import logging
logging.basicConfig(stream=sys.stderr)
sys.path.insert(0, "/var/www/catalog/")

from catalog import app as application
application.secret_key = 'supersecretkey'
```



