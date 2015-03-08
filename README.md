##What is this?##

This is a demo system for my "Advanced MCollective" presentation at Puppetconf 2015.

It's a small n-node cluster of machines for demoing the features of MCollective, along with some custom agents.  In particular I am demoing a *mysql mcollective agent*, which I hope will be the most useful to people out there in the wild, but the same premise applies to whatever technology you wish to orchestrate with MCollective.

I'm also demoing *how to fix the heartbleed vulnerability on this cluster with a one-line command*

It is also for *demonstrating some basic ruby TDD and rspec unit testing* around the mysql agent.

##How do I use it?##

Just clone this repo and then run `vagrant up`!

You can set the `VAGRANT_INSTANCES` environment variable to indicate the number of nodes you wish to join this demo collective.  It defaults to 3.  If you want more webservers, then you can increase this up to a maximum value of 9. You can also tweak the `VAGRANT_DOMAIN` (defaults to kahuna.com), `VAGRANT_MEMORY` (defaults to 350), and `VAGRANT_SUBNET` (defaults to 192.168.2.X) environment variables.

###Server roles###

Server roles are used, and the appropriate MCollective agents for that role are automatically deployed. e.g. nodes 1 and 2 on the subnet are mysql and memcached nodes, and nodes 3-9 are all webservers.  Node 10 is reserved for the MCollective client and middleware:

| Node        | Role           |
| ------------- |-------------|
| VAGRANT_SUBNET.0      | reverseproxy |
| VAGRANT_SUBNET.1      | mysql     |
| VAGRANT_SUBNET.2      | memcached |
| VAGRANT_SUBNET.3      | webserver |
| VAGRANT_SUBNET.4      | webserver |
| VAGRANT_SUBNET.5      | webserver |
| VAGRANT_SUBNET.6      | webserver |
| VAGRANT_SUBNET.7      | webserver |
| VAGRANT_SUBNET.8      | webserver |
| VAGRANT_SUBNET.9      | webserver |
| VAGRANT_SUBNET.10      | mcollective |

###Vagrant Provider###

I am running this using the [VMWare Fusion](https://www.vmware.com/products/fusion/fusion-evaluation) Vagrant [provider](http://www.vagrantup.com/vmware).  I recommend these for stability and speed and have in fact recently run into some serious issues using the freeware Virtualbox.

Although this Vagrantfile does support the virtualbox provider, you'll have to set the `VAGRANT_PROVIDER` environment variable to `virtualbox` to use it.  By default it's set to `vmware_fusion`.

