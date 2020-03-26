#Install Jitsi Meet on Ubuntu 18.04 LTS

## Prerequisites
* A fresh Ubuntu 18.04 LTS x64 server instance with an IPv4 address
   You can use a cloud provider, e.g.
   https://www.digitalocean.com/
   https://www.kamatera.com/
   https://www.linode.com/

* root access with ssh key to your server
* A domain`name  being pointed to your server 
   For DNS Services I recommend https://www.cloudflare.com/
* git and ansible installed on your workstation
   https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html
   https://www.linode.com/docs/development/version-control/how-to-install-git-on-linux-mac-and-windows/

## get the ansible playbooks
* create a temporary directory on your workstation and fetch the installation playbook

```commandline
mkdir tempdir
cd tempdir
git clone https://github.com/olsarnow/jitsi-meet.git
```

## configure the playbook settings
* change the entry in hosts.inv to the IP address of your server

``` cat hosts.inv
[jitsi]
134.122.31.99
```

* modify the entries in the group_vars/jitsi to the domain name, hostname of your server and fill in an(your) email address for the registration of the server certificate

``` cat group_vars/jitsi
---
ansible_setfqdn: meet.example.org
ansible_sethostname: meet
ansible_email: olaf@example.org
```

* that's all what you need to configure

## run the playbook and install your jitsi server

* execute ansible-playbook with the site-jitsi.yml 

``` commandline
ansible-playbook site-jitsi.yml
```

* wait some minutes and be prepared

## login and chat with your friends

* Finally, point your favorite web browser to https://yourdomainname to access your Jitsi Meet Video conferencing service.
* Clicking the GO button will immediately create a Video conferencing channel for you.
* Have fun!

