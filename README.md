Install the following software on your local machine. The commands given are intended for apt software manager
- Install Virtualbox
````bash
   sudo apt-get install virtualbox
````
- Install Vagrant
Download and install the latest version of Vagrant from https://www.vagrantup.com/downloads.html
The version tested is 1.6.5
````bash
   vagrant --version
````

- Install the latest version of Ansible (currently the latest version is 1.7.2)
````bash
   sudo apt-get install software-properties-common
   sudo apt-add-repository ppa:ansible/ansible
   sudo apt-get update
   sudo apt-get install ansible
````

Once you have installed the software, you need to update your ssh configuration settings.
By default, the ssh command is sending the locale of the host computer with every ssh connection.
This may cause LC_* issues with the installation of postgresql.

Please disable SendEnv in the settings of your ssh client (/etc/ssh/ssh_config):
````bash
   # SendEnv LANG LC_*
````

After this, go to the root of the repository and issue:

````bash
    vagrant up
````

The virtual machine will need a few minutes to build, upgrade and install the software and database.