# Linux-Server-Configuration-UDACITY

This is the seven project for "Full Stack Web Developer Nanodegree" on Udacity.

In this project, a Linux virtual machine needs to be configurated to support the Item Catalog website.

You can visit http://127.0.0.1 for the website deployed.

# the SSh Key the SSH key you created for the grader user :-
01111451253
# the password for grader login :-
M+e=2018 

# Tasks :-


  1-  Launch your Virtual Machine with your Udacity account
  2-  Follow the instructions provided to SSH into your server
  3-  Create a new user named grader
  4-  Give the grader the permission to sudo
  5-  Update all currently installed packages
  6-  Change the SSH port from 22 to 2200
  7-  Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200),
      HTTP (port 80), and NTP (port 123)
  8-  Configure the local timezone to UTC
  9-  Install and configure Apache to serve a Python mod_wsgi application
  10-  Install and configure PostgreSQL:
  *   Do not allow remote connections
  *     Create a new user named catalog that has limited permissions to your catalog application database
  11-  Install git, clone and setup your Catalog App project (from your GitHub repository from earlier in the Nanodegree program) so that it functions correctly when visiting your server’s IP address in a browser. Remember to set this up appropriately so that your .git directory is not publicly accessible via a browser!


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

    ssh -i [privateKeyFilename] grader@52.24.125.52

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
