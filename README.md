# CKAN-Chef

This branch, fi-ware, is configured to deploy a production instance to fi-ware's OpenStack environment.

A Vagrantfile is included for testing with chef-solo as provisioner.

CKAN 2.3:
Creates an Ubuntu 12.04 VM running Postgres 9.4, Solr, Jetty, CKAN (2.3) and Datastore.

CKAN 2.5:
Creates an Ubuntu 14.04 VM running Postgres 9.4, Solr, Jetty, CKAN (2.5) and Datastore.

## Installation

### For Testing with Vagrant

Install VirtualBox, Vagrant, Berkshelf and vagrant plugins:

1. Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. Install [Vagrant](https://www.vagrantup.com/)
3. Install Berkshelf by installing the [ChefDK](https://downloads.chef.io/chef-dk/)
4. Install vagrant-berkshelf plugin with: `$ vagrant plugin install vagrant-berkshelf`
5. Install vagrant-hostmanager plugin with: `$ vagrant plugin install vagrant-hostmanager`

Clone this repository, then:

`$ vagrant up`

The production instance can be viewed with the host machine's browser at `http://default.ckanhosted.dev/`, by default.

### For Production

Add `recipe[ckan::2.5_install]` to your run_list to install the dependencies needed for a production instance of CKAN that uses Apache/Nginx.

## Vagrant commands

Some useful Vagrant commands:

`$ vagrant up` Create and configure the guest machine.

`$ vagrant ssh` Login to the guest machine.

`$ vagrant suspend` Suspend the current state of the guest machine.

`$ vagrant halt` Attempt a shutdown of the guest machine.

`$ vagrant provision` Re-provision the guest machine according to the Chef cookbook.

`$ vagrant reload` Restart the guest machine. Add the `--provision` flag to also re-provision.

`$ vagrant destroy` Stops the guest machine and removes all of its resources. This will destroy the CKAN database and any uncommitted changes to the source code in the guest machine.

See [Vagrant documentation](http://docs.vagrantup.com/v2/cli/index.html) for a full list of commands.

## Attributes

CKAN configuration properties and installation locations can be tweaked in the attributes file: `/ckan/attributes/default.rb`.

Based on Victor Baptista's [chef-ckan](https://github.com/vitorbaptista/chef-ckan).
