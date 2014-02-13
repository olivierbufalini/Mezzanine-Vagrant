# Mezzanine Vagrant

Do a production-style deployment of mezzanine inside an Ubuntu virtual machine (VM).

The deployment uses Fabric scripts that come with Mezzanine. It configures PostgreSQL as the backend database,
Gunicorn as the WSGI server, Nginx as the front-web server with memcached, and Supervisor to control gunicorn.

## 1. Install the prequisites

 * [Vagrant](http://vagrantup.com) for managing VirtualBox-based virtual machines.
 * [Fabric](http://docs.fabfile.org) for automating the installation of Mezzanine.
 * Future.

 You can install fabric & future using pip.


## 2. Download this repository

If you haven't downloaded this repository yet, grab it from github:

    git clone https://github.com/olivierbufalini/Mezzanine-Vagrant
    
##  3. Put your SSH keys into the .ssh folder


##  4. Boot the virtual machine and install Mezzanine

Use Vagrant to boot the virtual machine and Fabric to install Mezzanine.

    cd Mezzanine-Vagrant
    vagrant up
    fab all


## 5. Access Mezzanine

Point your browser to <http://192.168.3.4>.

Log in to the admin interface <http://192.168.3.4/admin/> using the default account (username: `admin`, password: `default`).

You can also ssh to 192.168.3.3 to access the virtual machine (username: `vagrant`, password: `vagrant`).


## 6. Tear down your virtual machine

When you're all done, bring down your virtual machine.

    vagrant destroy
