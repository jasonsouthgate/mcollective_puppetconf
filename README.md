# mcollective_puppetconf

Demo system for my "Advanced MCollective" presentation at Puppetconf 2015

This is a small n-node cluster of machines for demoing the features of MCollective, along with some custom agents.  In particular I am demoing a mysql agent, which I hope will be the most useful to people out there in the wild, but the same premise applies to whatever technology you wish to orchestrate with MCollective.

You can set the VAGRANT_INSTANCES environment variable to indicate the number of nodes you wish to join this demo collective.  It defaults to 3.  You can also tweak the VAGRANT_DOMAIN (defaults to kahuna.com), VAGRANT_MEMORY (defaults to 350), and VAGRANT_SUBNET (defaults to 192.168.2.X).

Server roles are used, and the appropriate MCollective agents for that role are automatically deployed. e.g. nodes 1 and 2 on the subnet are mysql and memcached nodes, and nodes 3-9 are all webservers.  Node 10 is reserved for the MCollective middleware and client.

