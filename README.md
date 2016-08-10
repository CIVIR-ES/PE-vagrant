# puppetmaster-vagrant

Simple puppet enterprise vagrant provision.

To download installer uncomment the indicated line in the Vagrantfile

The prepared node1 has its cert autosigned.

First "vagrant up master1", then "vagrant up node1"

Check the public network ip just in case it is already in use (192.168.0.164/master1, 192.168.0.165/node1)

PE console: https://192.168.0.164:443
User:admin
Pass:nimda
