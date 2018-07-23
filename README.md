# Linux-Server-Configuration-UDACITY

This is the seven project for "Full Stack Web Developer Nanodegree" on Udacity.

In this project, a Linux virtual machine needs to be configurated to support the Item Catalog website.

You can visit http://104.196.198.90 for the website deployed.

#  the SSH key you created for the grader user :-
01111451253

# the url 
http://90.198.196.104.bc.googleusercontent.com
 
# ssh port
2200
# software installed
* apache2
* postgresql
* python

# Create a new user named grader

    sudo adduser grader
    vim /etc/sudoers
    touch /etc/sudoers.d/grader
    vim /etc/sudoers.d/grader, type in grader ALL=(ALL:ALL) ALL, save and quit

# Set ssh login using keys

    generate keys on local machine usingssh-keygen ; then save the private key in ~/.ssh on local machine

    deploy public key on developement enviroment

    On you virtual machine:

    $ su - grader
    $ mkdir .ssh
    $ touch .ssh/authorized_keys
    $ vim .ssh/authorized_keys

    Copy the public key generated on your local machine to this file and save

    $ chmod 700 .ssh
    $ chmod 644 .ssh/authorized_keys

    reload SSH using service ssh restart

    now you can use ssh to login with the new user you created

    ssh grader@104.196.198.90 -p 2200 -i [pass to key file]

# Update all currently installed packages

sudo apt-get update

sudo apt-get upgrade

# Change the SSH port from 22 to 2200

    Use sudo vim /etc/ssh/sshd_config and then change Port 22 to Port 2200 , save & quit.
    Reload SSH using sudo service ssh restart

# Configure the Uncomplicated Firewall (UFW)

Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123)

sudo ufw allow 2200/tcp

sudo ufw allow 80/tcp

sudo ufw allow 123/udp

sudo ufw enable 

# in this repository the key file is exist that called "linux_file_key.pub"
