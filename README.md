# Automated Linux Server provisioning using Ansible

This repository contains a playbook for provisioning modern hosting environments with primary focus on web and database hosting on a fresh install of Ubuntu 16.04 LTS. The following is handled out of the box:

* Database user setup
* Distribution Upgrade
* SSH hardening
* Firewall setup

It will also install the following software:

* Nginx with HTTP/2 and [improved default configs](https://github.com/A5hleyRich/wordpress-nginx)
* PHP 7
* Postgresql-9.6
* Redis
* build-essential
* Fail2Ban
* Git
* python3-dev
* python3
* memcached
* libmemcached-dev

It will also install the following python packages using pip: psycopg2, south, django and pylibmc

## Usage

Configure your [hosts file](https://github.com/Neroe4eDev/wordpress-ansible/blob/master/hosts).

```
[servers]
192.168.1.1 #sampledomain.com
```

Edit [vars.yml](https://github.com/A5hleyRich/wordpress-ansible/blob/master/provision.yml) to configure your default user, [hashed](http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module) sudo password and local public key path. This will create a new user on the provisioned servers that you can use to gain SSH access.

Run:

`ansible-playbook -i hosts setup/pkgs.yml`
